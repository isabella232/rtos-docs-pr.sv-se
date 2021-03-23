---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DHCP server Services
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCP Server-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826106"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a><span data-ttu-id="ab2b1-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DHCP server Services</span><span class="sxs-lookup"><span data-stu-id="ab2b1-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Server Services</span></span>

<span data-ttu-id="ab2b1-104">Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCP Server-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-104">This chapter contains a description of all NetX Duo DHCP Server services (listed below) in alphabetic order.</span></span>

> [!NOTE]
> <span data-ttu-id="ab2b1-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_dhcp_server-create"></a><span data-ttu-id="ab2b1-106">nx_dhcp_server skapa</span><span class="sxs-lookup"><span data-stu-id="ab2b1-106">nx_dhcp_server create</span></span>

<span data-ttu-id="ab2b1-107">Skapa en DHCP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="ab2b1-107">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab2b1-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab2b1-108">Prototype</span></span>

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ab2b1-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-109">Description</span></span>

<span data-ttu-id="ab2b1-110">Den här tjänsten skapar en DHCP-serverinstans med en tidigare skapad IP-instans.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-110">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab2b1-111">Programmet måste se till att Packet-poolen som skapas för tjänsten för IP-skapande har en minimal 548 byte-nyttolast, inte inklusive UDP-, IP-och Ethernet-huvudena.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-111">The application must make sure the packet pool created for the IP create service has a minimum 548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab2b1-112">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-112">Input Parameters</span></span>

- <span data-ttu-id="ab2b1-113">**dhcp_ptr** Pekare till DHCP-serverns kontroll block.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-113">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="ab2b1-114">**ip_ptr** Pekare till DHCP-serverns IP-instans.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-114">**ip_ptr** Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="ab2b1-115">**stack_ptr** Pekare för DHCP-serverns stack plats.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-115">**stack_ptr** Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="ab2b1-116">**Stack_size storleken på DHCP-serverns stack** input_address_list pekare till server lista över IP-adresser</span><span class="sxs-lookup"><span data-stu-id="ab2b1-116">**stack_size Size of DHCP Server stack** input_address_list Pointer to Server’s list of IP addresses</span></span>
- <span data-ttu-id="ab2b1-117">**Name_ptr pekare till DHCP-serverns namn** packet_pool_ptr pekare till DHCP-serverns paket-pool</span><span class="sxs-lookup"><span data-stu-id="ab2b1-117">**name_ptr Pointer to DHCP Server name** packet_pool_ptr Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ab2b1-118">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab2b1-118">Return Values</span></span>

- <span data-ttu-id="ab2b1-119">**NX_SUCCESS** (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-119">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ab2b1-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0XA9) paket nytto last för litet fel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="ab2b1-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0X96) Server alternativ listan är tom</span><span class="sxs-lookup"><span data-stu-id="ab2b1-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) Server option list is empty</span></span>
- <span data-ttu-id="ab2b1-122">NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="ab2b1-122">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="ab2b1-123">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-123">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ab2b1-124">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-124">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab2b1-125">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab2b1-125">Allowed From</span></span>

<span data-ttu-id="ab2b1-126">Program</span><span class="sxs-lookup"><span data-stu-id="ab2b1-126">Application</span></span>

### <a name="example"></a><span data-ttu-id="ab2b1-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-127">Example</span></span>

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="ab2b1-128">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="ab2b1-128">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="ab2b1-129">Skapa en IP-adresspool</span><span class="sxs-lookup"><span data-stu-id="ab2b1-129">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ab2b1-130">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab2b1-130">Prototype</span></span>

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="ab2b1-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-131">Description</span></span>

<span data-ttu-id="ab2b1-132">Den här tjänsten skapar en specifik pool med tillgängliga IP-adresser för den angivna DHCP-servern som ska tilldelas.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-132">This service creates a network interface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="ab2b1-133">Start-och slut-IP-adresserna måste matcha det angivna nätverks gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-133">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="ab2b1-134">Det faktiska antalet IP-adresser som lagts till kan vara mindre än det totala antalet adresser om IP-adress listan inte är tillräckligt stor (vilket anges i den användar konfigurerbara *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parametern).</span><span class="sxs-lookup"><span data-stu-id="ab2b1-134">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab2b1-135">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-135">Input Parameters</span></span>

- <span data-ttu-id="ab2b1-136">**dhcp_ptr** Pekare till DHCP-serverns kontroll block.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-136">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="ab2b1-137">**iface_index** Index som motsvarar nätverks gränssnittet</span><span class="sxs-lookup"><span data-stu-id="ab2b1-137">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="ab2b1-138">**start_ip_address** Första tillgängliga IP-adress</span><span class="sxs-lookup"><span data-stu-id="ab2b1-138">**start_ip_address** First available IP address</span></span>
- <span data-ttu-id="ab2b1-139">**end_ip_address** Sista tillgängliga IP-adress</span><span class="sxs-lookup"><span data-stu-id="ab2b1-139">**end_ip_address** Last of the available IP address</span></span>
- <span data-ttu-id="ab2b1-140">**addresses_added** Antal IP-adresser som lagts till i listan</span><span class="sxs-lookup"><span data-stu-id="ab2b1-140">**addresses_added** Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="ab2b1-141">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab2b1-141">Return Values</span></span>

- <span data-ttu-id="ab2b1-142">**NX_SUCCESS** (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-142">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ab2b1-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0XA1) indexet matchar inte adresser</span><span class="sxs-lookup"><span data-stu-id="ab2b1-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="ab2b1-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0X99) ogiltig adress indata</span><span class="sxs-lookup"><span data-stu-id="ab2b1-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Invalid address input</span></span>
- <span data-ttu-id="ab2b1-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start-/slut adresser</span><span class="sxs-lookup"><span data-stu-id="ab2b1-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="ab2b1-146">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-146">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab2b1-147">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab2b1-147">Allowed From</span></span>

<span data-ttu-id="ab2b1-148">Program</span><span class="sxs-lookup"><span data-stu-id="ab2b1-148">Application</span></span>

### <a name="example"></a><span data-ttu-id="ab2b1-149">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-149">Example</span></span>

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="ab2b1-150">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="ab2b1-150">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="ab2b1-151">Ta bort klient posten från Server databasen</span><span class="sxs-lookup"><span data-stu-id="ab2b1-151">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="ab2b1-152">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab2b1-152">Prototype</span></span>

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="ab2b1-153">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-153">Description</span></span>

<span data-ttu-id="ab2b1-154">Den här tjänsten rensar klient posten från Server databasen.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-154">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab2b1-155">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-155">Input Parameters</span></span>

- <span data-ttu-id="ab2b1-156">**dhcp_ptr** Pekare till DHCP-serverns kontroll block.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-156">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="ab2b1-157">**dhcp_client_ptr pekare till DHCP-klienten som ska tas bort**</span><span class="sxs-lookup"><span data-stu-id="ab2b1-157">**dhcp_client_ptr Pointer to DHCP Client to remove**</span></span>

### <a name="return-values"></a><span data-ttu-id="ab2b1-158">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab2b1-158">Return Values</span></span>

- <span data-ttu-id="ab2b1-159">**NX_SUCCESS** (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-159">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ab2b1-160">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-160">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ab2b1-161">NX_CALLER_ERROR (0x11) icke-tråd som anropar tjänsten</span><span class="sxs-lookup"><span data-stu-id="ab2b1-161">NX_CALLER_ERROR (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab2b1-162">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab2b1-162">Allowed From</span></span>

<span data-ttu-id="ab2b1-163">Program</span><span class="sxs-lookup"><span data-stu-id="ab2b1-163">Application</span></span>

### <a name="example"></a><span data-ttu-id="ab2b1-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-164">Example</span></span>

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="ab2b1-165">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="ab2b1-165">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="ab2b1-166">Ange Nätverks parametrar för DHCP-alternativ</span><span class="sxs-lookup"><span data-stu-id="ab2b1-166">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="ab2b1-167">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab2b1-167">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="ab2b1-168">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-168">Description</span></span>

<span data-ttu-id="ab2b1-169">Den här tjänsten ställer in standardvärden för nätverks kritiska parametrar för det angivna gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-169">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="ab2b1-170">DHCP-servern kommer att inkludera de här alternativen i erbjudandet och bekräftelse svar på DHCP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-170">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="ab2b1-171">Om värd uppsättningens gränssnitts parametrar som en DHCP-server körs på, kommer parametrarna att försättas enligt följande: routern är inställd på den primära gatewayen för DHCP-servern, DNS-serveradressen till själva DHCP-servern och nät masken till samma som DHCP-serverns gränssnitt har kon figurer ATS med.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-171">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab2b1-172">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-172">Input Parameters</span></span>

- <span data-ttu-id="ab2b1-173">**dhcp_ptr** Pekare till DHCP-serverns kontroll block.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-173">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="ab2b1-174">**iface_index** Index som motsvarar nätverks gränssnittet</span><span class="sxs-lookup"><span data-stu-id="ab2b1-174">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="ab2b1-175">**subnet_mask** Nätmask för klient nätverk</span><span class="sxs-lookup"><span data-stu-id="ab2b1-175">**subnet_mask** Subnet mask for Client network</span></span>
- <span data-ttu-id="ab2b1-176">**default_gateway_address** Klientens IP-adress för router</span><span class="sxs-lookup"><span data-stu-id="ab2b1-176">**default_gateway_address** Client’s router IP address</span></span>
- <span data-ttu-id="ab2b1-177">**dns_server_address** DNS-server för klient nätverk</span><span class="sxs-lookup"><span data-stu-id="ab2b1-177">**dns_server_address** DNS server for Client’s network</span></span>

### <a name="return-values"></a><span data-ttu-id="ab2b1-178">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab2b1-178">Return Values</span></span>

- <span data-ttu-id="ab2b1-179">**NX_SUCCESS** (0X00) DHCP-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-179">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="ab2b1-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0XA1) indexet matchar inte adresser</span><span class="sxs-lookup"><span data-stu-id="ab2b1-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="ab2b1-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0XA3) ogiltiga nätverks parametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="ab2b1-182">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-182">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab2b1-183">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab2b1-183">Allowed From</span></span>

<span data-ttu-id="ab2b1-184">Program</span><span class="sxs-lookup"><span data-stu-id="ab2b1-184">Application</span></span>

### <a name="example"></a><span data-ttu-id="ab2b1-185">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-185">Example</span></span>

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="ab2b1-186">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="ab2b1-186">nx_dhcp_server_delete</span></span>

<span data-ttu-id="ab2b1-187">Ta bort en DHCP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="ab2b1-187">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab2b1-188">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab2b1-188">Prototype</span></span>

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab2b1-189">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-189">Description</span></span>

<span data-ttu-id="ab2b1-190">Den här tjänsten tar bort en tidigare skapad DHCP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-190">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab2b1-191">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-191">Input Parameters</span></span>

- <span data-ttu-id="ab2b1-192">**dhcp_ptr** Pekare till en DHCP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-192">**dhcp_ptr** Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab2b1-193">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab2b1-193">Return Values</span></span>

- <span data-ttu-id="ab2b1-194">**NX_SUCCESS** (0X00) DHCP-servern har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-194">**NX_SUCCESS** (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="ab2b1-195">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-195">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ab2b1-196">NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="ab2b1-196">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="ab2b1-197">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-197">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab2b1-198">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab2b1-198">Allowed From</span></span>

<span data-ttu-id="ab2b1-199">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab2b1-199">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab2b1-200">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-200">Example</span></span>

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="ab2b1-201">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="ab2b1-201">nx_dhcp_server_start</span></span>

<span data-ttu-id="ab2b1-202">Starta bearbetning av DHCP-server</span><span class="sxs-lookup"><span data-stu-id="ab2b1-202">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ab2b1-203">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab2b1-203">Prototype</span></span>

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab2b1-204">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-204">Description</span></span>

<span data-ttu-id="ab2b1-205">Den här tjänsten startar DHCP-server bearbetning, vilket innefattar att skapa en server UDP-socket, binda DHCP-porten och vänta på att ta emot klient-DHCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-205">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab2b1-206">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-206">Input Parameters</span></span>

- <span data-ttu-id="ab2b1-207">**dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-207">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab2b1-208">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab2b1-208">Return Values</span></span>

- <span data-ttu-id="ab2b1-209">**NX_SUCCESS** (0X00) Server start har slutförts.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-209">**NX_SUCCESS** (0x00) Successful Server start.</span></span>
- <span data-ttu-id="ab2b1-210">**NX_DHCP_ALREADY_STARTED** (0X93) DHCP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ab2b1-211">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-211">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ab2b1-212">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-212">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ab2b1-213">NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="ab2b1-213">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab2b1-214">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab2b1-214">Allowed From</span></span>

<span data-ttu-id="ab2b1-215">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab2b1-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab2b1-216">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-216">Example</span></span>

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="ab2b1-217">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="ab2b1-217">nx_dhcp_server_stop</span></span>

<span data-ttu-id="ab2b1-218">Stoppar DHCP-server bearbetning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-218">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ab2b1-219">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab2b1-219">Prototype</span></span>

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ab2b1-220">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab2b1-220">Description</span></span>

<span data-ttu-id="ab2b1-221">Den här tjänsten stoppar DHCP-serverns bearbetning, vilket innefattar att ta emot begär Anden om DHCP-klienter.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-221">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab2b1-222">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab2b1-222">Input Parameters</span></span>

- <span data-ttu-id="ab2b1-223">**dhcp_ptr** Pekare till DHCP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-223">**dhcp_ptr** Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab2b1-224">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab2b1-224">Return Values</span></span>

- <span data-ttu-id="ab2b1-225">**NX_SUCCESS** (0X00) DHCP-stopp.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-225">**NX_SUCCESS** (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="ab2b1-226">**NX_DHCP_ALREADY_STARTED** (0X93) DHCP har redan startats.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ab2b1-227">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-227">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="ab2b1-228">NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="ab2b1-228">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ab2b1-229">NX_DHCP_PARAMETER_ERROR (0x92) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="ab2b1-229">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab2b1-230">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab2b1-230">Allowed From</span></span>

<span data-ttu-id="ab2b1-231">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab2b1-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab2b1-232">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab2b1-232">Example</span></span>

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
