---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Telnet-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo Telnet-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825713"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a><span data-ttu-id="044f0-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo Telnet-tjänster</span><span class="sxs-lookup"><span data-stu-id="044f0-103">Chapter 3 - Description of Azure RTOS NetX Duo Telnet services</span></span>

<span data-ttu-id="044f0-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo Telnet-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="044f0-104">This chapter contains a description of all Azure RTOS NetX Duo Telnet Services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="044f0-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="044f0-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="044f0-106">**nx_telnet_client_connect**: *Anslut en Telnet-klient med IPv4-adress*</span><span class="sxs-lookup"><span data-stu-id="044f0-106">**nx_telnet_client_connect**: *Connect a Telnet Client with IPv4 address*</span></span>
- <span data-ttu-id="044f0-107">**nxd_telnet_client_connect**: *Anslut en IPv6 Telnet-klient med IPv6-adress*</span><span class="sxs-lookup"><span data-stu-id="044f0-107">**nxd_telnet_client_connect**: *Connect an IPv6 Telnet Client with IPv6 address*</span></span>
- <span data-ttu-id="044f0-108">**nx_telnet_client_create**: *skapa en Telnet-klient*</span><span class="sxs-lookup"><span data-stu-id="044f0-108">**nx_telnet_client_create**: *Create a Telnet Client*</span></span>
- <span data-ttu-id="044f0-109">**nx_telnet_client_delete**: *ta bort en Telnet-klient*</span><span class="sxs-lookup"><span data-stu-id="044f0-109">**nx_telnet_client_delete**: *Delete a Telnet Client*</span></span>
- <span data-ttu-id="044f0-110">**nx_telnet_client_disconnect**: *Koppla från en Telnet-klient*</span><span class="sxs-lookup"><span data-stu-id="044f0-110">**nx_telnet_client_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="044f0-111">**nx_telnet_client_packet_receive**: *ta emot paket via Telnet-klienten*</span><span class="sxs-lookup"><span data-stu-id="044f0-111">**nx_telnet_client_packet_receive**: *Receive packet via Telnet Client*</span></span>
- <span data-ttu-id="044f0-112">**nx_telnet_client_packet_send**: *skicka paket via Telnet-klienten*</span><span class="sxs-lookup"><span data-stu-id="044f0-112">**nx_telnet_client_packet_send**: *Send packet via Telnet Client*</span></span>
- <span data-ttu-id="044f0-113">**nx_telnet_server_create**: *skapa en Telnet-Server*</span><span class="sxs-lookup"><span data-stu-id="044f0-113">**nx_telnet_server_create**: *Create a Telnet Server*</span></span>
- <span data-ttu-id="044f0-114">**nx_telnet_server_delete**: *ta bort en Telnet-Server*</span><span class="sxs-lookup"><span data-stu-id="044f0-114">**nx_telnet_server_delete**: *Delete a Telnet Server*</span></span>
- <span data-ttu-id="044f0-115">**nx_telnet_server_disconnect**: *Koppla från en Telnet-klient*</span><span class="sxs-lookup"><span data-stu-id="044f0-115">**nx_telnet_server_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="044f0-116">**nx_telnet_server_get_open_connection_count**: *Hämta antalet öppna anslutningar*</span><span class="sxs-lookup"><span data-stu-id="044f0-116">**nx_telnet_server_get_open_connection_count**: *Retrieve the number of open connections*</span></span>
- <span data-ttu-id="044f0-117">**nx_telnet_server_packet_send**: *skicka paket via klient anslutning*</span><span class="sxs-lookup"><span data-stu-id="044f0-117">**nx_telnet_server_packet_send**: *Send packet through Client connection*</span></span>
- <span data-ttu-id="044f0-118">**nx_telnet_server_packet_pool_set**: *Ange paket bassäng som programpool för Telnet-Server*</span><span class="sxs-lookup"><span data-stu-id="044f0-118">**nx_telnet_server_packet_pool_set**: *Set packet pool as Telnet Server packet pool*</span></span>
- <span data-ttu-id="044f0-119">**nx_telnet_server_start**: *starta en Telnet-Server*</span><span class="sxs-lookup"><span data-stu-id="044f0-119">**nx_telnet_server_start**: *Start a Telnet Server*</span></span>
- <span data-ttu-id="044f0-120">**nx_telnet_server_stop**: *stoppa en Telnet-Server*</span><span class="sxs-lookup"><span data-stu-id="044f0-120">**nx_telnet_server_stop**: *Stop a Telnet Server*</span></span>

## <a name="nx_telnet_client_connect"></a><span data-ttu-id="044f0-121">nx_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="044f0-121">nx_telnet_client_connect</span></span>

<span data-ttu-id="044f0-122">Ansluta en Telnet-klient med IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="044f0-122">Connect a Telnet Client with IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-123">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-123">Prototype</span></span>

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="044f0-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-124">Description</span></span>

<span data-ttu-id="044f0-125">Den här tjänsten försöker ansluta den tidigare skapade Telnet-klientprogrammet till servern på den angivna IP-adressen och porten med hjälp av en IPv4-adress för Telnet-servern.</span><span class="sxs-lookup"><span data-stu-id="044f0-125">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using an IPv4 address for the Telnet Server.</span></span> <span data-ttu-id="044f0-126">Den här tjänsten infogar faktiskt ULONG-serverns IP-adress i ett NXD_ADDRESS Control-Block och ställer in IP-versionen på 4 innan du anropar den *nxd_telnet_client_connect* tjänst som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="044f0-126">This service actually inserts the ULONG server IP address in an NXD_ADDRESS control block and sets the IP version to 4 before calling the *nxd_telnet_client_connect* service described below.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-127">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-127">Input Parameters</span></span>

- <span data-ttu-id="044f0-128">**client_ptr**: pekar på kontroll block för Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-128">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="044f0-129">**server_ip**: Telnet-serverns IPv4-adress.</span><span class="sxs-lookup"><span data-stu-id="044f0-129">**server_ip**: IPv4 Address of the Telnet Server.</span></span>
- <span data-ttu-id="044f0-130">**SERVER_PORT**: TCP-porten för Server (Telnet Server är port 23).</span><span class="sxs-lookup"><span data-stu-id="044f0-130">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="044f0-131">**wait_option**: anger hur länge tjänsten ska vänta på anslutning till Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-131">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="044f0-132">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="044f0-132">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="044f0-133">**timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="044f0-133">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="044f0-134">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="044f0-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-135">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-135">Return Values</span></span>

- <span data-ttu-id="044f0-136">**NX_SUCCESS**: (0X00) lyckad klient anslutning.</span><span class="sxs-lookup"><span data-stu-id="044f0-136">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="044f0-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4)-klienten är redan ansluten.</span><span class="sxs-lookup"><span data-stu-id="044f0-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="044f0-138">NX_PTR_ERROR: (0x07) ogiltig klient pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-138">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="044f0-139">NX_IP_ADDRESS_ERROR: (0x21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="044f0-139">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="044f0-140">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="044f0-140">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-141">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-141">Allowed From</span></span>

<span data-ttu-id="044f0-142">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-142">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-143">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-143">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a><span data-ttu-id="044f0-144">nxd_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="044f0-144">nxd_telnet_client_connect</span></span>

<span data-ttu-id="044f0-145">Ansluta en Telnet-klient med IPv6-eller IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="044f0-145">Connect a Telnet Client with IPv6 or IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-146">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-146">Prototype</span></span>

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="044f0-147">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-147">Description</span></span>

<span data-ttu-id="044f0-148">Den här tjänsten försöker ansluta den tidigare skapade Telnet-klientprogrammet till servern på den angivna IP-adressen och porten med hjälp av Telnet-serverns IPv6-adress.</span><span class="sxs-lookup"><span data-stu-id="044f0-148">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using the Telnet Server’s IPv6 address.</span></span> <span data-ttu-id="044f0-149">Den här tjänsten kan ta en IPv4-eller IPv6-adress men måste finnas i NXD_ADDRESS variabel *server_ip_address.*</span><span class="sxs-lookup"><span data-stu-id="044f0-149">This service can take an IPv4 or an IPv6 address but must be contained in the NXD_ADDRESS variable *server_ip_address.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-150">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-150">Input Parameters</span></span>

- <span data-ttu-id="044f0-151">**client_ptr**: pekar på kontroll block för Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-151">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="044f0-152">**server_ip_address**: serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="044f0-152">**server_ip_address**: IP Address of Server.</span></span>
- <span data-ttu-id="044f0-153">**SERVER_PORT**: TCP-porten för Server (Telnet Server är port 23).</span><span class="sxs-lookup"><span data-stu-id="044f0-153">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="044f0-154">**wait_option**: anger hur länge tjänsten ska vänta på anslutning till Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-154">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="044f0-155">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="044f0-155">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="044f0-156">**timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="044f0-156">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="044f0-157">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="044f0-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-158">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-158">Return Values</span></span>

- <span data-ttu-id="044f0-159">**NX_SUCCESS**: (0X00) lyckad klient anslutning.</span><span class="sxs-lookup"><span data-stu-id="044f0-159">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="044f0-160">**NX_TELNET_ERROR**: (0XF0) klient anslutnings fel.</span><span class="sxs-lookup"><span data-stu-id="044f0-160">**NX_TELNET_ERROR**: (0xF0) Client connect error.</span></span>
- <span data-ttu-id="044f0-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4)-klienten är redan ansluten.</span><span class="sxs-lookup"><span data-stu-id="044f0-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="044f0-162">NX_PTR_ERROR: (0x07) ogiltig klient pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-162">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="044f0-163">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="044f0-163">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="044f0-164">NX_TELNET_INVALID_PARAMETER: (0xF5) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="044f0-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-165">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-165">Allowed From</span></span>

<span data-ttu-id="044f0-166">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-166">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-167">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-167">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a><span data-ttu-id="044f0-168">nx_telnet_client_create</span><span class="sxs-lookup"><span data-stu-id="044f0-168">nx_telnet_client_create</span></span>

<span data-ttu-id="044f0-169">Skapa en Telnet-klient</span><span class="sxs-lookup"><span data-stu-id="044f0-169">Create a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-170">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-170">Prototype</span></span>

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="044f0-171">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-171">Description</span></span>

<span data-ttu-id="044f0-172">Den här tjänsten skapar en Telnet-klient instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-172">This service creates a Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-173">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-173">Input Parameters</span></span>

- <span data-ttu-id="044f0-174">**client_ptr**: pekar på kontroll block för Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-174">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="044f0-175">**client_name**: namnet på klient instansen.</span><span class="sxs-lookup"><span data-stu-id="044f0-175">**client_name**: Name of Client instance.</span></span>
- <span data-ttu-id="044f0-176">**ip_ptr**: pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-176">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="044f0-177">**window_size**: storleken på TCP Receive-fönstret för den här klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-177">**window_size**: Size of TCP receive window for this Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-178">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-178">Return Values</span></span>

- <span data-ttu-id="044f0-179">**NX_SUCCESS**: (0X00) lyckad klient skapande.</span><span class="sxs-lookup"><span data-stu-id="044f0-179">**NX_SUCCESS**: (0x00) Successful Client create.</span></span>
- <span data-ttu-id="044f0-180">**NX_TELNET_ERROR**: (0XF0) socket-skapande fel.</span><span class="sxs-lookup"><span data-stu-id="044f0-180">**NX_TELNET_ERROR**: (0xF0) Socket create error.</span></span>
- <span data-ttu-id="044f0-181">NX_PTR_ERROR: (0x07) ogiltig klient eller IP-pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-181">NX_PTR_ERROR: (0x07) Invalid Client or IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-182">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-182">Allowed From</span></span>

<span data-ttu-id="044f0-183">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="044f0-183">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-184">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-184">Example</span></span>

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a><span data-ttu-id="044f0-185">nx_telnet_client_delete</span><span class="sxs-lookup"><span data-stu-id="044f0-185">nx_telnet_client_delete</span></span>

<span data-ttu-id="044f0-186">Ta bort en Telnet-klient</span><span class="sxs-lookup"><span data-stu-id="044f0-186">Delete a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-187">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-187">Prototype</span></span>

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="044f0-188">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-188">Description</span></span>

<span data-ttu-id="044f0-189">Den här tjänsten tar bort en tidigare skapad Telnet-klient instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-189">This service deletes a previously created Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-190">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-190">Input Parameters</span></span>

- <span data-ttu-id="044f0-191">**client_ptr**: pekar på kontroll block för Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-191">**client_ptr**: Pointer to Telnet Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-192">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-192">Return Values</span></span>

- <span data-ttu-id="044f0-193">**NX_SUCCESS**: (0X00) lyckad klient borttagning.</span><span class="sxs-lookup"><span data-stu-id="044f0-193">**NX_SUCCESS**: (0x00) Successful Client delete.</span></span>
- <span data-ttu-id="044f0-194">**NX_TELNET_NOT_DISCONNECTED**: (0XF4) klienten är fortfarande ansluten.</span><span class="sxs-lookup"><span data-stu-id="044f0-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client still connected.</span></span>
- <span data-ttu-id="044f0-195">NX_PTR_ERROR: (0x07) ogiltig klient pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-195">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="044f0-196">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="044f0-196">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-197">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-197">Allowed From</span></span>

<span data-ttu-id="044f0-198">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-199">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-199">Example</span></span>

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a><span data-ttu-id="044f0-200">nx_telnet_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="044f0-200">nx_telnet_client_disconnect</span></span>

<span data-ttu-id="044f0-201">Koppla från en Telnet-klient</span><span class="sxs-lookup"><span data-stu-id="044f0-201">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-202">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-202">Prototype</span></span>

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="044f0-203">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-203">Description</span></span>

<span data-ttu-id="044f0-204">Den här tjänsten kopplar från en tidigare ansluten Telnet-klient instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-204">This service disconnects a previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-205">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-205">Input Parameters</span></span>

- <span data-ttu-id="044f0-206">**client_ptr**: pekar på kontroll block för Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-206">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="044f0-207">**wait_option**: anger hur länge tjänsten ska vänta tills Telnet-klienten kopplas från.</span><span class="sxs-lookup"><span data-stu-id="044f0-207">**wait_option**: Defines how long the service will wait for the Telnet Client disconnect.</span></span> <span data-ttu-id="044f0-208">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="044f0-208">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="044f0-209">**timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="044f0-209">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="044f0-210">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="044f0-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-211">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-211">Return Values</span></span>

- <span data-ttu-id="044f0-212">**NX_SUCCESS**: (0X00) lyckad klient från koppling.</span><span class="sxs-lookup"><span data-stu-id="044f0-212">**NX_SUCCESS**: (0x00) Successful Client disconnect.</span></span>
- <span data-ttu-id="044f0-213">**NX_TELNET_NOT_CONNECTED**: (0XF3) klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="044f0-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) Client not connected.</span></span>
- <span data-ttu-id="044f0-214">NX_PTR_ERROR: (0x07) ogiltig klient pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-214">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="044f0-215">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="044f0-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="044f0-216">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-216">Allowed From</span></span>

<span data-ttu-id="044f0-217">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-218">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-218">Example</span></span>

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a><span data-ttu-id="044f0-219">nx_telnet_client_packet_receive</span><span class="sxs-lookup"><span data-stu-id="044f0-219">nx_telnet_client_packet_receive</span></span>

<span data-ttu-id="044f0-220">Ta emot paket via Telnet Client</span><span class="sxs-lookup"><span data-stu-id="044f0-220">Receive packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-221">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-221">Prototype</span></span>

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="044f0-222">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-222">Description</span></span>

<span data-ttu-id="044f0-223">Den här tjänsten tar emot ett paket från den tidigare anslutna Telnet Client-instansen.</span><span class="sxs-lookup"><span data-stu-id="044f0-223">This service receives a packet from the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-224">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-224">Input Parameters</span></span>

- <span data-ttu-id="044f0-225">**client_ptr**: pekar på kontroll block för Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-225">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="044f0-226">**packet_ptr**: pekar mot målet för det mottagna paketet.</span><span class="sxs-lookup"><span data-stu-id="044f0-226">**packet_ptr**: Pointer to the destination for the received packet.</span></span>
- <span data-ttu-id="044f0-227">**wait_option**: anger hur länge tjänsten ska vänta på att det tar emot Telnet-klientcertifikatet.</span><span class="sxs-lookup"><span data-stu-id="044f0-227">**wait_option**: Defines how long the service will wait for the Telnet Client packet receive.</span></span> <span data-ttu-id="044f0-228">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="044f0-228">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="044f0-229">**timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="044f0-229">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="044f0-230">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="044f0-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-231">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-231">Return Values</span></span>

- <span data-ttu-id="044f0-232">**NX_SUCCESS**: (0X00) lyckad klient paket mottagning.</span><span class="sxs-lookup"><span data-stu-id="044f0-232">**NX_SUCCESS**: (0x00) Successful Client packet receive.</span></span>
- <span data-ttu-id="044f0-233">NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="044f0-233">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="044f0-234">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="044f0-234">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-235">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-235">Allowed From</span></span>

<span data-ttu-id="044f0-236">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-236">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-237">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-237">Example</span></span>

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a><span data-ttu-id="044f0-238">nx_telnet_client_packet_send</span><span class="sxs-lookup"><span data-stu-id="044f0-238">nx_telnet_client_packet_send</span></span>

<span data-ttu-id="044f0-239">Skicka paket via Telnet Client</span><span class="sxs-lookup"><span data-stu-id="044f0-239">Send packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-240">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-240">Prototype</span></span>

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="044f0-241">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-241">Description</span></span>

<span data-ttu-id="044f0-242">Den här tjänsten skickar ett paket genom den tidigare anslutna Telnet-klientprogrammet.</span><span class="sxs-lookup"><span data-stu-id="044f0-242">This service sends a packet through the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-243">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-243">Input Parameters</span></span>

- <span data-ttu-id="044f0-244">**client_ptr**: pekar på kontroll block för Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-244">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="044f0-245">**packet_ptr**: pekar på det paket som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="044f0-245">**packet_ptr**: Pointer to the packet to send.</span></span>
- <span data-ttu-id="044f0-246">**wait_option**: anger hur länge tjänsten ska vänta på att skicka Telnet-klienten.</span><span class="sxs-lookup"><span data-stu-id="044f0-246">**wait_option**: Defines how long the service will wait for the Telnet Client packet send.</span></span> <span data-ttu-id="044f0-247">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="044f0-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="044f0-248">**timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="044f0-248">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="044f0-249">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="044f0-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-250">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-250">Return Values</span></span>

- <span data-ttu-id="044f0-251">**NX_SUCCESS**: (0X00) lyckades skicka klient paket.</span><span class="sxs-lookup"><span data-stu-id="044f0-251">**NX_SUCCESS**: (0x00) Successful Client packet send.</span></span>
- <span data-ttu-id="044f0-252">**NX_TELNET_ERROR**: (0xF0) Det gick inte att skicka paket – anroparen ansvarar för att släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="044f0-252">**NX_TELNET_ERROR**: (0xF0) Send packet failed – caller is responsible for releasing the packet.</span></span>
- <span data-ttu-id="044f0-253">NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="044f0-253">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="044f0-254">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="044f0-254">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-255">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-255">Allowed From</span></span>

<span data-ttu-id="044f0-256">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-256">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-257">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-257">Example</span></span>

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a><span data-ttu-id="044f0-258">nx_telnet_server_create</span><span class="sxs-lookup"><span data-stu-id="044f0-258">nx_telnet_server_create</span></span>

<span data-ttu-id="044f0-259">Skapa en Telnet-Server</span><span class="sxs-lookup"><span data-stu-id="044f0-259">Create a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-260">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-260">Prototype</span></span>

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a><span data-ttu-id="044f0-261">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-261">Description</span></span>

<span data-ttu-id="044f0-262">Den här tjänsten skapar en Telnet Server-instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="044f0-262">This service creates a Telnet Server instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-263">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-263">Input Parameters</span></span>

- <span data-ttu-id="044f0-264">**server_ptr**: pekar mot kontroll block för Telnet-Server.</span><span class="sxs-lookup"><span data-stu-id="044f0-264">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="044f0-265">**server_name**: namnet på Telnet Server-instansen.</span><span class="sxs-lookup"><span data-stu-id="044f0-265">**server_name**: Name of Telnet Server instance.</span></span>
- <span data-ttu-id="044f0-266">**ip_ptr**: pekar mot associerad IP-instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-266">**ip_ptr**: Pointer to associated IP instance.</span></span>
- <span data-ttu-id="044f0-267">**stack_ptr**: pekare till stack för den interna Server tråden.</span><span class="sxs-lookup"><span data-stu-id="044f0-267">**stack_ptr**: Pointer to stack for the internal Server thread.</span></span>
- <span data-ttu-id="044f0-268">**sack_size**: stackens storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="044f0-268">**sack_size**: Size of the stack, in bytes.</span></span>
- <span data-ttu-id="044f0-269">**new_connection**: funktions pekare för motringning av program.</span><span class="sxs-lookup"><span data-stu-id="044f0-269">**new_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="044f0-270">Den här rutinen anropas när en ny anslutnings förfrågan för Telnet-klienten identifieras av servern.</span><span class="sxs-lookup"><span data-stu-id="044f0-270">This routine is called whenever a new Telnet Client connection request is detected by the Server.</span></span>
- <span data-ttu-id="044f0-271">**receive_data**: funktions pekare för motringning av program.</span><span class="sxs-lookup"><span data-stu-id="044f0-271">**receive_data**: Application callback routine function pointer.</span></span> <span data-ttu-id="044f0-272">Den här rutinen anropas när det finns nya Telnet-klientinställningar på anslutningen.</span><span class="sxs-lookup"><span data-stu-id="044f0-272">This routine is called whenever a new Telnet Client data is present on the connection.</span></span> <span data-ttu-id="044f0-273">Den här rutinen ansvarar för att släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="044f0-273">This routine is responsible for releasing the packet.</span></span>
- <span data-ttu-id="044f0-274">**end_connection**: funktions pekare för motringning av program.</span><span class="sxs-lookup"><span data-stu-id="044f0-274">**end_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="044f0-275">Den här rutinen anropas när en anslutning för Telnet-klienten kopplas från av klienten eller om klient anslutnings tiden upphör ("aktivitetens timeout upphör att gälla).</span><span class="sxs-lookup"><span data-stu-id="044f0-275">This routine is called whenever a Telnet Client connection is disconnected by the Client or the Client connection times out (“activity timeout” expires).</span></span> <span data-ttu-id="044f0-276">Servern kan också koppla från tjänsten *nx_telnet_server_disconnect* som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="044f0-276">The Server can also disconnect via the *nx_telnet_server_disconnect* service described below.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-277">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-277">Return Values</span></span>

- <span data-ttu-id="044f0-278">**NX_SUCCESS**: (0X00) lyckad Server skapande.</span><span class="sxs-lookup"><span data-stu-id="044f0-278">**NX_SUCCESS**: (0x00) Successful Server create.</span></span>
- <span data-ttu-id="044f0-279">NX_PTR_ERROR: (0x07) ogiltig pekare för Server, IP, stack eller program.</span><span class="sxs-lookup"><span data-stu-id="044f0-279">NX_PTR_ERROR: (0x07) Invalid Server, IP, stack, or application callback pointers.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-280">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-280">Allowed From</span></span>

<span data-ttu-id="044f0-281">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="044f0-281">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-282">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-282">Example</span></span>

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a><span data-ttu-id="044f0-283">nx_telnet_server_delete</span><span class="sxs-lookup"><span data-stu-id="044f0-283">nx_telnet_server_delete</span></span>

<span data-ttu-id="044f0-284">Ta bort en Telnet-Server</span><span class="sxs-lookup"><span data-stu-id="044f0-284">Delete a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-285">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-285">Prototype</span></span>

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="044f0-286">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-286">Description</span></span>

<span data-ttu-id="044f0-287">Den här tjänsten tar bort en tidigare skapad Telnet Server-instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-287">This service deletes a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-288">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-288">Input Parameters</span></span>

- <span data-ttu-id="044f0-289">**server_ptr**: pekar mot kontroll block för Telnet-Server.</span><span class="sxs-lookup"><span data-stu-id="044f0-289">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-290">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-290">Return Values</span></span>

- <span data-ttu-id="044f0-291">**NX_SUCCESS**: (0X00) lyckad Server borttagning.</span><span class="sxs-lookup"><span data-stu-id="044f0-291">**NX_SUCCESS**: (0x00) Successful Server delete.</span></span>
- <span data-ttu-id="044f0-292">NX_PTR_ERROR: (0x07) ogiltig Server pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-292">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="044f0-293">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="044f0-293">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-294">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-294">Allowed From</span></span>

<span data-ttu-id="044f0-295">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-295">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-296">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-296">Example</span></span>

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a><span data-ttu-id="044f0-297">nx_telnet_server_disconnect</span><span class="sxs-lookup"><span data-stu-id="044f0-297">nx_telnet_server_disconnect</span></span>

<span data-ttu-id="044f0-298">Koppla från en Telnet-klient</span><span class="sxs-lookup"><span data-stu-id="044f0-298">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-299">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-299">Prototype</span></span>

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a><span data-ttu-id="044f0-300">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-300">Description</span></span>

<span data-ttu-id="044f0-301">Den här tjänsten kopplar från en tidigare ansluten klient på den här Telnet-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="044f0-301">This service disconnects a previously connected Client on this Telnet Server instance.</span></span> <span data-ttu-id="044f0-302">Den här rutinen anropas vanligt vis från programmets motringnings funktion för mottagning av data som svar på ett villkor som upptäckts i mottagna data.</span><span class="sxs-lookup"><span data-stu-id="044f0-302">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-303">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-303">Input Parameters</span></span>

- <span data-ttu-id="044f0-304">**server_ptr**: pekar mot kontroll block för Telnet-Server.</span><span class="sxs-lookup"><span data-stu-id="044f0-304">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="044f0-305">**logical_connection**: logisk anslutning motsvarande klient anslutningen på den här servern.</span><span class="sxs-lookup"><span data-stu-id="044f0-305">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="044f0-306">Giltigt värde intervall från 0 till NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="044f0-306">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-307">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-307">Return Values</span></span>

- <span data-ttu-id="044f0-308">**NX_SUCCESS**: (0X00) lyckad Server från koppling.</span><span class="sxs-lookup"><span data-stu-id="044f0-308">**NX_SUCCESS**: (0x00) Successful Server disconnect.</span></span>
- <span data-ttu-id="044f0-309">**NX_TELNET_ERROR**: det gick inte att koppla från servern (0xF0).</span><span class="sxs-lookup"><span data-stu-id="044f0-309">**NX_TELNET_ERROR**: (0xF0) Server disconnect failed.</span></span>
- <span data-ttu-id="044f0-310">NX_OPTION_ERROR: (0x0A) ogiltig logisk anslutning.</span><span class="sxs-lookup"><span data-stu-id="044f0-310">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="044f0-311">NX_PTR_ERROR: (0x07) ogiltig Server pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-311">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="044f0-312">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="044f0-312">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-313">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-313">Allowed From</span></span>

<span data-ttu-id="044f0-314">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-314">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-315">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-315">Example</span></span>

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a><span data-ttu-id="044f0-316">nx_telnet_server_get_open_connection_count</span><span class="sxs-lookup"><span data-stu-id="044f0-316">nx_telnet_server_get_open_connection_count</span></span>

<span data-ttu-id="044f0-317">Returnera antalet öppna anslutningar</span><span class="sxs-lookup"><span data-stu-id="044f0-317">Return number of currently open connections</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-318">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-318">Prototype</span></span>

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a><span data-ttu-id="044f0-319">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-319">Description</span></span>

<span data-ttu-id="044f0-320">Den här tjänsten returnerar antalet Telnet-klienter som är anslutna till varandra.</span><span class="sxs-lookup"><span data-stu-id="044f0-320">This service returns the number of currently connected Telnet Clients.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-321">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-321">Input Parameters</span></span>

- <span data-ttu-id="044f0-322">**server_ptr**: pekar mot kontroll block för Telnet-Server.</span><span class="sxs-lookup"><span data-stu-id="044f0-322">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="044f0-323">**Connection_count**: pekar på minne för att lagra antal anslutningar</span><span class="sxs-lookup"><span data-stu-id="044f0-323">**Connection_count**: Pointer to memory to store connection count</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-324">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-324">Return Values</span></span>

- <span data-ttu-id="044f0-325">**NX_SUCCESS**: (0X00) slutfördes.</span><span class="sxs-lookup"><span data-stu-id="044f0-325">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="044f0-326">NX_PTR_ERROR: (0x07) ogiltig Server pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-326">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="044f0-327">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="044f0-327">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-328">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-328">Allowed From</span></span>

<span data-ttu-id="044f0-329">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-330">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-330">Example</span></span>

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a><span data-ttu-id="044f0-331">nx_telnet_server_packet_send</span><span class="sxs-lookup"><span data-stu-id="044f0-331">nx_telnet_server_packet_send</span></span>

<span data-ttu-id="044f0-332">Skicka paket via klient anslutning</span><span class="sxs-lookup"><span data-stu-id="044f0-332">Send packet through Client connection</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-333">Prototype</span></span>

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="044f0-334">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-334">Description</span></span>

<span data-ttu-id="044f0-335">Den här tjänsten skickar ett paket till klient anslutningen på den här Telnet-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="044f0-335">This service sends a packet to the Client connection on this Telnet Server instance.</span></span> <span data-ttu-id="044f0-336">Den här rutinen anropas vanligt vis från programmets motringnings funktion för mottagning av data som svar på ett villkor som upptäckts i mottagna data.</span><span class="sxs-lookup"><span data-stu-id="044f0-336">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-337">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-337">Input Parameters</span></span>

- <span data-ttu-id="044f0-338">**server_ptr**: pekar mot kontroll block för Telnet-Server.</span><span class="sxs-lookup"><span data-stu-id="044f0-338">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="044f0-339">**logical_connection**: logisk anslutning motsvarande klient anslutningen på den här servern.</span><span class="sxs-lookup"><span data-stu-id="044f0-339">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="044f0-340">Giltigt värde intervall från 0 till NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="044f0-340">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>
- <span data-ttu-id="044f0-341">**packet_ptr**: pekar på det mottagna paketet.</span><span class="sxs-lookup"><span data-stu-id="044f0-341">**packet_ptr**: Pointer to the received packet.</span></span>
- <span data-ttu-id="044f0-342">**wait_option**: anger hur länge tjänsten ska vänta på att Telnet Server-paketet ska skickas.</span><span class="sxs-lookup"><span data-stu-id="044f0-342">**wait_option**: Defines how long the service will wait for the Telnet Server packet send.</span></span> <span data-ttu-id="044f0-343">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="044f0-343">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="044f0-344">**timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på Telnet-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="044f0-344">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="044f0-345">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills Telnet-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="044f0-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span> 

### <a name="return-values"></a><span data-ttu-id="044f0-346">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-346">Return Values</span></span>

- <span data-ttu-id="044f0-347">**NX_SUCCESS**: (0X00) slutfört paket sändning.</span><span class="sxs-lookup"><span data-stu-id="044f0-347">**NX_SUCCESS**: (0x00) Successful packet send.</span></span>
- <span data-ttu-id="044f0-348">**NX_TELNET_FAILED**: (0XF2) TCP-socket-sändning misslyckades.</span><span class="sxs-lookup"><span data-stu-id="044f0-348">**NX_TELNET_FAILED**: (0xF2) TCP socket send failed.</span></span>
- <span data-ttu-id="044f0-349">NX_OPTION_ERROR: (0x0A) ogiltig logisk anslutning.</span><span class="sxs-lookup"><span data-stu-id="044f0-349">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="044f0-350">NX_PTR_ERROR: (0x07) ogiltig Server pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-350">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="044f0-351">NX_CALLER_ERROR: (0x11) ogiltig anropar tjänst.</span><span class="sxs-lookup"><span data-stu-id="044f0-351">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-352">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-352">Allowed From</span></span>

<span data-ttu-id="044f0-353">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-354">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-354">Example</span></span>

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a><span data-ttu-id="044f0-355">nx_telnet_server_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="044f0-355">nx_telnet_server_packet_pool_set</span></span>

<span data-ttu-id="044f0-356">Ange tidigare skapade Packet bassäng som Telnet-adresspool</span><span class="sxs-lookup"><span data-stu-id="044f0-356">Set previously created packet pool as Telnet Server pool</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-357">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-357">Prototype</span></span>

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a><span data-ttu-id="044f0-358">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-358">Description</span></span>

<span data-ttu-id="044f0-359">Den här tjänsten anger en tidigare skapad modempool som programpoolen för Telnet-servern om NX_TELNET_SERVER_USER_CREATE_PACKET_POOL har definierats.</span><span class="sxs-lookup"><span data-stu-id="044f0-359">This service sets a previously created packet pool as the Telnet Server packet pool if NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined.</span></span> <span data-ttu-id="044f0-360">Det kräver också att NX_TELNET_SERVER_OPTION_DISABLE inte definieras så att Telnet-servern behöver en modempool för att överföra Telnet-alternativ till Telnet-klienter.</span><span class="sxs-lookup"><span data-stu-id="044f0-360">It also requires that NX_TELNET_SERVER_OPTION_DISABLE not be defined such that the Telnet Server needs a packet pool to transmit Telnet options to Telnet clients.</span></span>

<span data-ttu-id="044f0-361">Detta gör det möjligt för program att skapa en modempool i olika minnen, t. ex. minne utan cache, än i Telnet-serverns stack.</span><span class="sxs-lookup"><span data-stu-id="044f0-361">This permits applications to create the packet pool in different memory e.g. no cache memory, than the Telnet Server stack.</span></span> <span data-ttu-id="044f0-362">Observera att om den här funktionen inte kontrollerar om programpoolen för Telnet-servern redan har angetts.</span><span class="sxs-lookup"><span data-stu-id="044f0-362">Note that if this function does not check if the Telnet Server packet pool is already set.</span></span> <span data-ttu-id="044f0-363">Om den anropas på en icke-null-pekare för en Telnet-Server, kommer den att skriva över den och ersätta den befintliga poolen med pakethuvuden som intrycks av insamlings pekaren.</span><span class="sxs-lookup"><span data-stu-id="044f0-363">If it is called on a non null Telnet Server packet pool pointer, it will overwrite it and replace the existing packet pool with packet pool pointed to by the input pointer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-364">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-364">Input Parameters</span></span>

- <span data-ttu-id="044f0-365">**server_ptr**: pekare till kontroll block för Telnet-Server</span><span class="sxs-lookup"><span data-stu-id="044f0-365">**server_ptr**: Pointer to Telnet Server control block</span></span>
- <span data-ttu-id="044f0-366">**packet_pool_ptr**: pekare till tidigare skapade paketets pool</span><span class="sxs-lookup"><span data-stu-id="044f0-366">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-367">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-367">Return Values</span></span>

- <span data-ttu-id="044f0-368">**NX_SUCCESS**: (0X00) har angett poolen.</span><span class="sxs-lookup"><span data-stu-id="044f0-368">**NX_SUCCESS**: (0x00) Successfully set pool.</span></span>
- <span data-ttu-id="044f0-369">NX_PTR_ERROR: (0x07) ogiltig Server pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-369">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-370">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-370">Allowed From</span></span>

<span data-ttu-id="044f0-371">Init, trådar</span><span class="sxs-lookup"><span data-stu-id="044f0-371">Init, Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-372">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-372">Example</span></span>

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a><span data-ttu-id="044f0-373">nx_telnet_server_start</span><span class="sxs-lookup"><span data-stu-id="044f0-373">nx_telnet_server_start</span></span>

<span data-ttu-id="044f0-374">Starta en Telnet-Server</span><span class="sxs-lookup"><span data-stu-id="044f0-374">Start a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-375">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-375">Prototype</span></span>

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="044f0-376">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-376">Description</span></span>

<span data-ttu-id="044f0-377">Den här tjänsten startar en tidigare skapad Telnet Server-instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-377">This service starts a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-378">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-378">Input Parameters</span></span>

- <span data-ttu-id="044f0-379">**server_ptr**: pekar mot kontroll block för Telnet-Server.</span><span class="sxs-lookup"><span data-stu-id="044f0-379">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-380">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-380">Return Values</span></span>

- <span data-ttu-id="044f0-381">**NX_SUCCESS**: (0X00) har startats.</span><span class="sxs-lookup"><span data-stu-id="044f0-381">**NX_SUCCESS**: (0x00) Successfully started.</span></span>
- <span data-ttu-id="044f0-382">**NX_TELNET_NO_PACKET_POOL**: (0XF6) ingen paket uppsättnings uppsättning</span><span class="sxs-lookup"><span data-stu-id="044f0-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) No packet pool set</span></span>
- <span data-ttu-id="044f0-383">NX_PTR_ERROR: (0x07) ogiltig Server pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-383">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-384">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-384">Allowed From</span></span>

<span data-ttu-id="044f0-385">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="044f0-385">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-386">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-386">Example</span></span>

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a><span data-ttu-id="044f0-387">nx_telnet_server_stop</span><span class="sxs-lookup"><span data-stu-id="044f0-387">nx_telnet_server_stop</span></span>

<span data-ttu-id="044f0-388">Stoppa en Telnet-Server</span><span class="sxs-lookup"><span data-stu-id="044f0-388">Stop a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="044f0-389">Prototyp</span><span class="sxs-lookup"><span data-stu-id="044f0-389">Prototype</span></span>

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="044f0-390">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="044f0-390">Description</span></span>

<span data-ttu-id="044f0-391">Den här tjänsten stoppar en tidigare skapad och startad Telnet Server-instans.</span><span class="sxs-lookup"><span data-stu-id="044f0-391">This service stops a previously created and started Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="044f0-392">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="044f0-392">Input Parameters</span></span>

- <span data-ttu-id="044f0-393">**server_ptr**: pekar mot kontroll block för Telnet-Server.</span><span class="sxs-lookup"><span data-stu-id="044f0-393">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="044f0-394">Retur värden</span><span class="sxs-lookup"><span data-stu-id="044f0-394">Return Values</span></span>

- <span data-ttu-id="044f0-395">**NX_SUCCESS**: (0X00) har stoppats</span><span class="sxs-lookup"><span data-stu-id="044f0-395">**NX_SUCCESS**: (0x00) Successfully stopped</span></span>
- <span data-ttu-id="044f0-396">NX_PTR_ERROR: (0x07) ogiltig Server pekare.</span><span class="sxs-lookup"><span data-stu-id="044f0-396">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="044f0-397">NX_CALLER_ERROR: (0x11) ogiltig anropare av tjänst</span><span class="sxs-lookup"><span data-stu-id="044f0-397">NX_CALLER_ERROR: (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="044f0-398">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="044f0-398">Allowed From</span></span>

<span data-ttu-id="044f0-399">Konversation</span><span class="sxs-lookup"><span data-stu-id="044f0-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="044f0-400">Exempel</span><span class="sxs-lookup"><span data-stu-id="044f0-400">Example</span></span>

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```