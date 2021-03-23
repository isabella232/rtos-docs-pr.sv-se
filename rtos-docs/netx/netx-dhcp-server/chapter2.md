---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX DHCP-servern
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av komponenten Azure återställnings tider NetX DHCP-server.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 034a4d74c566fbfe94981a42b7e06e7f2ee79d25
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826790"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a><span data-ttu-id="8d971-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX DHCP-servern</span><span class="sxs-lookup"><span data-stu-id="8d971-103">Chapter 2 - Installation and use of the Azure RTOS NetX DHCP Server</span></span>

<span data-ttu-id="8d971-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX DHCP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="8d971-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="8d971-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="8d971-105">Product Distribution</span></span>

<span data-ttu-id="8d971-106">Azure återställnings tider NetX DHCP-server kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="8d971-106">Azure RTOS NetX DHCP Server can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="8d971-107">Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d971-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="8d971-108">**nx_dhcp_server. h**: rubrik fil för netx DHCP-server</span><span class="sxs-lookup"><span data-stu-id="8d971-108">**nx_dhcp_server.h**: Header file for NetX DHCP Server</span></span>
- <span data-ttu-id="8d971-109">**nx_dhcp_server. c**: c-källfil för netx DHCP-server</span><span class="sxs-lookup"><span data-stu-id="8d971-109">**nx_dhcp_server.c**: C Source file for NetX DHCP Server</span></span>
- <span data-ttu-id="8d971-110">**nx_dhcp_server.pdf**: PDF-Beskrivning av netx DHCP-server</span><span class="sxs-lookup"><span data-stu-id="8d971-110">**nx_dhcp_server.pdf**: PDF description of NetX DHCP Server</span></span>
- <span data-ttu-id="8d971-111">**demo_netx_dhcp_server. c**: netx DHCP-server demonstration</span><span class="sxs-lookup"><span data-stu-id="8d971-111">**demo_netx_dhcp_server.c**: NetX DHCP Server demonstration</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="8d971-112">DHCP-installation</span><span class="sxs-lookup"><span data-stu-id="8d971-112">DHCP Installation</span></span>

<span data-ttu-id="8d971-113">För att kunna använda NetX DHCP-server, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats.</span><span class="sxs-lookup"><span data-stu-id="8d971-113">In order to use NetX DHCP Server, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="8d971-114">Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_dhcp_server. h* -och *nx_dhpc_server. c* -filerna kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="8d971-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_dhcp_server.h* and *nx_dhpc_server.c* files should be copied into this directory.</span></span>

## <a name="using-netx-dhcp-server"></a><span data-ttu-id="8d971-115">Använda NetX DHCP-server</span><span class="sxs-lookup"><span data-stu-id="8d971-115">Using NetX DHCP Server</span></span>

<span data-ttu-id="8d971-116">Det är enkelt att använda NetX DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="8d971-116">Using NetX DHCP Server is easy.</span></span> <span data-ttu-id="8d971-117">I princip måste program koden innehålla *nx_dhcp_server. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX respektive netx.</span><span class="sxs-lookup"><span data-stu-id="8d971-117">Basically, the application code must include *nx_dhcp_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="8d971-118">När *nx_dhcp_server. h* ingår kan program koden sedan göra DHCP-funktions anropen angivna senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="8d971-118">Once *nx_dhcp_server.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="8d971-119">Programmet måste även innehålla *nx_dhcp_server. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="8d971-119">The application must also include *nx_dhcp_server.c* in the build process.</span></span> <span data-ttu-id="8d971-120">Den här filen måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="8d971-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="8d971-121">Mer information om hur du använder NetX DHCP-server finns i följande avsnitt [krav för netx](#requirements-of-the-netx-dhcp-server) DHCP [Server och begränsningar för netx DHCP-server](#constraints-of-the-netx-dhcp-server).</span><span class="sxs-lookup"><span data-stu-id="8d971-121">For more details on using NetX DHCP Server, see the following sections [Requirements of the NetX DHCPServer](#requirements-of-the-netx-dhcp-server) and [Constraints of the NetX DHCP Server](#constraints-of-the-netx-dhcp-server).</span></span>

> [!NOTE]
> <span data-ttu-id="8d971-122">Eftersom DHCP använder sig av NetX UDP-tjänster måste UDP aktive ras med det *nx_udp_enable* samtalet innan DHCP används.</span><span class="sxs-lookup"><span data-stu-id="8d971-122">Since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

## <a name="requirements-of-the-netx-dhcp-server"></a><span data-ttu-id="8d971-123">Krav för DHCP-servern NetX</span><span class="sxs-lookup"><span data-stu-id="8d971-123">Requirements of the NetX DHCP Server</span></span>

<span data-ttu-id="8d971-124">NetX DHCP-servern kräver en UDP-socketanslutning som tilldelats den välkända DHCP-porten 67.</span><span class="sxs-lookup"><span data-stu-id="8d971-124">The NetX DHCP Server requires a UDP socket port assigned to the well known DHCP port 67.</span></span> <span data-ttu-id="8d971-125">För att skapa DHCP-servern måste programmet skapa en modempool med paket nytto Last minst 548 byte plus IP-, UDP-och Ethernet-huvuden (som totalt 44 byte med 4 byte justering).</span><span class="sxs-lookup"><span data-stu-id="8d971-125">To create the DHCP Server, the application must create a packet pool with packet payload at least 548 bytes plus IP, UDP and Ethernet headers (which total 44 bytes with 4 byte alignment).</span></span>

<span data-ttu-id="8d971-126">Det förutsätts att både servern och klienten använder inställningarna för Ethernet-maskinvara:</span><span class="sxs-lookup"><span data-stu-id="8d971-126">It is assumed that the Server and Client are both using Ethernet hardware address settings:</span></span>

- <span data-ttu-id="8d971-127">**Maskin varu typ**: 1</span><span class="sxs-lookup"><span data-stu-id="8d971-127">**Hardware type**: 1</span></span>
- <span data-ttu-id="8d971-128">**Maskin varu längd**: 6</span><span class="sxs-lookup"><span data-stu-id="8d971-128">**Hardware length**: 6</span></span>
- <span data-ttu-id="8d971-129">**Hopp**: 0</span><span class="sxs-lookup"><span data-stu-id="8d971-129">**Hops**: 0</span></span>

### <a name="multiple-client-sessions"></a><span data-ttu-id="8d971-130">Flera klientsessioner</span><span class="sxs-lookup"><span data-stu-id="8d971-130">Multiple Client Sessions</span></span>

<span data-ttu-id="8d971-131">NetX DHCP-servern kan hantera flera klientsessioner genom att ha en tabell med aktiva DHCP-klienter och det tillstånd som klienten är i t. ex. DHCP-tillstånd INIT, start, välja, begära, förnya osv. Om tids gränsen för sessionen upphör att gälla innan nästa klient meddelande tas emot, om inte klienten är kopplad till ett IP-lån, rensar servern klientens sessionsdata och returnerar den tilldelade IP-adressen till den tillgängliga poolen.</span><span class="sxs-lookup"><span data-stu-id="8d971-131">The NetX DHCP Server can handles multiple Client sessions by keeping a table of active DHCP clients and what 'state' the Client is in e.g. DHCP states INIT, BOOT, SELECTING, REQUESTING, RENEWING etc. If the session time out expires before receiving the next Client message, unless that Client is bound to an IP lease, the Server will clear the Client session data and return the assigned IP address back to the available pool.</span></span> <span data-ttu-id="8d971-132">Om servern tar emot flera IDENTIFIERINGs meddelanden från samma klient återställs tids gränsen för sessionen och den IP-adress som är reserverad för klienten godkänns i ett efterföljande begär ande meddelande.</span><span class="sxs-lookup"><span data-stu-id="8d971-132">If the Server receives multiple DISCOVER messages from the same Client the Server resets the session time out and keeps the IP address reserved for the Client to accept in a subsequent REQUEST message.</span></span>

<span data-ttu-id="8d971-133">DHCP-NetX accepterar också klient-begäran med enskild tillstånd, t. ex. klienten skickar endast ett meddelande om begär Ande.</span><span class="sxs-lookup"><span data-stu-id="8d971-133">The NetX DHCP Server also accepts the single state Client DHCP request e.g. the Client only sends a REQUEST message.</span></span> <span data-ttu-id="8d971-134">Detta förutsätter att klienten har tilldelats ett IP-lån från DHCP-servern tidigare.</span><span class="sxs-lookup"><span data-stu-id="8d971-134">This assumes the Client has been previously assigned an IP lease from the DHCP server.</span></span>

### <a name="setting-interface-specific-network-parameters-server-responses"></a><span data-ttu-id="8d971-135">Ställer in gränssnitts information Server svar för nätverks parametrar</span><span class="sxs-lookup"><span data-stu-id="8d971-135">Setting Interface Specific Network Parameters Server Responses</span></span>

<span data-ttu-id="8d971-136">Programmet kan ange router, nätmask och DNS-serverns parametrar för varje gränssnitt som hanteras av DHCP-klienter med hjälp av tjänsten *nx_dhcp_set_interface_network_parameters* .</span><span class="sxs-lookup"><span data-stu-id="8d971-136">The application can set the router, subnet mask and DNS server parameters for each interface it handles DHCP Client requests, using the *nx_dhcp_set_interface_network_parameters* service.</span></span> <span data-ttu-id="8d971-137">Annars är dessa parametrar standardiserade till IP-gatewayen på serverns primära gränssnitt, dess DHCP-undernät och IP-adressen för DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d971-137">Otherwise these parameters are defaulted to the IP gateway on the Server's primary interface, its DHCP network subnet, and DHCP Server IP address, respectively.</span></span>

<span data-ttu-id="8d971-138">DHCP-servern inkluderar dessa parametrar i alternativ data för DHCP-meddelanden som skickas till DHCP-klienter.</span><span class="sxs-lookup"><span data-stu-id="8d971-138">The DHCP Server includes these parameters in the option data of DHCP messages it sends to DHCP clients.</span></span>

### <a name="assigning-ip-addresses-to-the-client"></a><span data-ttu-id="8d971-139">Tilldela IP-adresser till klienten</span><span class="sxs-lookup"><span data-stu-id="8d971-139">Assigning IP addresses to the Client</span></span>

<span data-ttu-id="8d971-140">Om klient IDENTIFIERINGs meddelandet inte anger någon begärd IP-adress kan DHCP-servern använda en från sin egen pool.</span><span class="sxs-lookup"><span data-stu-id="8d971-140">If the Client DISCOVER message does not specify a requested IP address, the DHCP Server can use one from its own pool.</span></span> <span data-ttu-id="8d971-141">Om servern inte har några tillgängliga IP-adresser kommer den att skicka ett NACK-meddelande till klienten.</span><span class="sxs-lookup"><span data-stu-id="8d971-141">If the Server has no available IP addresses it will send the Client a NACK message.</span></span>

<span data-ttu-id="8d971-142">NetX DHCP-servern kommer att bevilja den begärda IP-adressen i klient begär ande meddelandet så länge IP-adressen är tillgänglig och finns i serverns IP-serverdatabas.</span><span class="sxs-lookup"><span data-stu-id="8d971-142">The NetX DHCP Server will grant the requested IP address in the Client REQUEST message as long as the IP address is available and can be found in the Server IP address database.</span></span> <span data-ttu-id="8d971-143">Programmet skapar serverns lista över tillgängliga IP-adresser för att tilldela DHCP-klienter med hjälp av tjänsten *nx_dhcp_create_server_ip_address_list* .</span><span class="sxs-lookup"><span data-stu-id="8d971-143">The application creates the Server's list of available IP addresses for assigning to DHCP Clients using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="8d971-144">Om servern inte har de begärda IP-adresserna eller om den är tilldelad till en annan värd kommer den att skicka ett NACK-meddelande till klienten.</span><span class="sxs-lookup"><span data-stu-id="8d971-144">If the Server does not have the requested IP addresses or it is assigned to another host it will send the Client a NACK message.</span></span>

<span data-ttu-id="8d971-145">När DHCP-servern tar emot en klientbegäran, identifierar den klienten unikt med klientens MAC-adress i fältet klientens MAC-adress i DHCP-meddelandet.</span><span class="sxs-lookup"><span data-stu-id="8d971-145">When the DHCP Server receives a Client request, it identifies that Client uniquely using the Client MAC address in the Client MAC address field in the DHCP message.</span></span> <span data-ttu-id="8d971-146">Om klienten ändrar sin MAC-adress eller flyttas någon annan stans till ett annat undernät bör den skicka ett RELEASE-meddelande till servern för att returnera IP-adressen tillbaka till den tillgängliga poolen och begära en ny IP-adress i INIT-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8d971-146">If the Client changes it's MAC address or is moved elsewhere onto another subnet it should send a RELEASE message to the Server to return the IP address back to the available pool, and request a new IP address in the INIT state.</span></span>

<span data-ttu-id="8d971-147">Mer information finns i bild 1,1 i system avsnittet för **små exempel** .</span><span class="sxs-lookup"><span data-stu-id="8d971-147">See Figure 1.1 of the **Small Example System** section for details.</span></span> <span data-ttu-id="8d971-148">Antalet IP-adresser som sparas till DHCP-serverinstansen är begränsat till storleken på server adress matrisen i DHCP-serverns kontroll block och definieras av det konfigurerbara alternativet NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span><span class="sxs-lookup"><span data-stu-id="8d971-148">The number of IP addresses saved to the DHCP Server instance is limited to the size of the server address array in the DHCP Server control block, and defined by the configurable option NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span></span>

### <a name="ip-address-lease-times"></a><span data-ttu-id="8d971-149">IP-adressens låne tider</span><span class="sxs-lookup"><span data-stu-id="8d971-149">IP Address Lease Times</span></span>

<span data-ttu-id="8d971-150">DHCP-servern kommer också att acceptera låne tiden för klient begär Anden om den här låne tiden är mindre än serverns standard låne tid som definieras i konfigurerbart alternativ NX_DHCP_DEFAULT_LEASE_TIME.</span><span class="sxs-lookup"><span data-stu-id="8d971-150">The DHCP Server will also accept the request Client lease time if that lease time is less than the Server default lease time which is defined in configurable option NX_DHCP_DEFAULT_LEASE_TIME.</span></span> <span data-ttu-id="8d971-151">Förnyelse-och återbind-tider som tilldelats till klienten är 50% och 85% av låne tiden, om inte låne tiden är oändlig (0xFFFFFFFF), vilket innebär att förnyelse och OMBINDNINGS tid också anges till oändlighet.</span><span class="sxs-lookup"><span data-stu-id="8d971-151">Renewal and rebind times assigned to the Client are 50% and 85% of the lease time, respectively, unless the lease time is infinity (0xFFFFFFFF), in which case renewal and rebind times are also set to infinity.</span></span>

### <a name="dhcp-server-timeouts"></a><span data-ttu-id="8d971-152">Timeout för DHCP-server</span><span class="sxs-lookup"><span data-stu-id="8d971-152">DHCP Server Timeouts</span></span>

<span data-ttu-id="8d971-153">DHCP-servern har en tids gräns för användare som kan konfigureras, NX_DHCP_CLIENT_SESSION_TIMEOUT, för att vänta på nästa DHCP-klientcertifikat om inte sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="8d971-153">The DHCP Server has a user configurable session timeout, NX_DHCP_CLIENT_SESSION_TIMEOUT, for waiting for the next DHCP Client message unless the session is completed.</span></span> <span data-ttu-id="8d971-154">Tids gränsen återställs när servern tar emot nästa meddelande från klienten oavsett om samma meddelande redan har skickats.</span><span class="sxs-lookup"><span data-stu-id="8d971-154">The time out is reset when the Server receives the next message from the Client regardless if is the same message previously sent.</span></span>

### <a name="internal-error-handling"></a><span data-ttu-id="8d971-155">Intern fel hantering</span><span class="sxs-lookup"><span data-stu-id="8d971-155">Internal error handling</span></span>

<span data-ttu-id="8d971-156">DHCP-servern tar emot och bearbetar DHCP-klientens paket i *nx_dhcp_listen_for_messages* -funktionen.</span><span class="sxs-lookup"><span data-stu-id="8d971-156">The DHCP Server receives and processes DHCP Client packets in the *nx_dhcp_listen_for_messages* function.</span></span> <span data-ttu-id="8d971-157">Den här funktionen upphör att bearbeta det aktuella DHCP-klientprogrammet om paketet är ogiltigt, eller så påträffar DHCP-servern ett internt fel. n *x_dhcp_listen_for_messages* returnerar en fel status.</span><span class="sxs-lookup"><span data-stu-id="8d971-157">This function will discontinue processing the current DHCP Client packet if the packet is invalid, or the DHCP Server encounters an internal error.n *x_dhcp_listen_for_messages* returns an error status.</span></span> <span data-ttu-id="8d971-158">DHCP-serverrollen låser sig kort av ThreadX Scheduler innan den här funktionen anropas för att ta emot nästa DHCP-klient meddelande.</span><span class="sxs-lookup"><span data-stu-id="8d971-158">The DHCP Server thread relinquishes control briefly of the ThreadX scheduler before calling this function to receive the next DHCP Client message.</span></span> <span data-ttu-id="8d971-159">I den aktuella versionen finns det ingen loggnings support för fel status från *nx_dhcp_listen_for_messages.*</span><span class="sxs-lookup"><span data-stu-id="8d971-159">In the current release there is no logging support for error status returns from *nx_dhcp_listen_for_messages.*</span></span>

### <a name="option-55-parameter-request-list"></a><span data-ttu-id="8d971-160">Alternativ 55: lista över parameter begär Anden</span><span class="sxs-lookup"><span data-stu-id="8d971-160">Option 55: Parameter Request List</span></span>

<span data-ttu-id="8d971-161">DHCP-NetX måste konfigureras med en uppsättning alternativ som ska läsas in i listan med alternativ för parameter förfrågan (55) i erbjudandet och DHCPACK-meddelanden som skickas tillbaka till klienten.</span><span class="sxs-lookup"><span data-stu-id="8d971-161">The NetX DHCP Server must be configured with a set of options to load to Parameter Request Option (55) list in the OFFER and DHCPACK messages it transmits back to the Client.</span></span> <span data-ttu-id="8d971-162">De här alternativen bör inkludera nätverks kritiska konfigurations data för klient nätverket och definieras som standard som routerns IP-adress, nätmask och DNS-server.</span><span class="sxs-lookup"><span data-stu-id="8d971-162">These options should include network critical configuration data for the Client network and by default is defined to be router IP address, subnet mask, and DNS server.</span></span> <span data-ttu-id="8d971-163">Alternativ listan är en blankstegsavgränsad lista och definieras i den användare som kan konfigureras NX_DHCP_DEFAULT_SERVER_OPTION_LIST.</span><span class="sxs-lookup"><span data-stu-id="8d971-163">The option list is a space delimited list and defined in the user configurable NX_DHCP_DEFAULT_SERVER_OPTION_LIST.</span></span> <span data-ttu-id="8d971-164">Observera att antalet alternativ som anges i den här listan måste vara lika NX_DHCP_DEFAULT_OPTION_LIST_SIZE som också är användardefinierad.</span><span class="sxs-lookup"><span data-stu-id="8d971-164">Note the number of options specified in this list must equal NX_DHCP_DEFAULT_OPTION_LIST_SIZE which is also user defined.</span></span>

## <a name="constraints-of-the-netx-dhcp-server"></a><span data-ttu-id="8d971-165">Begränsningar för DHCP-servern NetX</span><span class="sxs-lookup"><span data-stu-id="8d971-165">Constraints of the NetX DHCP Server</span></span>

### <a name="dhcp-messages"></a><span data-ttu-id="8d971-166">DHCP-meddelanden</span><span class="sxs-lookup"><span data-stu-id="8d971-166">DHCP Messages</span></span>

<span data-ttu-id="8d971-167">NetX DHCP-servern verifierar inte att en IP-adress inte har tilldelats någon annan stans i nätverket innan IP-adressen beviljas till klienten.</span><span class="sxs-lookup"><span data-stu-id="8d971-167">The NetX DHCP Server does not verify that an IP address has not been assigned elsewhere on the network before granting the IP address to the Client.</span></span> <span data-ttu-id="8d971-168">Om det finns flera DHCP-servrar kan detta vara fallet.</span><span class="sxs-lookup"><span data-stu-id="8d971-168">If there are multiple DHCP servers, this can indeed be the case.</span></span> <span data-ttu-id="8d971-169">*Enligt RFC 2131 är det klientens ansvar att kontrol lera att IP-adressen är unik i nätverket* (t. ex. pinga adressen).</span><span class="sxs-lookup"><span data-stu-id="8d971-169">*As per RFC 2131, it is the Client's responsibility to verify the IP address is unique on its network* (e.g. pinging the address).</span></span> <span data-ttu-id="8d971-170">Om så inte är fallet bör servern ta emot ett neka-meddelande med IP-adressen för att uppdatera sin databas från klienten.</span><span class="sxs-lookup"><span data-stu-id="8d971-170">If it is not, the Server should receive a DECLINE message with the IP address to update its database from the Client.</span></span>

<span data-ttu-id="8d971-171">NetX-DHCP-servern utfärdar inte FORCE_RENEW meddelanden.</span><span class="sxs-lookup"><span data-stu-id="8d971-171">The NetX DHCP Server does not issue FORCE_RENEW messages.</span></span> <span data-ttu-id="8d971-172">Det är upp till DHCP-klienten som förnyar IP-adresslån.</span><span class="sxs-lookup"><span data-stu-id="8d971-172">It is up to the DHCP Client to renew its IP address lease.</span></span> <span data-ttu-id="8d971-173">DHCP-servern övervakar dock den återstående tiden på alla tilldelade IP-adresser i databasen.</span><span class="sxs-lookup"><span data-stu-id="8d971-173">However, the DHCP Server monitors the time remaining on all the assigned IP addresses in its database.</span></span> <span data-ttu-id="8d971-174">När ett IP-adresslån upphör att gälla returneras den IP-adressen till poolen med tillgängliga IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="8d971-174">When an IP address lease expires, that IP address is returned to the pool of available IP addresses.</span></span> <span data-ttu-id="8d971-175">Därför är det upp till klienten att aktivt förnya/ombinda sitt IP-adresslån.</span><span class="sxs-lookup"><span data-stu-id="8d971-175">Hence it is up to the Client to actively renew/rebind its IP address lease.</span></span>

<span data-ttu-id="8d971-176">Sessionsdata rensas så snart klienten beviljas ("bound") till ett IP-lån (eller en befintlig förnyas).</span><span class="sxs-lookup"><span data-stu-id="8d971-176">Session data is cleared as soon as the Client either is granted ("bound") to an IP lease (or an existing one is renewed).</span></span> <span data-ttu-id="8d971-177">Om ett klient paket bevisar falsk eller om klientens tids gräns mellan svaren rensas, rensas sessionens data.</span><span class="sxs-lookup"><span data-stu-id="8d971-177">If a Client packet proves bogus, or the Client times out between responses, session data is cleared.</span></span>

### <a name="saving-data-between-reboots"></a><span data-ttu-id="8d971-178">Spara data mellan omstarter</span><span class="sxs-lookup"><span data-stu-id="8d971-178">Saving Data Between Reboots</span></span>

<span data-ttu-id="8d971-179">NetX DHCP-servern sparar klient data inklusive parametrar för DHCP-begäran i en klient post tabell.</span><span class="sxs-lookup"><span data-stu-id="8d971-179">The NetX DHCP Server saves Client data including DHCP request parameters in a Client record table.</span></span> <span data-ttu-id="8d971-180">Den här tabellen lagras inte i icke-flyktigt minne, så om DHCP-serverns värd måste starta om den informationen inte sparas mellan omstarter.</span><span class="sxs-lookup"><span data-stu-id="8d971-180">This table is not stored in non volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

<span data-ttu-id="8d971-181">NetX DHCP-servern sparar data för IP-adresslån i en IP-adress tabell.</span><span class="sxs-lookup"><span data-stu-id="8d971-181">The NetX DHCP Server saves IP address lease data in a IP address table.</span></span> <span data-ttu-id="8d971-182">Den här tabellen lagras inte i icke-flyktigt minne, så om DHCP-serverns värd måste starta om den informationen inte sparas mellan omstarter.</span><span class="sxs-lookup"><span data-stu-id="8d971-182">This table is not stored in non volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

### <a name="relay-agents"></a><span data-ttu-id="8d971-183">Relä agenter</span><span class="sxs-lookup"><span data-stu-id="8d971-183">Relay Agents</span></span>

<span data-ttu-id="8d971-184">NetX DHCP-servern har kon figurer ATS med noll IP-adress för fältet "Relay Agent" eftersom den inte har stöd för out of Network DHCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d971-184">The NetX DHCP Server is configured with a zero IP address for the 'Relay agent' field because it does not support out of network DHCP requests.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="8d971-185">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="8d971-185">Small Example System</span></span>

<span data-ttu-id="8d971-186">Ett exempel på hur enkelt det är att använda NetX DHCP-servern beskrivs i bild 1,1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="8d971-186">An example of how easy it is to use the NetX DHCP Server is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="8d971-187">I det här exemplet tas DHCP-filen *nx_dhcp_server. h* in på rad 5.</span><span class="sxs-lookup"><span data-stu-id="8d971-187">In this example, the DHCP include file *nx_dhcp_server.h* is brought in at line 5.</span></span> <span data-ttu-id="8d971-188">Stack storlek för DHCP-serverns tråd, stack storlek och test tråds stack storlek anges i rad 7-13.</span><span class="sxs-lookup"><span data-stu-id="8d971-188">DHCP Server thread stack size, IP thread stack size and test thread stack size are all defined in lines 7-13.</span></span>

<span data-ttu-id="8d971-189">Först skapar du en valfri test tråds aktivitet för att stoppa, starta om och slutligen ta bort DHCP-servern med funktionen "*test_thread_entry*" på rad 57.</span><span class="sxs-lookup"><span data-stu-id="8d971-189">First, an optional test thread task for stopping, restarting and eventually deleting the DHCP server is created with the "*test_thread_entry*" function at line 57.</span></span> <span data-ttu-id="8d971-190">Ett kontroll block för DHCP-server (*dhcp_server*) definieras som en global variabel på rad 20.</span><span class="sxs-lookup"><span data-stu-id="8d971-190">A DHCP Server control block "*dhcp_server*" is defined as a global variable at line 20.</span></span> <span data-ttu-id="8d971-191">Observera att serverpoolen för servern skapas med paket som har en nytto last på minst lika stor som standard-DHCP-meddelandet (548 byte plus IP-och UDP-huvudets byte).</span><span class="sxs-lookup"><span data-stu-id="8d971-191">Note that the server packet pool is created with packets having a payload at least as large as the standard DHCP message (548 bytes plus IP and UDP header bytes).</span></span> <span data-ttu-id="8d971-192">När du har skapat en IP-instans för DHCP-servern skapar programmet DHCP-servern på rad 96.</span><span class="sxs-lookup"><span data-stu-id="8d971-192">After successfully creating an IP instance for the DHCP Server, the application creates the DHCP Server in line 96.</span></span> <span data-ttu-id="8d971-193">Därefter gör programmet det möjligt för Server-IP-instansen att vara UDP aktiverat.</span><span class="sxs-lookup"><span data-stu-id="8d971-193">Next, the application enables the Server IP instance to be UDP enabled.</span></span> <span data-ttu-id="8d971-194">Innan du startar DHCP-servern skapas listan över tillgängliga IP-adresser på rad 137 med hjälp av tjänsten *nx_dhcp_create_server_ip_address_list* .</span><span class="sxs-lookup"><span data-stu-id="8d971-194">Before starting the DHCP Server, the available IP address list is created in line 137 using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="8d971-195">Parametrarna för nätverks konfiguration anges på följande rad 138 med hjälp av tjänsten *nx_dhcp_set_interface_network_parameters* , blir DHCP-Server tjänsterna tillgängliga när programmet anropar *nx_dhcp_server_start* på rad 141.</span><span class="sxs-lookup"><span data-stu-id="8d971-195">The network configuration parameters are set in the following line 138 using the *nx_dhcp_set_interface_network_parameters* service, DHCP Server services become available when the application calls the *nx_dhcp_server_start* at line 141.</span></span> <span data-ttu-id="8d971-196">Uppgiften test tråd visar hur du stoppar och startar om DHCP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d971-196">The test thread task demonstrates the use of stopping and restarting the DHCP server.</span></span>

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);

    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}
```

<span data-ttu-id="8d971-197">Figur 1,1 exempel NetX DHCP Server Application</span><span class="sxs-lookup"><span data-stu-id="8d971-197">Figure 1.1 Example NetX DHCP Server application</span></span>

## <a name="configuration-options"></a><span data-ttu-id="8d971-198">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="8d971-198">Configuration Options</span></span>

<span data-ttu-id="8d971-199">Det finns flera konfigurations alternativ för att skapa NetX DHCP-server.</span><span class="sxs-lookup"><span data-stu-id="8d971-199">There are several configuration options for building NetX DHCP Server.</span></span> <span data-ttu-id="8d971-200">I följande lista beskrivs var och en i detalj:</span><span class="sxs-lookup"><span data-stu-id="8d971-200">The following list describes each in detail:</span></span>  
  
- <span data-ttu-id="8d971-201">**NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort grundläggande fel sökning i DHCP.</span><span class="sxs-lookup"><span data-stu-id="8d971-201">**NX_DISABLE_ERROR_CHECKING**: This option removes the basic DHCP error checking.</span></span> <span data-ttu-id="8d971-202">Den används vanligt vis efter fel sökning av programmet.</span><span class="sxs-lookup"><span data-stu-id="8d971-202">It is typically used after the application is debugged.</span></span>  
- <span data-ttu-id="8d971-203">**NX_DHCP_SERVER_THREAD_PRIORITY**: det här alternativet anger prioriteten för DHCP-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="8d971-203">**NX_DHCP_SERVER_THREAD_PRIORITY**: This option specifies the priority of the DHCP Server thread.</span></span> <span data-ttu-id="8d971-204">Som standard anger det här värdet att DHCP-tråden körs vid prioritet 2.</span><span class="sxs-lookup"><span data-stu-id="8d971-204">By default, this value specifies that the DHCP thread runs at priority 2.</span></span>
- <span data-ttu-id="8d971-205">**NX_DHCP_TYPE_OF_SERVICE**: det här alternativet anger vilken typ av tjänst som krävs för DHCP UDP-begärandena.</span><span class="sxs-lookup"><span data-stu-id="8d971-205">**NX_DHCP_TYPE_OF_SERVICE**: This option specifies the type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="8d971-206">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="8d971-206">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="8d971-207">**NX_DHCP_FRAGMENT_OPTION**: fragment aktivera för DHCP UDP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d971-207">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="8d971-208">Som standard är det här värdet inställt på NX_DONT_FRAGMENT för att inaktivera UDP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="8d971-208">By default, this value is set to NX_DONT_FRAGMENT to disable UDP fragmenting.</span></span>
- <span data-ttu-id="8d971-209">**NX_DHCP_TIME_TO_LIVE**: anger antalet routrar som paketet kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="8d971-209">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers the packet can pass before it is discarded.</span></span> <span data-ttu-id="8d971-210">Standardvärdet är 0x80.</span><span class="sxs-lookup"><span data-stu-id="8d971-210">The default value is 0x80.</span></span>
- <span data-ttu-id="8d971-211">**NX_DHCP_QUEUE_DEPTH** Anger antalet paket som DHCP-serverns socket behåller innan kön töms.</span><span class="sxs-lookup"><span data-stu-id="8d971-211">**NX_DHCP_QUEUE_DEPTH** Specifies the number of packets that the DHCP Server socket keeps before flushing the queue.</span></span> <span data-ttu-id="8d971-212">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="8d971-212">The default value is 5.</span></span>
- <span data-ttu-id="8d971-213">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: anger tids gränsen i timer-Tick för att netx DHCP-servern ska vänta på att allokera ett paket från paketets adresspool.</span><span class="sxs-lookup"><span data-stu-id="8d971-213">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: Specifies the timeout in timer ticks for the NetX DHCP Server to wait for allocate a packet from its packet pool.</span></span> <span data-ttu-id="8d971-214">Standardvärdet är inställt på NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="8d971-214">The default value is set to NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="8d971-215">**NX_DHCP_SUBNET_MASK**: det här är nät masken som DHCP-klienten ska konfigureras med.</span><span class="sxs-lookup"><span data-stu-id="8d971-215">**NX_DHCP_SUBNET_MASK**: This is the subnet mask the DHCP Client should be configured with.</span></span> <span data-ttu-id="8d971-216">Standardvärdet är inställt på 0xFFFFFF00.</span><span class="sxs-lookup"><span data-stu-id="8d971-216">The default value is set to 0xFFFFFF00.</span></span>
- <span data-ttu-id="8d971-217">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: Detta är tids gräns i timer-Tick för DHCP-serverns snabba timer för att kontrol lera tiden som återstår och hantera sessioner som har nått tids gränsen.</span><span class="sxs-lookup"><span data-stu-id="8d971-217">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server fast timer to check on session time remaining and handle sessions that have timed out.</span></span>
- <span data-ttu-id="8d971-218">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: Detta är tids gräns i timer-Tick för DHCP-serverns långsamma timer för att kontrol lera om IP-adressen är kvar och hantera lån som har uppnådde sin tids gräns.</span><span class="sxs-lookup"><span data-stu-id="8d971-218">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server slow timer to check on IP address lease time remaining and handle lease that have timed out.</span></span>
- <span data-ttu-id="8d971-219">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: Detta är tids gräns i timer-Tick som DHCP-servern väntar på att ta emot nästa DHCP-klient meddelande.</span><span class="sxs-lookup"><span data-stu-id="8d971-219">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: This is timeout period in timer ticks the DHCP Server will wait to receive the next DHCP Client message.</span></span>
- <span data-ttu-id="8d971-220">**NX_DHCP_DEFAULT_LEASE_TIME**: det här är IP-adressens låne tid i sekunder som tilldelats DHCP-klienten, och basen för att beräkna och återbinda tider som också har tilldelats till klienten.</span><span class="sxs-lookup"><span data-stu-id="8d971-220">**NX_DHCP_DEFAULT_LEASE_TIME**: This is IP Address lease time in seconds assigned to the DHCP Client, and the basis for computing the renewal and rebind times also assigned to the Client.</span></span> <span data-ttu-id="8d971-221">Standardvärdet är inställt på 0xFFFFFFFF (oändlighet).</span><span class="sxs-lookup"><span data-stu-id="8d971-221">The default value is set to 0xFFFFFFFF (infinity).</span></span>
- <span data-ttu-id="8d971-222">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: Detta är storleken på DHCP-serverns matris för att tillhandahålla tillgängliga IP-adresser för tilldelning till klienten.</span><span class="sxs-lookup"><span data-stu-id="8d971-222">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: This is size of the DHCP Server array for holding available IP addresses for assigning to the Client.</span></span> <span data-ttu-id="8d971-223">Standardvärdet är 20.</span><span class="sxs-lookup"><span data-stu-id="8d971-223">The default value is 20.</span></span>
- <span data-ttu-id="8d971-224">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: Detta är storleken på DHCP-serverns matris för att lagra klient poster.</span><span class="sxs-lookup"><span data-stu-id="8d971-224">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: This is size of the DHCP Server array for holding Client records.</span></span> <span data-ttu-id="8d971-225">Standardvärdet är 50.</span><span class="sxs-lookup"><span data-stu-id="8d971-225">The default value is 50.</span></span>
- <span data-ttu-id="8d971-226">**NX_DHCP_CLIENT_OPTIONS_MAX**: Detta är storleken på matrisen i DHCP-klientens instans för att hålla alla begärda alternativ i listan parameter förfrågan i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8d971-226">**NX_DHCP_CLIENT_OPTIONS_MAX**: This is size of the array in the DHCP Client instance for holding the all the requested options in the parameter request list in the current session.</span></span> <span data-ttu-id="8d971-227">Standardvärdet är 12.</span><span class="sxs-lookup"><span data-stu-id="8d971-227">The default value is 12.</span></span>
- <span data-ttu-id="8d971-228">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: det här är den buffert som innehåller DHCP-serverns standard lista med alternativ för att tillhandahålla den aktuella DHCP-klienten i listan med parameter begär Anden.</span><span class="sxs-lookup"><span data-stu-id="8d971-228">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: This is the buffer holding the DHCP Server's default list of options to supply to the current DHCP Client in the parameter request list.</span></span> <span data-ttu-id="8d971-229">Standardvärdet är "1 3 6".</span><span class="sxs-lookup"><span data-stu-id="8d971-229">The default is "1 3 6."</span></span>
- <span data-ttu-id="8d971-230">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: Detta är storleken på matrisen som innehåller DHCP-serverns standard lista med alternativ.</span><span class="sxs-lookup"><span data-stu-id="8d971-230">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: This is the size of the array to hold the DHCP Server's default list of options.</span></span> <span data-ttu-id="8d971-231">Standardvärdet är 3.</span><span class="sxs-lookup"><span data-stu-id="8d971-231">The default value is 3.</span></span>
- <span data-ttu-id="8d971-232">**NX_DHCP_SERVER_HOSTNAME_MAX**: storleken på bufferten för att placera serverns värdnamn.</span><span class="sxs-lookup"><span data-stu-id="8d971-232">**NX_DHCP_SERVER_HOSTNAME_MAX**: This is size of the buffer for holding the Server host name.</span></span> <span data-ttu-id="8d971-233">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="8d971-233">The default value is 32.</span></span>
- <span data-ttu-id="8d971-234">**NX_DHCP_CLIENT_HOSTNAME_MAX**: storleken på bufferten för att placera klientens värdnamn i den aktuella DHCP-serverns klientsession.</span><span class="sxs-lookup"><span data-stu-id="8d971-234">**NX_DHCP_CLIENT_HOSTNAME_MAX**: This is size of the buffer for holding the Client host name in the current DHCP Server Client session.</span></span> <span data-ttu-id="8d971-235">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="8d971-235">The default value is 32.</span></span>
