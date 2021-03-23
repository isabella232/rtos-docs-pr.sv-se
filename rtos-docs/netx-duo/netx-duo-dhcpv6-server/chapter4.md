---
title: Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-server tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6Server-tjänster
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826028"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a><span data-ttu-id="752e9-103">Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-server tjänster</span><span class="sxs-lookup"><span data-stu-id="752e9-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 server services</span></span>

<span data-ttu-id="752e9-104">Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6Server-tjänster (visas nedan).</span><span class="sxs-lookup"><span data-stu-id="752e9-104">This chapter contains a description of all NetX Duo DHCPv6Server services (listed below).</span></span>

<span data-ttu-id="752e9-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="752e9-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="752e9-106">nx_dhcpv6_server_create *skapa en DHCPv6-serverinstance*</span><span class="sxs-lookup"><span data-stu-id="752e9-106">nx_dhcpv6_server_create *Create a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="752e9-107">nx_dhcpv6_server_delete *ta bort ett DHCPv6-serverinstance*</span><span class="sxs-lookup"><span data-stu-id="752e9-107">nx_dhcpv6_server_delete *Delete a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="752e9-108">nx_dhcpv6_server_start *starta aktiviteten DHCPv6-server*</span><span class="sxs-lookup"><span data-stu-id="752e9-108">nx_dhcpv6_server_start *Start the DHCPv6 server task*</span></span>
- <span data-ttu-id="752e9-109">nx_dhcpv6_server_suspend *pausa aktiviteten DHCPv6-server*</span><span class="sxs-lookup"><span data-stu-id="752e9-109">nx_dhcpv6_server_suspend *Suspend the DHCPv6 server task*</span></span>
- <span data-ttu-id="752e9-110">nx_dhcpv6_server_resume *återuppta DHCPV6-klient bearbetning*</span><span class="sxs-lookup"><span data-stu-id="752e9-110">nx_dhcpv6_server_resume *Resume DHCPv6 client processing*</span></span>
- <span data-ttu-id="752e9-111">nx_dhcpv6_server_suspend *pausa DHCPV6-klient bearbetning*</span><span class="sxs-lookup"><span data-stu-id="752e9-111">nx_dhcpv6_server_suspend *Suspend DHCPv6 client processing*</span></span>
- <span data-ttu-id="752e9-112">nx_dhcpv6_create_dns_address *ställa in DNS-servern för Options-begäranden*</span><span class="sxs-lookup"><span data-stu-id="752e9-112">nx_dhcpv6_create_dns_address *Set the DNS server for option requests*</span></span>
- <span data-ttu-id="752e9-113">nx_dhcpv6_create_ip_address_range *skapa intervallet av IP-adresser som ska lånas*</span><span class="sxs-lookup"><span data-stu-id="752e9-113">nx_dhcpv6_create_ip_address_range *Create the range of IP addresses to lease*</span></span>
- <span data-ttu-id="752e9-114">nx_dhcpv6_reserve_ip_address_range *reserv intervall med IP-adresser i Server listan*</span><span class="sxs-lookup"><span data-stu-id="752e9-114">nx_dhcpv6_reserve_ip_address_range *Reserve range of IP addresses in server list*</span></span>
- <span data-ttu-id="752e9-115">nx_dhcpv6_set_server_duid *ange serverns DUID för DHCPv6-paket*</span><span class="sxs-lookup"><span data-stu-id="752e9-115">nx_dhcpv6_set_server_duid *Set the Server DUID for DHCPv6 packets*</span></span>
- <span data-ttu-id="752e9-116">nx_dhcpv6_add_ip_address_lease *lägga till en låne post i DHCPv6-server tabellen*</span><span class="sxs-lookup"><span data-stu-id="752e9-116">nx_dhcpv6_add_ip_address_lease *Add a lease record to the DHCPv6 server table*</span></span>
- <span data-ttu-id="752e9-117">Nx_dhcpv6_retrieve_ip_address_lease *Hämta en IP-adresslån från Server tabellen*</span><span class="sxs-lookup"><span data-stu-id="752e9-117">Nx_dhcpv6_retrieve_ip_address_lease *Retrieve an IP lease record from the Server table*</span></span>
- <span data-ttu-id="752e9-118">nx_dhcpv6_add_client_record *lägga till en DHCPV6-klient post i Server tabellen*</span><span class="sxs-lookup"><span data-stu-id="752e9-118">nx_dhcpv6_add_client_record *Add a DHCPv6 Client record to the Server table*</span></span>
- <span data-ttu-id="752e9-119">nx_dhcpv6_retrieve_client_record *Hämta en klient post från Server tabellen*</span><span class="sxs-lookup"><span data-stu-id="752e9-119">nx_dhcpv6_retrieve_client_record *Retrieve a client record from the Server table*</span></span>
- <span data-ttu-id="752e9-120">nx_dhcpv6_server_interface_set *Ange gränssnitts index för serverns DHCPv6-tjänster*</span><span class="sxs-lookup"><span data-stu-id="752e9-120">nx_dhcpv6_server_interface_set *Set the interface index for Server DHCPv6 services*</span></span>
- <span data-ttu-id="752e9-121">nx_dhcpv6_server_option_request_handler_set *Ange hanteraren för Options-begäran*</span><span class="sxs-lookup"><span data-stu-id="752e9-121">nx_dhcpv6_server_option_request_handler_set *Set the option request handler*</span></span>

## <a name="nx_dhcpv6_create_dns_address"></a><span data-ttu-id="752e9-122">nx_dhcpv6_create_dns_address</span><span class="sxs-lookup"><span data-stu-id="752e9-122">nx_dhcpv6_create_dns_address</span></span>

### <a name="set-the-network-dns-server"></a><span data-ttu-id="752e9-123">Ange nätverks-DNS-Server</span><span class="sxs-lookup"><span data-stu-id="752e9-123">Set the network DNS server</span></span>

<span data-ttu-id="752e9-124">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-124">**Prototype**</span></span>

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

<span data-ttu-id="752e9-125">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-125">**Description**</span></span>

<span data-ttu-id="752e9-126">Den här tjänsten läser in DHCPv6-servern med DNS-serveradressen för serverns DHCPv6-nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="752e9-126">This service loads the DHCPv6 Server with the DNS server address for the Server DHCPv6 network interface.</span></span>

<span data-ttu-id="752e9-127">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-127">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-128">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-128">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-129">**dns_ipv6_address** Pekare till DNS-servern</span><span class="sxs-lookup"><span data-stu-id="752e9-129">**dns_ipv6_address** Pointer to the DNS server</span></span>

<span data-ttu-id="752e9-130">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-130">**Return Values**</span></span>

- <span data-ttu-id="752e9-131">**NX_SUCCESS** (0X00) DNS-Serversaved till DHCPv6-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="752e9-131">**NX_SUCCESS** (0x00) DNS Serversaved to DHCPv6 Server instance</span></span>
- <span data-ttu-id="752e9-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) en ogiltig adress har angetts</span><span class="sxs-lookup"><span data-stu-id="752e9-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="752e9-133">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-133">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-134">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-134">**Allowed From**</span></span>

<span data-ttu-id="752e9-135">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-135">Application Code</span></span>

<span data-ttu-id="752e9-136">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-136">**Example**</span></span>

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a><span data-ttu-id="752e9-137">nx_dhcpv6_create_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="752e9-137">nx_dhcpv6_create_ip_address_range</span></span>

### <a name="create-the-server-ip-address-list"></a><span data-ttu-id="752e9-138">Skapa serverns IP-adress lista</span><span class="sxs-lookup"><span data-stu-id="752e9-138">Create the Server IP address list</span></span>

<span data-ttu-id="752e9-139">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-139">**Prototype**</span></span>

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

<span data-ttu-id="752e9-140">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-140">**Description**</span></span>

<span data-ttu-id="752e9-141">Den här tjänsten skapar IP-adress listan som anges av start-och slut adresserna för serverns tilldelnings bara adress intervall.</span><span class="sxs-lookup"><span data-stu-id="752e9-141">This service creates the IP address list specified by the start and end addresses of the Server’s assignable address range.</span></span> <span data-ttu-id="752e9-142">Start-och slut adresserna måste överensstämma med adressprefixet för Server gränssnittet (måste finnas på samma länk som serverns DHCPv6-gränssnitt).</span><span class="sxs-lookup"><span data-stu-id="752e9-142">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 interface).</span></span> <span data-ttu-id="752e9-143">Antalet adresser som faktiskt har lagts till returneras.</span><span class="sxs-lookup"><span data-stu-id="752e9-143">The number of addresses actually added is returned.</span></span>

<span data-ttu-id="752e9-144">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-144">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-145">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-145">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-146">**start_ipv6_address** Början av adresser som ska läggas till</span><span class="sxs-lookup"><span data-stu-id="752e9-146">**start_ipv6_address** Start of addresses to add</span></span>
- <span data-ttu-id="752e9-147">**end_ipv6_address** Slut på adresser som ska läggas till</span><span class="sxs-lookup"><span data-stu-id="752e9-147">**end_ipv6_address** End of addresses to add</span></span>
- <span data-ttu-id="752e9-148">\***addresses_added** Utdata från adresser har lagts till</span><span class="sxs-lookup"><span data-stu-id="752e9-148">\***addresses_added** Output of addresses added</span></span>

<span data-ttu-id="752e9-149">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-149">**Return Values**</span></span>

- <span data-ttu-id="752e9-150">**NX_SUCCESS** (0X00) IP-adress lista har skapats</span><span class="sxs-lookup"><span data-stu-id="752e9-150">**NX_SUCCESS** (0x00) IP address list successfully created</span></span>
- <span data-ttu-id="752e9-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) en ogiltig adress har angetts</span><span class="sxs-lookup"><span data-stu-id="752e9-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="752e9-152">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-152">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-153">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-153">**Allowed From**</span></span>

<span data-ttu-id="752e9-154">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-154">Application Code</span></span>

<span data-ttu-id="752e9-155">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-155">**Example**</span></span>

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a><span data-ttu-id="752e9-156">nx_dhcpv6_reserve_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="752e9-156">nx_dhcpv6_reserve_ip_address_range</span></span>

### <a name="reserve-specified-range-of-ip-addresses"></a><span data-ttu-id="752e9-157">Reservera angivet intervall av IP-adresser</span><span class="sxs-lookup"><span data-stu-id="752e9-157">Reserve specified range of IP addresses</span></span>

<span data-ttu-id="752e9-158">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-158">**Prototype**</span></span>

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

<span data-ttu-id="752e9-159">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-159">**Description**</span></span>

<span data-ttu-id="752e9-160">Den här tjänsten reserverar det IP-adressintervall som anges av start-och slut adresserna.</span><span class="sxs-lookup"><span data-stu-id="752e9-160">This service reserves the IP address range specified by the start and end addresses.</span></span> <span data-ttu-id="752e9-161">Dessa adresser måste ligga inom det tidigare skapade Server-IP-adressintervallet.</span><span class="sxs-lookup"><span data-stu-id="752e9-161">These addresses must be within in the previously created server IP address range.</span></span> <span data-ttu-id="752e9-162">Dessa adresser kommer inte att tilldelas till några klienter av DHCPv6-servern.</span><span class="sxs-lookup"><span data-stu-id="752e9-162">These addresses will not be assigned to any Clients by the DHCPv6 Server.</span></span> <span data-ttu-id="752e9-163">Start-och slut adresserna måste överensstämma med adressprefixet för Server gränssnittet (måste finnas på samma länk som serverns DHCPv6-nätverks gränssnitt).</span><span class="sxs-lookup"><span data-stu-id="752e9-163">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 network interface).</span></span> <span data-ttu-id="752e9-164">Antalet adresser som faktiskt reserver ATS returneras.</span><span class="sxs-lookup"><span data-stu-id="752e9-164">The number of addresses actually reserved is returned.</span></span>

<span data-ttu-id="752e9-165">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-165">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-166">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-166">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-167">**start_ipv6_address** Början av adresser som ska reserveras</span><span class="sxs-lookup"><span data-stu-id="752e9-167">**start_ipv6_address** Start of addresses to reserve</span></span>
- <span data-ttu-id="752e9-168">**end_ipv6_address** Slut på adresser som ska reserveras</span><span class="sxs-lookup"><span data-stu-id="752e9-168">**end_ipv6_address** End of addresses to reserve</span></span>
- <span data-ttu-id="752e9-169">\***addresses_reserved** Antal reserverade adresser</span><span class="sxs-lookup"><span data-stu-id="752e9-169">\***addresses_reserved** Number of addresses reserved</span></span>

<span data-ttu-id="752e9-170">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-170">**Return Values**</span></span>

- <span data-ttu-id="752e9-171">**NX_SUCCESS** (0X00) versions meddelandet har skapats och bearbetats</span><span class="sxs-lookup"><span data-stu-id="752e9-171">**NX_SUCCESS** (0x00) RELEASE message successfully created and processed</span></span>
- <span data-ttu-id="752e9-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) en ogiltig adress har angetts</span><span class="sxs-lookup"><span data-stu-id="752e9-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="752e9-173">Det gick inte att hitta **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) med start adress i server adress listan.</span><span class="sxs-lookup"><span data-stu-id="752e9-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Starting address not found in Server address list.</span></span>
- <span data-ttu-id="752e9-174">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-174">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-175">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-175">**Allowed From**</span></span>

<span data-ttu-id="752e9-176">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-176">Application Code</span></span>

<span data-ttu-id="752e9-177">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-177">**Example**</span></span>

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a><span data-ttu-id="752e9-178">nx_dhcpv6_server_create</span><span class="sxs-lookup"><span data-stu-id="752e9-178">nx_dhcpv6_server_create</span></span>

### <a name="create-the-dhcpv6-server-instance"></a><span data-ttu-id="752e9-179">Skapa DHCPv6-Server instansen</span><span class="sxs-lookup"><span data-stu-id="752e9-179">Create the DHCPv6 Server instance</span></span> 

<span data-ttu-id="752e9-180">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-180">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

<span data-ttu-id="752e9-181">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-181">**Description**</span></span>

<span data-ttu-id="752e9-182">Den här tjänsten skapar DHCPv6-servern med angivna inuppgifter.</span><span class="sxs-lookup"><span data-stu-id="752e9-182">This service creates the DHCPv6 Server task with the specified input.</span></span> <span data-ttu-id="752e9-183">Återanrops hanterarna är valfria ingångar.</span><span class="sxs-lookup"><span data-stu-id="752e9-183">The callback handlers are optional input.</span></span> <span data-ttu-id="752e9-184">Stack pekaren, indatamängden för IP-instansen och Packet-poolen krävs.</span><span class="sxs-lookup"><span data-stu-id="752e9-184">The stack pointer, IP instance and packet pool input are required.</span></span> <span data-ttu-id="752e9-185">IP-instansen och Packet-poolen måste redan ha skapats.</span><span class="sxs-lookup"><span data-stu-id="752e9-185">The IP instance and packet pool must already be created.</span></span>

<span data-ttu-id="752e9-186">Användaren uppmanas att anropa nx_dhcpv6_server_option_request_handler_set för att ställa in option Request handler.</span><span class="sxs-lookup"><span data-stu-id="752e9-186">User is encouraged to call nx_dhcpv6_server_option_request_handler_set to set the option request handler.</span></span>

<span data-ttu-id="752e9-187">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-187">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-188">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-188">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-189">**ip_ptr** Pekare till IP-instansen</span><span class="sxs-lookup"><span data-stu-id="752e9-189">**ip_ptr** Pointer to the IP instance</span></span>
- <span data-ttu-id="752e9-190">**name_str** Pekare till Server namn</span><span class="sxs-lookup"><span data-stu-id="752e9-190">**name_str** Pointer to Server name</span></span>
- <span data-ttu-id="752e9-191">**packet_pool_ptr** Pekare till Server paketets pool</span><span class="sxs-lookup"><span data-stu-id="752e9-191">**packet_pool_ptr** Pointer to Server packet pool</span></span>
- <span data-ttu-id="752e9-192">**stack_ptr** Pekare till serverns stack minne</span><span class="sxs-lookup"><span data-stu-id="752e9-192">**stack_ptr** Pointer to Server stack memory</span></span>
- <span data-ttu-id="752e9-193">**stack_size** Storlek på serverns stack-minne</span><span class="sxs-lookup"><span data-stu-id="752e9-193">**stack_size** Size of Server stack memory</span></span>
- <span data-ttu-id="752e9-194">**dhcpv6_address_declined_handler** Pekare till klienten nekar eller frigör meddelande hanterare</span><span class="sxs-lookup"><span data-stu-id="752e9-194">**dhcpv6_address_declined_handler** Pointer to Client Decline or Release message handler</span></span>
- <span data-ttu-id="752e9-195">**dhcpv6_option_request_handler** Pekare till alternativ hanteraren för begär ande alternativ</span><span class="sxs-lookup"><span data-stu-id="752e9-195">**dhcpv6_option_request_handler** Pointer to options request option handler</span></span>

<span data-ttu-id="752e9-196">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-196">**Return Values**</span></span>

- <span data-ttu-id="752e9-197">**NX_SUCCESS** (0X00) servern har återupptagits</span><span class="sxs-lookup"><span data-stu-id="752e9-197">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="752e9-198">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-198">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="752e9-199">NX_DHCPV6_PARAM_ERROR ogiltiga inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-199">NX_DHCPV6_PARAM_ERROR Invalid non pointer input</span></span>

<span data-ttu-id="752e9-200">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-200">**Allowed From**</span></span>

<span data-ttu-id="752e9-201">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-201">Application Code</span></span>

<span data-ttu-id="752e9-202">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-202">**Example**</span></span>

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a><span data-ttu-id="752e9-203">nx_dhcpv6_server_delete</span><span class="sxs-lookup"><span data-stu-id="752e9-203">nx_dhcpv6_server_delete</span></span>

### <a name="delete-the-dhcpv6-server"></a><span data-ttu-id="752e9-204">Ta bort DHCPv6-servern</span><span class="sxs-lookup"><span data-stu-id="752e9-204">Delete the DHCPv6 Server</span></span>

<span data-ttu-id="752e9-205">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-205">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="752e9-206">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-206">**Description**</span></span>

<span data-ttu-id="752e9-207">Den här tjänsten tar bort aktiviteten DHCPv6-server och alla begär Anden som servern har bearbetat.</span><span class="sxs-lookup"><span data-stu-id="752e9-207">This service deletes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="752e9-208">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-208">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-209">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-209">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="752e9-210">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-210">**Return Values**</span></span>

- <span data-ttu-id="752e9-211">**NX_SUCCESS** (0x00)-servern har tagits bort</span><span class="sxs-lookup"><span data-stu-id="752e9-211">**NX_SUCCESS** (0x00) Server successfully deleted</span></span>
- <span data-ttu-id="752e9-212">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-212">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-213">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-213">**Allowed From**</span></span>

<span data-ttu-id="752e9-214">Konversation</span><span class="sxs-lookup"><span data-stu-id="752e9-214">Threads</span></span>

<span data-ttu-id="752e9-215">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-215">**Example**</span></span>

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a><span data-ttu-id="752e9-216">nx_dhcpv6_server_resume</span><span class="sxs-lookup"><span data-stu-id="752e9-216">nx_dhcpv6_server_resume</span></span>

### <a name="resume-dhcpv6-server-task"></a><span data-ttu-id="752e9-217">Återuppta DHCPv6-server uppgift</span><span class="sxs-lookup"><span data-stu-id="752e9-217">Resume DHCPv6 Server task</span></span> 

<span data-ttu-id="752e9-218">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-218">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="752e9-219">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-219">**Description**</span></span>

<span data-ttu-id="752e9-220">Den här tjänsten återupptar DHCPv6-server uppgiften och alla begär Anden som servern har bearbetat.</span><span class="sxs-lookup"><span data-stu-id="752e9-220">This service resumes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="752e9-221">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-221">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-222">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-222">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="752e9-223">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-223">**Return Values**</span></span>

- <span data-ttu-id="752e9-224">**NX_SUCCESS** (0X00) servern har återupptagits</span><span class="sxs-lookup"><span data-stu-id="752e9-224">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="752e9-225">**NX_DHCPV6_ALREADY_STARTED** -servern (0xE91) körs redan</span><span class="sxs-lookup"><span data-stu-id="752e9-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="752e9-226">**status** (variabel) ThreadX och netx Duo-fel status</span><span class="sxs-lookup"><span data-stu-id="752e9-226">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="752e9-227">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-227">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-228">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-228">**Allowed From**</span></span>

<span data-ttu-id="752e9-229">Konversation</span><span class="sxs-lookup"><span data-stu-id="752e9-229">Threads</span></span>

<span data-ttu-id="752e9-230">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-230">**Example**</span></span>

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a><span data-ttu-id="752e9-231">nx_dhcpv6_server_suspend</span><span class="sxs-lookup"><span data-stu-id="752e9-231">nx_dhcpv6_server_suspend</span></span>

### <a name="suspend-dhcpv6-server-task"></a><span data-ttu-id="752e9-232">Pausa DHCPv6-server aktivitet</span><span class="sxs-lookup"><span data-stu-id="752e9-232">Suspend DHCPv6 Server task</span></span> 

<span data-ttu-id="752e9-233">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-233">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="752e9-234">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-234">**Description**</span></span>

<span data-ttu-id="752e9-235">Den här tjänsten gör att DHCPv6-server aktiviteten stoppas och alla begär Anden om att servern har bearbetats.</span><span class="sxs-lookup"><span data-stu-id="752e9-235">This service suspends the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="752e9-236">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-236">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-237">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-237">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="752e9-238">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-238">**Return Values**</span></span>

- <span data-ttu-id="752e9-239">**NX_SUCCESS** (0X00) servern har återupptagits</span><span class="sxs-lookup"><span data-stu-id="752e9-239">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="752e9-240">**NX_DHCPV6_NOT_STARTED** -servern (0xE92) har inte startats</span><span class="sxs-lookup"><span data-stu-id="752e9-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started</span></span> 
- <span data-ttu-id="752e9-241">**Status** (variabel) ThreadX och netx Duo-fel status</span><span class="sxs-lookup"><span data-stu-id="752e9-241">**Status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="752e9-242">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-242">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-243">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-243">**Allowed From**</span></span>

<span data-ttu-id="752e9-244">Konversation</span><span class="sxs-lookup"><span data-stu-id="752e9-244">Threads</span></span>

<span data-ttu-id="752e9-245">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-245">**Example**</span></span>

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a><span data-ttu-id="752e9-246">nx_dhcpv6_server_start</span><span class="sxs-lookup"><span data-stu-id="752e9-246">nx_dhcpv6_server_start</span></span>

### <a name="start-the-dhcpv6-server-task"></a><span data-ttu-id="752e9-247">Starta aktiviteten DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-247">Start the DHCPv6 Server task</span></span> 

<span data-ttu-id="752e9-248">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-248">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="752e9-249">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-249">**Description**</span></span>

<span data-ttu-id="752e9-250">Den här tjänsten startar DHCPv6-server aktiviteten och läser servern för att bearbeta program begär Anden för att ta emot DHCPv6-klient meddelanden.</span><span class="sxs-lookup"><span data-stu-id="752e9-250">This service starts the DHCPv6 Server task and readies the Server to process application requests for receiving DHCPv6 Client messages.</span></span> <span data-ttu-id="752e9-251">Den verifierar att Server instansen har tillräckligt med information (Server-DUID), skapar och binder UDP-socketen för att skicka och ta emot DHCPv6-meddelanden och aktiverar timers för att hålla reda på sessionens tid och förfallo datum för IP-lån.</span><span class="sxs-lookup"><span data-stu-id="752e9-251">It verifies the Server instance has sufficient information (Server DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages, and activates timers for keeping track of session time and IP lease expiration.</span></span>

>[!NOTE] 
> <span data-ttu-id="752e9-252">Innan DHCPv6-servern kan köras ansvarar värd programmet för att skapa det IP-adressintervall som servern kan tilldela IP-adresser från.</span><span class="sxs-lookup"><span data-stu-id="752e9-252">Before the DHCPv6 Server can run, the host application is responsible for creating the IP address range from which the Server can assign IP addresses.</span></span> <span data-ttu-id="752e9-253">Det är också ansvarigt för att ställa in serverns DUID och DHCPv6-gränssnitt (se *nx_dhcpv6_server_duid_set* respektive *nx_dhcpv6_server_interface_set* .</span><span class="sxs-lookup"><span data-stu-id="752e9-253">It is also responsible for setting the Server DUID and DHCPv6 interface (see *nx_dhcpv6_server_duid_set* and *nx_dhcpv6_server_interface_set* respectively.</span></span>

<span data-ttu-id="752e9-254">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-254">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-255">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-255">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="752e9-256">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-256">**Return Values**</span></span>

- <span data-ttu-id="752e9-257">**NX_SUCCESS** (0X00) servern har startats</span><span class="sxs-lookup"><span data-stu-id="752e9-257">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="752e9-258">**NX_DHCPV6_ALREADY_STARTED** -servern (0xE91) körs redan</span><span class="sxs-lookup"><span data-stu-id="752e9-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="752e9-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** -servern (0xEA7) har inga adresser som kan tilldelas till lån</span><span class="sxs-lookup"><span data-stu-id="752e9-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server has no assignable addresses to lease</span></span>
- <span data-ttu-id="752e9-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) inget globalt adress index har angetts</span><span class="sxs-lookup"><span data-stu-id="752e9-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Global address index not set</span></span>
- <span data-ttu-id="752e9-261">**NX_DHCPV6_NO_SERVER_DUID** (0XE92) inget Server-DUID har skapats</span><span class="sxs-lookup"><span data-stu-id="752e9-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No Server DUID created</span></span> 
- <span data-ttu-id="752e9-262">**status** (variabel) ThreadX och netx Duo-fel status</span><span class="sxs-lookup"><span data-stu-id="752e9-262">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="752e9-263">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-263">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-264">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-264">**Allowed From**</span></span>

<span data-ttu-id="752e9-265">Konversation</span><span class="sxs-lookup"><span data-stu-id="752e9-265">Threads</span></span>

<span data-ttu-id="752e9-266">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-266">**Example**</span></span>

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a><span data-ttu-id="752e9-267">nx_dhcpv6_retrieve_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="752e9-267">nx_dhcpv6_retrieve_ip_address_lease</span></span>

### <a name="get-an-ip-address-lease-from-the-server-table"></a><span data-ttu-id="752e9-268">Hämta ett IP-adresslån från Server tabellen</span><span class="sxs-lookup"><span data-stu-id="752e9-268">Get an IP address lease from the Server table</span></span>

<span data-ttu-id="752e9-269">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-269">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

<span data-ttu-id="752e9-270">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-270">**Description**</span></span>

<span data-ttu-id="752e9-271">Den här tjänsten hämtar en post för IP-adresslån från Server tabellen på den angivna tabell index platsen.</span><span class="sxs-lookup"><span data-stu-id="752e9-271">This service retrieves an IP address lease record from the Server table at the specified table index location.</span></span> <span data-ttu-id="752e9-272">Detta kan göras innan eller efter att klient post data har hämtats.</span><span class="sxs-lookup"><span data-stu-id="752e9-272">This can be done before or after retrieving Client record data.</span></span>

<span data-ttu-id="752e9-273">Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet.</span><span class="sxs-lookup"><span data-stu-id="752e9-273">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="752e9-274">Det innebär ingen skillnad i vilken ordning IP-adresslån data och klient post data sparas till icke-flyktigt minne.</span><span class="sxs-lookup"><span data-stu-id="752e9-274">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="752e9-275">Vi rekommenderar inte att du kopierar data till eller från Server tabeller utan att stoppa eller pausa DHCPv6-servern först.</span><span class="sxs-lookup"><span data-stu-id="752e9-275">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="752e9-276">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-276">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-277">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-277">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-278">**table_index** Tabell index för att lagra lån på</span><span class="sxs-lookup"><span data-stu-id="752e9-278">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="752e9-279">**lease_IP_address** Pekare till IP-adress som är lånad till klienten</span><span class="sxs-lookup"><span data-stu-id="752e9-279">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="752e9-280">**T1** Klient begärd förnyelse tid</span><span class="sxs-lookup"><span data-stu-id="752e9-280">**T1** Client requested renew time</span></span>
- <span data-ttu-id="752e9-281">**T2** Klienten begärde OMBINDNINGS tid</span><span class="sxs-lookup"><span data-stu-id="752e9-281">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="752e9-282">**valid_lifetime** Klient lånet blir föråldrat</span><span class="sxs-lookup"><span data-stu-id="752e9-282">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="752e9-283">**preferred_lifetime** Klient lånet blir ogiltigt</span><span class="sxs-lookup"><span data-stu-id="752e9-283">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="752e9-284">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-284">**Return Values**</span></span>

- <span data-ttu-id="752e9-285">**NX_SUCCESS** (0X00) servern har startats</span><span class="sxs-lookup"><span data-stu-id="752e9-285">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="752e9-286">**NX_DHCPV6_PARAMETER_ERROR** (0XE93) ogiltiga indata från IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="752e9-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="752e9-287">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-287">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-288">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-288">**Allowed From**</span></span>

<span data-ttu-id="752e9-289">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-289">Application code</span></span>

<span data-ttu-id="752e9-290">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-290">**Example**</span></span>

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a><span data-ttu-id="752e9-291">nx_dhcpv6_add_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="752e9-291">nx_dhcpv6_add_ip_address_lease</span></span>

### <a name="add-an-ip-address-lease-to-the-server-table"></a><span data-ttu-id="752e9-292">Lägg till ett IP-adresslån till Server tabellen</span><span class="sxs-lookup"><span data-stu-id="752e9-292">Add an IP address lease to the Server table</span></span>

<span data-ttu-id="752e9-293">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-293">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

<span data-ttu-id="752e9-294">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-294">**Description**</span></span>

<span data-ttu-id="752e9-295">Den här tjänsten läser in IP-adresslån från en tidigare DHCPv6-server-session från icke-flyktigt minne till Server leasing tabellen.</span><span class="sxs-lookup"><span data-stu-id="752e9-295">This service loads IP lease data from a previous DHCPv6 Server session from non volatile memory to the Server lease table.</span></span> <span data-ttu-id="752e9-296">Detta är inte nödvändigt om servern körs för första gången och inte har några tidigare låne data.</span><span class="sxs-lookup"><span data-stu-id="752e9-296">This is not necessary if the Server is running for the first time and has no previous lease data.</span></span> <span data-ttu-id="752e9-297">Om detta är fallet måste värd programmet skapa ett IP-adressintervall för att tilldela IP-adresser med hjälp av tjänsten *nx_dhcpv6_create_ip_address_range*.</span><span class="sxs-lookup"><span data-stu-id="752e9-297">If this is the case the host application must create an IP address range for assigning IP addresses, using the *nx_dhcpv6_create_ip_address_range* service.</span></span> <span data-ttu-id="752e9-298">Data räcker för att rekonstruera en DHCPv6-låne post.</span><span class="sxs-lookup"><span data-stu-id="752e9-298">The data is sufficient to reconstruct a DHCPv6 lease record.</span></span> <span data-ttu-id="752e9-299">Tabell indexet behöver inte anges.</span><span class="sxs-lookup"><span data-stu-id="752e9-299">The table index need not be specified.</span></span> <span data-ttu-id="752e9-300">Om värdet är 0xFFFFFFFF (oändlighet) kommer DHCPv6-servern att hitta nästa tillgängliga plats för att kopiera data till.</span><span class="sxs-lookup"><span data-stu-id="752e9-300">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will find the next available slot to copy the data to.</span></span>

>[!NOTE] 
> <span data-ttu-id="752e9-301">Överföring av IP-adresslån måste göras innan klient poster överförs. båda måste utföras före (åter) start av DHCPv6-servern.</span><span class="sxs-lookup"><span data-stu-id="752e9-301">Uploading IP lease data MUST be done before uploading Client records; both MUST be done before (re)starting the DHCPv6 Server.</span></span>

<span data-ttu-id="752e9-302">Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet.</span><span class="sxs-lookup"><span data-stu-id="752e9-302">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="752e9-303">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-303">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-304">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-304">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-305">**table_index** Tabell index för att lagra lån på</span><span class="sxs-lookup"><span data-stu-id="752e9-305">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="752e9-306">**lease_IP_address** Pekare till IP-adress som är lånad till klienten</span><span class="sxs-lookup"><span data-stu-id="752e9-306">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="752e9-307">**T1** Klient begärd förnyelse tid</span><span class="sxs-lookup"><span data-stu-id="752e9-307">**T1** Client requested renew time</span></span>
- <span data-ttu-id="752e9-308">**T2** Klienten begärde OMBINDNINGS tid</span><span class="sxs-lookup"><span data-stu-id="752e9-308">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="752e9-309">**valid_lifetime** Klient lånet blir föråldrat</span><span class="sxs-lookup"><span data-stu-id="752e9-309">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="752e9-310">**preferred_lifetime** Klient lånet blir ogiltigt</span><span class="sxs-lookup"><span data-stu-id="752e9-310">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="752e9-311">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-311">**Return Values**</span></span>

- <span data-ttu-id="752e9-312">**NX_SUCCESS** (0X00) servern har startats</span><span class="sxs-lookup"><span data-stu-id="752e9-312">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="752e9-313">**NX_DHCPV6_TABLE_FULL** (0XEC4) inget rum för fler låne data \* \*</span><span class="sxs-lookup"><span data-stu-id="752e9-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No room for more lease data\*\*</span></span>
- <span data-ttu-id="752e9-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) låne data visas inte på länk med serverns DHCPv6-gränssnitt</span><span class="sxs-lookup"><span data-stu-id="752e9-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lease data does not appear to be on link with Server DHCPv6 interface</span></span>
- <span data-ttu-id="752e9-315">**NX_DHCPV6_PARAM_ERROR** (0XE93) ogiltiga indata från IP-adresslån</span><span class="sxs-lookup"><span data-stu-id="752e9-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="752e9-316">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-316">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-317">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-317">**Allowed From**</span></span>

<span data-ttu-id="752e9-318">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-318">Application code</span></span>

<span data-ttu-id="752e9-319">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-319">**Example**</span></span>

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a><span data-ttu-id="752e9-320">nx_dhcpv6_add_client_record</span><span class="sxs-lookup"><span data-stu-id="752e9-320">nx_dhcpv6_add_client_record</span></span>

### <a name="add-a-client-record-to-the-server-table"></a><span data-ttu-id="752e9-321">Lägga till en klient post i Server tabellen</span><span class="sxs-lookup"><span data-stu-id="752e9-321">Add a Client record to the Server table</span></span>

<span data-ttu-id="752e9-322">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-322">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

<span data-ttu-id="752e9-323">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-323">**Description**</span></span>

<span data-ttu-id="752e9-324">Den här tjänsten kopierar klient data från icke-flyktigt minne till Server tabellen en post i taget.</span><span class="sxs-lookup"><span data-stu-id="752e9-324">This service copies Client data from non volatile memory to the Server table one record at a time.</span></span> <span data-ttu-id="752e9-325">Detta är bara nödvändigt om servern startas om och har klient data från en tidigare session som ska återställas från minnet.</span><span class="sxs-lookup"><span data-stu-id="752e9-325">This is only necessary if the Server is being rebooted and has Client data from a previous session to restore from memory.</span></span> <span data-ttu-id="752e9-326">Om en server saknar tidigare data initierar DHCPv6-servern klient tabellen för att kunna lägga till klient poster.</span><span class="sxs-lookup"><span data-stu-id="752e9-326">If a Server has no previous data, the DHCPv6 Server will initialize the Client table to be able for adding Client records.</span></span>

<span data-ttu-id="752e9-327">Du behöver inte ange tabell indexet.</span><span class="sxs-lookup"><span data-stu-id="752e9-327">It is not necessary to specify the table index.</span></span> <span data-ttu-id="752e9-328">Om värdet är 0xFFFFFFFF (oändlighet) kommer DHCPv6-servern att hitta nästa tillgängliga plats.</span><span class="sxs-lookup"><span data-stu-id="752e9-328">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will locate the next available slot.</span></span> <span data-ttu-id="752e9-329">DHCPv6-servern kan rekonstruera en klient post från dessa data.</span><span class="sxs-lookup"><span data-stu-id="752e9-329">The DHCPv6 Server can reconstruct a Client record from this data.</span></span>

>[!NOTE] 
> <span data-ttu-id="752e9-330">Värd programmet måste ladda upp IP-adresslån innan klienten registrerar data.</span><span class="sxs-lookup"><span data-stu-id="752e9-330">The host application MUST upload the IP lease data BEFORE the Client record data.</span></span> <span data-ttu-id="752e9-331">Detta är så att en intern DHCPv6-server kan korsa länkar tabellerna så att varje klient post är kopplad till motsvarande IP-adresslån i respektive tabell.</span><span class="sxs-lookup"><span data-stu-id="752e9-331">This is so that internally the DHCPv6 Server can cross link the tables so that each Client record is joined with its corresponding IP lease record in their respective tables.</span></span> <span data-ttu-id="752e9-332">Se *nx_dhcpv6_add_ip_address_lease* för information om hur du överför IP-adresslån från minnet.</span><span class="sxs-lookup"><span data-stu-id="752e9-332">See *nx_dhcpv6_add_ip_address_lease* for details on uploading IP lease data from memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="752e9-333">Inte alla data måste anges beroende på DUID-typ.</span><span class="sxs-lookup"><span data-stu-id="752e9-333">Depending on DUID type, not all data must be supplied.</span></span> <span data-ttu-id="752e9-334">Om till exempel en klient har tilldelats en leverantör som har tilldelats typen DUID, kan den skicka i noll för DUID-länk skikts parametrar (MAC-adress, maskin varu typ, DUID-tid).</span><span class="sxs-lookup"><span data-stu-id="752e9-334">For example if a Client has a vendor assigned DUID type, it can send in zero for DUID Link Layer parameters (MAC address, hardware type, DUID time).</span></span>

<span data-ttu-id="752e9-335">Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet.</span><span class="sxs-lookup"><span data-stu-id="752e9-335">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="752e9-336">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-336">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-337">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-337">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="752e9-338">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-338">**Return Values**</span></span>

- <span data-ttu-id="752e9-339">**NX_SUCCESS** (0X00) servern har startats</span><span class="sxs-lookup"><span data-stu-id="752e9-339">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="752e9-340">**NX_ INVALID_PARAMETERS** (0X4D) ogiltig information om icke-pekare \* \*</span><span class="sxs-lookup"><span data-stu-id="752e9-340">**NX_ INVALID_PARAMETERS** (0x4D) Invalid non pointer input\*\*</span></span>
- <span data-ttu-id="752e9-341">**NX_DHCPV6_TABLE_FULL** (0XEC4) inga tomma platser kvar för att lägga till en annan klient post</span><span class="sxs-lookup"><span data-stu-id="752e9-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No empty slots left for adding another Client record</span></span>
- <span data-ttu-id="752e9-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0XEA8) kunde inte hitta en klient som har tilldelats adressen i serverns leasing tabell.</span><span class="sxs-lookup"><span data-stu-id="752e9-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Client assigned address not found in Server lease table.</span></span>
- <span data-ttu-id="752e9-343">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-343">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-344">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-344">**Allowed From**</span></span>

<span data-ttu-id="752e9-345">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-345">Application code</span></span>

<span data-ttu-id="752e9-346">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-346">**Example**</span></span>

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a><span data-ttu-id="752e9-347">nx_dhcpv6_retrieve_client_record</span><span class="sxs-lookup"><span data-stu-id="752e9-347">nx_dhcpv6_retrieve_client_record</span></span>

### <a name="retrieve-a-client-record-from-the-server-table"></a><span data-ttu-id="752e9-348">Hämta en klient post från Server tabellen</span><span class="sxs-lookup"><span data-stu-id="752e9-348">Retrieve a Client record from the Server table</span></span>

<span data-ttu-id="752e9-349">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-349">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

<span data-ttu-id="752e9-350">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-350">**Description**</span></span>

<span data-ttu-id="752e9-351">Den här tjänsten kopierar viktiga data från serverns klient post tabell för lagring till beständigt minne.</span><span class="sxs-lookup"><span data-stu-id="752e9-351">This service copies the essential data from the Server’s Client record table for storage to non-volatile memory.</span></span> <span data-ttu-id="752e9-352">Servern kan konstruera om en lämplig klient post från sådana data i den omvända processen (Ladda upp data till Server tabellen).</span><span class="sxs-lookup"><span data-stu-id="752e9-352">The Server can reconstruct an adequate Client record from such data in the reverse process (uploading data to the Server table).</span></span> <span data-ttu-id="752e9-353">Oavsett DUID-typ kan ingen av punkterna vara NULL-pekare; data initieras till noll för alla parametrar.</span><span class="sxs-lookup"><span data-stu-id="752e9-353">Regardless of the DUID type, none of the pointers can be NULL pointers; data is initialized to zero for all parameters.</span></span> <span data-ttu-id="752e9-354">Om t. ex. klientens DUID-typ är länk skikt och tid returneras leverantörs numret som noll och det privata ID: t är en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="752e9-354">For example, if the Client DUID type is Link Layer Plus Time, the vendor number is returned as zero and the private ID is an empty string.</span></span>

<span data-ttu-id="752e9-355">Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet.</span><span class="sxs-lookup"><span data-stu-id="752e9-355">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="752e9-356">Det innebär ingen skillnad i vilken ordning IP-adresslån data och klient post data sparas till icke-flyktigt minne.</span><span class="sxs-lookup"><span data-stu-id="752e9-356">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="752e9-357">Vi rekommenderar inte att du kopierar data till eller från Server tabeller utan att stoppa eller pausa DHCPv6-servern först.</span><span class="sxs-lookup"><span data-stu-id="752e9-357">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="752e9-358">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-358">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-359">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-359">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-360">**table_index** Index i serverns klient tabell</span><span class="sxs-lookup"><span data-stu-id="752e9-360">**table_index** Index into Server’s client table</span></span>
- <span data-ttu-id="752e9-361">**message_xid** Transaktions-ID för klient server</span><span class="sxs-lookup"><span data-stu-id="752e9-361">**message_xid** Client Server Transaction ID</span></span>
- <span data-ttu-id="752e9-362">**client_address** IPv6-adress lånad till klient</span><span class="sxs-lookup"><span data-stu-id="752e9-362">**client_address** IPv6 address leased to Client</span></span>
- <span data-ttu-id="752e9-363">**client_state** Klientens DHCPv6-tillstånd (t. ex. Bound)</span><span class="sxs-lookup"><span data-stu-id="752e9-363">**client_state** Client DHCPv6 state (e.g. bound)</span></span>
- <span data-ttu-id="752e9-364">**IP_lease_time_accrued** Tiden upphörde att gälla för lån **dhcpv6_server_ptr** pekare till Dhcpv6-servern</span><span class="sxs-lookup"><span data-stu-id="752e9-364">**IP_lease_time_accrued** Time expired on lease already **dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-365">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-365">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="752e9-366">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-366">**Return Values**</span></span>

- <span data-ttu-id="752e9-367">**NX_SUCCESS** (0X00) servern har startats</span><span class="sxs-lookup"><span data-stu-id="752e9-367">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="752e9-368">**NX_DHCPV6_INVALID_DUID** (0XECC) ogiltiga eller inkonsekventa DUID-data</span><span class="sxs-lookup"><span data-stu-id="752e9-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Invalid or inconsistent DUID data</span></span>
- <span data-ttu-id="752e9-369">**NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-369">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="752e9-370">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-370">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

<span data-ttu-id="752e9-371">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-371">**Allowed From**</span></span>

<span data-ttu-id="752e9-372">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-372">Application code</span></span>

<span data-ttu-id="752e9-373">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-373">**Example**</span></span>

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a><span data-ttu-id="752e9-374">nx_dhcpv6_server_interface_set</span><span class="sxs-lookup"><span data-stu-id="752e9-374">nx_dhcpv6_server_interface_set</span></span>

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a><span data-ttu-id="752e9-375">Setthe Interface index för Server DHCPv6-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="752e9-375">Setthe interface index for Server DHCPv6 interface</span></span>

<span data-ttu-id="752e9-376">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-376">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

<span data-ttu-id="752e9-377">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-377">**Description**</span></span>

<span data-ttu-id="752e9-378">Den här tjänsten anger det nätverks gränssnitt där DHCPv6-servern hanterar DHCPv6-klient förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="752e9-378">This service sets the network interface on which the DHCPv6 Server handles DHCPv6 Client requests.</span></span> <span data-ttu-id="752e9-379">För versioner av NetX Duo som inte har stöd för multihome är gränssnittets värde standard värdet noll.</span><span class="sxs-lookup"><span data-stu-id="752e9-379">Not that for versions of NetX Duo that do not support multihome, the interface value is defaulted to zero.</span></span> <span data-ttu-id="752e9-380">Det globala adress indexet krävs för att hämta serverns globala adress i DHCPv6-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="752e9-380">The global address index is necessary to obtain the Server global address on its DHCPv6 interface.</span></span> <span data-ttu-id="752e9-381">Detta används av DHCPv6-logiken för att säkerställa att låne adresser och andra DHCPv6-data finns på länken till DHCPv6-servern.</span><span class="sxs-lookup"><span data-stu-id="752e9-381">This is used by the DHCPv6 logic to ensure that lease addresses and other DHCPv6 data is on link with the DHCPv6 Server.</span></span>

<span data-ttu-id="752e9-382">Detta måste anropas innan DHCPv6-servern startas, även för program på enskilda enheter eller utan support för flera hem.</span><span class="sxs-lookup"><span data-stu-id="752e9-382">This must be called before the DHCPv6 server is started, even for applications on single homed devices or without multihome support.</span></span>

<span data-ttu-id="752e9-383">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-383">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-384">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-384">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-385">**iface_index** Serverns DHCPv6-server gränssnitt</span><span class="sxs-lookup"><span data-stu-id="752e9-385">**iface_index** Server DHCPv6 Server interface</span></span>
- <span data-ttu-id="752e9-386">**ga_address_index** Index för serverns globala adress i adress tabellen för serverns IP-instans</span><span class="sxs-lookup"><span data-stu-id="752e9-386">**ga_address_index** Index of Server global address in the Server IP instance address table</span></span>

<span data-ttu-id="752e9-387">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-387">**Return Values**</span></span>

- <span data-ttu-id="752e9-388">**NX_SUCCESS** (0X00) servern har startats</span><span class="sxs-lookup"><span data-stu-id="752e9-388">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="752e9-389">**NX_INVALID_INTERFACE** -gränssnittet (0x4C) finns inte</span><span class="sxs-lookup"><span data-stu-id="752e9-389">**NX_INVALID_INTERFACE** (0x4C) Interface does not exist</span></span>
- <span data-ttu-id="752e9-390">NX_NO_INTERFACE_ADDRESS (0x50) globalt index överskrider IP-instansens högsta IPv6-adresser (NX_MAX_IPV6_ADDRESSES)</span><span class="sxs-lookup"><span data-stu-id="752e9-390">NX_NO_INTERFACE_ADDRESS (0x50) Global index exceeds the IP instance maximum IPv6 addresses (NX_MAX_IPV6_ADDRESSES)</span></span>
- <span data-ttu-id="752e9-391">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-391">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-392">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-392">**Allowed From**</span></span>

<span data-ttu-id="752e9-393">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-393">Application code</span></span>

<span data-ttu-id="752e9-394">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-394">**Example**</span></span>

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a><span data-ttu-id="752e9-395">nx_dhcpv6_set_server_duid</span><span class="sxs-lookup"><span data-stu-id="752e9-395">nx_dhcpv6_set_server_duid</span></span>

### <a name="set-the-server-duid-for-dhcpv6-packets"></a><span data-ttu-id="752e9-396">Ange serverns DUID för DHCPv6-paket</span><span class="sxs-lookup"><span data-stu-id="752e9-396">Set the Server DUID for DHCPv6 packets</span></span>

<span data-ttu-id="752e9-397">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-397">**Prototype**</span></span>

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

<span data-ttu-id="752e9-398">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-398">**Description**</span></span>

<span data-ttu-id="752e9-399">Den här tjänsten ställer in serverns DUID och måste anropas innan värd programmet startar servern.</span><span class="sxs-lookup"><span data-stu-id="752e9-399">This service sets the Server DUID and must be called before the host application starts the Server.</span></span> <span data-ttu-id="752e9-400">För länk skikts typer och länk lager tids typer av DUID måste värd programmet ange maskin varu typ och MAC-Datadata.</span><span class="sxs-lookup"><span data-stu-id="752e9-400">For link layer and link layer time DUID types, the host application must supply the hardware type and MAC address data.</span></span> <span data-ttu-id="752e9-401">För länk skiktets tids DUIDs måste tids pekaren peka på en giltig tid.</span><span class="sxs-lookup"><span data-stu-id="752e9-401">For link layer time DUIDs, the time pointer must point to a valid time.</span></span> <span data-ttu-id="752e9-402">Antalet sekunder sedan 1 januari 2000 är ett typiskt Seed-värde.</span><span class="sxs-lookup"><span data-stu-id="752e9-402">The number of seconds since Jan 1, 2000 is a typical seed value.</span></span> <span data-ttu-id="752e9-403">Om serverns DUID-typ är företag, tilldelad typ, skapas DUIDen från användar konfigurerbara alternativ NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID och NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, och värdena för tid och MAC-adress kan anges till NULL.</span><span class="sxs-lookup"><span data-stu-id="752e9-403">If the Server DUID type is the enterprise, vendor assigned type, the DUID will be created from the user configurable options NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID and NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, and the time and MAC address values can be set to NULL.</span></span>

>[!NOTE] 
> <span data-ttu-id="752e9-404">Det är värd programmets ansvar att spara DUID-parametrarna för servern på ett beständigt minne, så att den använder samma DUID i meddelanden till klienter mellan omstarter.</span><span class="sxs-lookup"><span data-stu-id="752e9-404">It is the host application’s responsibility to save the Server DUID parameters to nonvolatile memory such that it uses the same DUID in messages to Clients between reboots.</span></span> <span data-ttu-id="752e9-405">Detta är ett krav för DHCPv6-protokollet (RFC 3315).</span><span class="sxs-lookup"><span data-stu-id="752e9-405">This is a requirement of the DHCPv6 protocol (RFC 3315).</span></span>

<span data-ttu-id="752e9-406">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-406">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-407">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-407">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-408">**duid_type** DUID-typ för DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-408">**duid_type** DHCPv6 Server DUID type</span></span>
- <span data-ttu-id="752e9-409">**hardware_type** Maskin varu typ (t. ex. Ethernet)</span><span class="sxs-lookup"><span data-stu-id="752e9-409">**hardware_type** Hardware type (e.g. Ethernet)</span></span>
- <span data-ttu-id="752e9-410">**mac_address_msw** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-410">**mac_address_msw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-411">**mac_address_lsw** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-411">**mac_address_lsw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-412">**tid** Tids värde för DUID</span><span class="sxs-lookup"><span data-stu-id="752e9-412">**time** Time value for DUID</span></span>

<span data-ttu-id="752e9-413">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-413">**Return Values**</span></span>

- <span data-ttu-id="752e9-414">**NX_SUCCESS** (0X00) servern har pausats</span><span class="sxs-lookup"><span data-stu-id="752e9-414">**NX_SUCCESS** (0x00) Server successfully suspended</span></span>
- <span data-ttu-id="752e9-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) okänd eller DUID-typ som inte stöds</span><span class="sxs-lookup"><span data-stu-id="752e9-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Unknown or unsupported DUID type</span></span>
- <span data-ttu-id="752e9-416">**NX_INVALID_PARAMETERS** (0X4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-416">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>
- <span data-ttu-id="752e9-417">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-417">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-418">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-418">**Allowed From**</span></span>

<span data-ttu-id="752e9-419">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-419">Application code</span></span>

<span data-ttu-id="752e9-420">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-420">**Example**</span></span>

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a><span data-ttu-id="752e9-421">nx_dhcpv6_server_option_request_handler_set</span><span class="sxs-lookup"><span data-stu-id="752e9-421">nx_dhcpv6_server_option_request_handler_set</span></span>

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a><span data-ttu-id="752e9-422">Ange option Request Handler för DHCPv6-Server instans</span><span class="sxs-lookup"><span data-stu-id="752e9-422">Set the option request handler for DHCPv6 Server instance</span></span> 

<span data-ttu-id="752e9-423">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="752e9-423">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

<span data-ttu-id="752e9-424">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="752e9-424">**Description**</span></span>

<span data-ttu-id="752e9-425">Den här tjänsten anger hanterings hanteraren för utökade alternativ för DHCPv6-servern.</span><span class="sxs-lookup"><span data-stu-id="752e9-425">This service sets the DHCPv6 Server extended option request handler.</span></span>

<span data-ttu-id="752e9-426">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="752e9-426">**Input Parameters**</span></span>

- <span data-ttu-id="752e9-427">**dhcpv6_server_ptr** Pekare till DHCPv6-server</span><span class="sxs-lookup"><span data-stu-id="752e9-427">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="752e9-428">**dhcpv6_option_request_handler_extended** Pekare till begär ande hanterare för utökade alternativ</span><span class="sxs-lookup"><span data-stu-id="752e9-428">**dhcpv6_option_request_handler_extended** Pointer to extended options request handler</span></span>

<span data-ttu-id="752e9-429">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="752e9-429">**Return Values**</span></span>

- <span data-ttu-id="752e9-430">**NX_SUCCESS** (0X00) servern har återupptagits</span><span class="sxs-lookup"><span data-stu-id="752e9-430">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="752e9-431">NX_PTR_ERROR (0x16) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="752e9-431">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="752e9-432">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="752e9-432">**Allowed From**</span></span>

<span data-ttu-id="752e9-433">Program kod</span><span class="sxs-lookup"><span data-stu-id="752e9-433">Application Code</span></span>

<span data-ttu-id="752e9-434">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="752e9-434">**Example**</span></span>

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```