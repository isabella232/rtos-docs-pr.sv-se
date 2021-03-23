---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP server Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-tjänster för DHCP-server.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826784"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a><span data-ttu-id="41852-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP server Services</span><span class="sxs-lookup"><span data-stu-id="41852-103">Chapter 3 - Description of Azure RTOS NetX DHCP Server services</span></span>

<span data-ttu-id="41852-104">Det här kapitlet innehåller en beskrivning av alla NetX DHCP Server-tjänster.</span><span class="sxs-lookup"><span data-stu-id="41852-104">This chapter contains a description of all NetX DHCP Server services.</span></span>

<span data-ttu-id="41852-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="41852-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="41852-106">**nx_dhcp_server_create**: *skapa en DHCP-serverinstans*</span><span class="sxs-lookup"><span data-stu-id="41852-106">**nx_dhcp_server_create**: *Create a DHCP Server instance*</span></span>
- <span data-ttu-id="41852-107">**nx_dhcp_set_interface_network_parameters**: *ange DHCP-Server alternativ för kritiska nätverks parametrar för det angivna gränssnittet*</span><span class="sxs-lookup"><span data-stu-id="41852-107">**nx_dhcp_set_interface_network_parameters**: *Set DHCP Server options for critical network parameters for specified interface*</span></span>
- <span data-ttu-id="41852-108">**nx_dhcp_create_server_ip_address_list**: *skapa en pool med tillgängliga IP-adresser som ska tilldelas till DHCP-klienter*</span><span class="sxs-lookup"><span data-stu-id="41852-108">**nx_dhcp_create_server_ip_address_list**: *Create pool of available IP addresses to assign to DHCP Clients interface*</span></span>
- <span data-ttu-id="41852-109">**nx_dhcp_clear_client_record**: *ta bort klient posten i Server databasen*</span><span class="sxs-lookup"><span data-stu-id="41852-109">**nx_dhcp_clear_client_record**: *Remove Client record in the Server database*</span></span>
- <span data-ttu-id="41852-110">**nx_dhcp_server_delete**: *ta bort en DHCP-instans*</span><span class="sxs-lookup"><span data-stu-id="41852-110">**nx_dhcp_server_delete**: *Delete a DHCPServer instance*</span></span>
- <span data-ttu-id="41852-111">**nx_dhcp_server_start**: *starta eller återuppta DHCP-server bearbetning*</span><span class="sxs-lookup"><span data-stu-id="41852-111">**nx_dhcp_server_start**: *Start or resume DHCP Server processing*</span></span>
- <span data-ttu-id="41852-112">**nx_dhcp_server_stop**: *stoppa DHCP-server bearbetning*</span><span class="sxs-lookup"><span data-stu-id="41852-112">**nx_dhcp_server_stop**: *Stop DHCP server processing*</span></span>

## <a name="nx_dhcp_server_create"></a><span data-ttu-id="41852-113">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="41852-113">nx_dhcp_server_create</span></span>

<span data-ttu-id="41852-114">Skapa en DHCP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="41852-114">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="41852-115">Prototyp</span><span class="sxs-lookup"><span data-stu-id="41852-115">Prototype</span></span>

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="41852-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41852-116">Description</span></span>

<span data-ttu-id="41852-117">Den här tjänsten skapar en DHCP-serverinstans med en tidigare skapad IP-instans.</span><span class="sxs-lookup"><span data-stu-id="41852-117">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41852-118">Programmet måste se till att den modempool som skapas för tjänsten för IP-skapande har en minimum548 byte-nyttolast, inte inklusive UDP-, IP-och Ethernet-huvudena.</span><span class="sxs-lookup"><span data-stu-id="41852-118">The application must make sure the packet pool created for the IP create service has a minimum548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="41852-119">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="41852-119">Input Parameters</span></span>

- <span data-ttu-id="41852-120">**dhcp_ptr**: pekar mot kontroll block för DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="41852-120">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="41852-121">**ip_ptr**: pekar mot IP-instans för DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="41852-121">**ip_ptr**: Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="41852-122">**stack_ptr**: pekare DHCP-serverns stack plats.</span><span class="sxs-lookup"><span data-stu-id="41852-122">**stack_ptr**: Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="41852-123">**stack_size**: storleken på DHCP-serverns stack</span><span class="sxs-lookup"><span data-stu-id="41852-123">**stack_size**: Size of DHCP Server stack</span></span>
- <span data-ttu-id="41852-124">**input_address_list**: pekar på server lista över IP-adresser</span><span class="sxs-lookup"><span data-stu-id="41852-124">**input_address_list**: Pointer to Server's list of IP addresses</span></span>
- <span data-ttu-id="41852-125">**name_ptr**: pekare till DHCP-servernamnet</span><span class="sxs-lookup"><span data-stu-id="41852-125">**name_ptr**: Pointer to DHCP Server name</span></span>
- <span data-ttu-id="41852-126">**packet_pool_ptr**: pekare till DHCP-serverns pakets bassäng</span><span class="sxs-lookup"><span data-stu-id="41852-126">**packet_pool_ptr**: Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="41852-127">Retur värden</span><span class="sxs-lookup"><span data-stu-id="41852-127">Return Values</span></span>

- <span data-ttu-id="41852-128">**NX_SUCCESS**: (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="41852-128">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="41852-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0XA9) paket nytto last för litet fel</span><span class="sxs-lookup"><span data-stu-id="41852-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="41852-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0X96) Server alternativ listan är tom</span><span class="sxs-lookup"><span data-stu-id="41852-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Server option list is empty</span></span>
- <span data-ttu-id="41852-131">NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="41852-131">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="41852-132">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="41852-132">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="41852-133">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-133">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41852-134">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="41852-134">Allowed From</span></span>

<span data-ttu-id="41852-135">Program</span><span class="sxs-lookup"><span data-stu-id="41852-135">Application</span></span>

### <a name="example"></a><span data-ttu-id="41852-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="41852-136">Example</span></span>

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="41852-137">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="41852-137">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="41852-138">Skapa en IP-adresspool</span><span class="sxs-lookup"><span data-stu-id="41852-138">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="41852-139">Prototyp</span><span class="sxs-lookup"><span data-stu-id="41852-139">Prototype</span></span>

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="41852-140">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41852-140">Description</span></span>

<span data-ttu-id="41852-141">Den här tjänsten skapar en networkinterface specifik pool med tillgängliga IP-adresser för den angivna DHCP-servern som ska tilldelas.</span><span class="sxs-lookup"><span data-stu-id="41852-141">This service creates a networkinterface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="41852-142">Start-och slut-IP-adresserna måste matcha det angivna nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="41852-142">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="41852-143">Det faktiska antalet IP-adresser som lagts till kan vara mindre än det totala antalet adresser om IP-adress listan inte är tillräckligt stor (vilket anges i den användar konfigurerbara *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parametern).</span><span class="sxs-lookup"><span data-stu-id="41852-143">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="41852-144">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="41852-144">Input Parameters</span></span>

- <span data-ttu-id="41852-145">**dhcp_ptr** Pekare till DHCP-serverns kontroll block.</span><span class="sxs-lookup"><span data-stu-id="41852-145">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="41852-146">**iface_index**: index som motsvarar nätverks gränssnittet</span><span class="sxs-lookup"><span data-stu-id="41852-146">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="41852-147">**start_ip_address**: första tillgängliga IP-adress</span><span class="sxs-lookup"><span data-stu-id="41852-147">**start_ip_address**: First available IP address</span></span>
- <span data-ttu-id="41852-148">**end_ip_address**: sista tillgängliga IP-adress</span><span class="sxs-lookup"><span data-stu-id="41852-148">**end_ip_address**: Last of the available IP address</span></span>
- <span data-ttu-id="41852-149">**addresses_added**: antal IP-adresser som lagts till i listan</span><span class="sxs-lookup"><span data-stu-id="41852-149">**addresses_added**: Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="41852-150">Retur värden</span><span class="sxs-lookup"><span data-stu-id="41852-150">Return Values</span></span>

- <span data-ttu-id="41852-151">**NX_SUCCESS**: (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="41852-151">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="41852-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0XA1) indexet matchar inte adresser</span><span class="sxs-lookup"><span data-stu-id="41852-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="41852-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0X99) ogiltig adress indata</span><span class="sxs-lookup"><span data-stu-id="41852-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Invalid address input</span></span>
- <span data-ttu-id="41852-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start-/slut adresser</span><span class="sxs-lookup"><span data-stu-id="41852-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="41852-155">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-155">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41852-156">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="41852-156">Allowed From</span></span>

<span data-ttu-id="41852-157">Program</span><span class="sxs-lookup"><span data-stu-id="41852-157">Application</span></span>

### <a name="example"></a><span data-ttu-id="41852-158">Exempel</span><span class="sxs-lookup"><span data-stu-id="41852-158">Example</span></span>

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="41852-159">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="41852-159">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="41852-160">Ta bort klient posten från Server databasen</span><span class="sxs-lookup"><span data-stu-id="41852-160">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="41852-161">Prototyp</span><span class="sxs-lookup"><span data-stu-id="41852-161">Prototype</span></span>

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="41852-162">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41852-162">Description</span></span>

<span data-ttu-id="41852-163">Den här tjänsten rensar klient posten från Server databasen.</span><span class="sxs-lookup"><span data-stu-id="41852-163">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="41852-164">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="41852-164">Input Parameters</span></span>

- <span data-ttu-id="41852-165">**dhcp_ptr**: pekar mot kontroll block för DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="41852-165">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="41852-166">**dhcp_client_ptr**: pekare till DHCP-klienten som ska tas bort</span><span class="sxs-lookup"><span data-stu-id="41852-166">**dhcp_client_ptr**: Pointer to DHCP Client to remove</span></span>

### <a name="return-values"></a><span data-ttu-id="41852-167">Retur värden</span><span class="sxs-lookup"><span data-stu-id="41852-167">Return Values</span></span>

- <span data-ttu-id="41852-168">**NX_SUCCESS**: (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="41852-168">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="41852-169">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-169">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="41852-170">NX_CALLER_ERROR: (0x11) icke-tråd som anropar tjänsten</span><span class="sxs-lookup"><span data-stu-id="41852-170">NX_CALLER_ERROR: (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41852-171">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="41852-171">Allowed From</span></span>

<span data-ttu-id="41852-172">Program</span><span class="sxs-lookup"><span data-stu-id="41852-172">Application</span></span>

### <a name="example"></a><span data-ttu-id="41852-173">Exempel</span><span class="sxs-lookup"><span data-stu-id="41852-173">Example</span></span>

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="41852-174">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="41852-174">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="41852-175">Ange Nätverks parametrar för DHCP-alternativ</span><span class="sxs-lookup"><span data-stu-id="41852-175">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="41852-176">Prototyp</span><span class="sxs-lookup"><span data-stu-id="41852-176">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="41852-177">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41852-177">Description</span></span>

<span data-ttu-id="41852-178">Den här tjänsten ställer in standardvärden för nätverks kritiska parametrar för det angivna gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="41852-178">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="41852-179">DHCP-servern kommer att inkludera de här alternativen i erbjudandet och bekräftelse svar på DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="41852-179">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="41852-180">Om värd uppsättningens gränssnitts parametrar som en DHCP-server körs på, kommer parametrarna att försättas enligt följande: routern är inställd på den primära gatewayen för DHCP-servern, DNS-serveradressen till själva DHCP-servern och nät masken till samma som DHCP-serverns gränssnitt har kon figurer ATS med.</span><span class="sxs-lookup"><span data-stu-id="41852-180">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="41852-181">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="41852-181">Input Parameters</span></span>

- <span data-ttu-id="41852-182">**dhcp_ptr**: pekar mot kontroll block för DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="41852-182">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="41852-183">**iface_index**: index som motsvarar nätverks gränssnittet</span><span class="sxs-lookup"><span data-stu-id="41852-183">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="41852-184">**subnet_mask**: nät mask för klient nätverk</span><span class="sxs-lookup"><span data-stu-id="41852-184">**subnet_mask**: Subnet mask for Client network</span></span>
- <span data-ttu-id="41852-185">**default_gateway_address**: klientens IP-adress för router</span><span class="sxs-lookup"><span data-stu-id="41852-185">**default_gateway_address**: Client's router IP address</span></span>
- <span data-ttu-id="41852-186">**dns_server_address**: DNS-server för klient nätverk</span><span class="sxs-lookup"><span data-stu-id="41852-186">**dns_server_address**: DNS server for Client's network</span></span>

### <a name="return-values"></a><span data-ttu-id="41852-187">Retur värden</span><span class="sxs-lookup"><span data-stu-id="41852-187">Return Values</span></span>

- <span data-ttu-id="41852-188">**NX_SUCCESS**: (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="41852-188">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="41852-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0XA1) indexet matchar inte adresser</span><span class="sxs-lookup"><span data-stu-id="41852-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="41852-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0XA3) ogiltiga nätverks parametrar</span><span class="sxs-lookup"><span data-stu-id="41852-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="41852-191">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-191">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41852-192">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="41852-192">Allowed From</span></span>

<span data-ttu-id="41852-193">Program</span><span class="sxs-lookup"><span data-stu-id="41852-193">Application</span></span>

### <a name="example"></a><span data-ttu-id="41852-194">Exempel</span><span class="sxs-lookup"><span data-stu-id="41852-194">Example</span></span>

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="41852-195">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="41852-195">nx_dhcp_server_delete</span></span>

<span data-ttu-id="41852-196">Ta bort en DHCP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="41852-196">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="41852-197">Prototyp</span><span class="sxs-lookup"><span data-stu-id="41852-197">Prototype</span></span>

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="41852-198">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41852-198">Description</span></span>

<span data-ttu-id="41852-199">Den här tjänsten tar bort en tidigare skapad DHCP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="41852-199">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="41852-200">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="41852-200">Input Parameters</span></span>

- <span data-ttu-id="41852-201">**dhcp_ptr**: pekar mot en DHCP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="41852-201">**dhcp_ptr**: Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41852-202">Retur värden</span><span class="sxs-lookup"><span data-stu-id="41852-202">Return Values</span></span>

- <span data-ttu-id="41852-203">**NX_SUCCESS**: (0X00) DHCP-servern har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="41852-203">**NX_SUCCESS**: (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="41852-204">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-204">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="41852-205">NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="41852-205">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="41852-206">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="41852-206">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41852-207">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="41852-207">Allowed From</span></span>

<span data-ttu-id="41852-208">Konversation</span><span class="sxs-lookup"><span data-stu-id="41852-208">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41852-209">Exempel</span><span class="sxs-lookup"><span data-stu-id="41852-209">Example</span></span>

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="41852-210">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="41852-210">nx_dhcp_server_start</span></span>

<span data-ttu-id="41852-211">Starta bearbetning av DHCP-server</span><span class="sxs-lookup"><span data-stu-id="41852-211">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="41852-212">Prototyp</span><span class="sxs-lookup"><span data-stu-id="41852-212">Prototype</span></span>

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="41852-213">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41852-213">Description</span></span>

<span data-ttu-id="41852-214">Den här tjänsten startar DHCP-server bearbetning, vilket innefattar att skapa en server UDP-socket, binda DHCP-porten och vänta på att ta emot klient-DHCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="41852-214">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="41852-215">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="41852-215">Input Parameters</span></span>

- <span data-ttu-id="41852-216">**dhcp_ptr**: pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="41852-216">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41852-217">Retur värden</span><span class="sxs-lookup"><span data-stu-id="41852-217">Return Values</span></span>

- <span data-ttu-id="41852-218">**NX_SUCCESS**: (0X00) lyckad Server start.</span><span class="sxs-lookup"><span data-stu-id="41852-218">**NX_SUCCESS**: (0x00) Successful Server start.</span></span>  
- <span data-ttu-id="41852-219">**NX_DHCP_ALREADY_STARTED**: (0X93) DHCP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="41852-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="41852-220">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-220">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="41852-221">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="41852-221">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="41852-222">NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="41852-222">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41852-223">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="41852-223">Allowed From</span></span>

<span data-ttu-id="41852-224">Konversation</span><span class="sxs-lookup"><span data-stu-id="41852-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41852-225">Exempel</span><span class="sxs-lookup"><span data-stu-id="41852-225">Example</span></span>

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="41852-226">Se även</span><span class="sxs-lookup"><span data-stu-id="41852-226">See Also</span></span>

<span data-ttu-id="41852-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="41852-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span></span>

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="41852-228">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="41852-228">nx_dhcp_server_stop</span></span>

<span data-ttu-id="41852-229">Stoppar DHCP-server bearbetning</span><span class="sxs-lookup"><span data-stu-id="41852-229">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="41852-230">Prototyp</span><span class="sxs-lookup"><span data-stu-id="41852-230">Prototype</span></span>

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="41852-231">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="41852-231">Description</span></span>

<span data-ttu-id="41852-232">Den här tjänsten stoppar DHCP-serverns bearbetning, vilket innefattar att ta emot begär Anden om DHCP-klienter.</span><span class="sxs-lookup"><span data-stu-id="41852-232">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="41852-233">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="41852-233">Input Parameters</span></span>

- <span data-ttu-id="41852-234">**dhcp_ptr**: pekar mot DHCP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="41852-234">**dhcp_ptr**: Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41852-235">Retur värden</span><span class="sxs-lookup"><span data-stu-id="41852-235">Return Values</span></span>

- <span data-ttu-id="41852-236">**NX_SUCCESS**: (0X00) DHCP-stopp har slutförts.</span><span class="sxs-lookup"><span data-stu-id="41852-236">**NX_SUCCESS**: (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="41852-237">**NX_DHCP_ALREADY_STARTED**: (0X93) DHCP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="41852-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="41852-238">NX_PTR_ERROR: (0x16) ogiltigt inmatade pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-238">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="41852-239">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="41852-239">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="41852-240">NX_DHCP_PARAMETER_ERROR: (0x92) ogiltig inmatad icke-pekare.</span><span class="sxs-lookup"><span data-stu-id="41852-240">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41852-241">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="41852-241">Allowed From</span></span>

<span data-ttu-id="41852-242">Konversation</span><span class="sxs-lookup"><span data-stu-id="41852-242">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41852-243">Exempel</span><span class="sxs-lookup"><span data-stu-id="41852-243">Example</span></span>

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
