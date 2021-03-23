---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo TFTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo TFTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825707"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a><span data-ttu-id="d2576-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo TFTP-tjänster</span><span class="sxs-lookup"><span data-stu-id="d2576-103">Chapter 3 - Description of Azure RTOS NetX Duo TFTP services</span></span>

<span data-ttu-id="d2576-104">Det här kapitlet innehåller en beskrivning av alla NetX Duo TFTP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="d2576-104">This chapter contains a description of all NetX Duo TFTP services (listed below) in alphabetic order.</span></span> <span data-ttu-id="d2576-105">Om inget annat anges stöder alla tjänster IPv6-och IPv4-kommunikation.</span><span class="sxs-lookup"><span data-stu-id="d2576-105">Unless otherwise specified, all services support IPv6 and IPv4 communications.</span></span>

<span data-ttu-id="d2576-106">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="d2576-106">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="d2576-107">**nxd_tftp_client_file_open**: *Öppna TFTP-klienttjänsten*</span><span class="sxs-lookup"><span data-stu-id="d2576-107">**nxd_tftp_client_file_open**: *Open TFTP client file*</span></span>

- <span data-ttu-id="d2576-108">**nxd_tftp_client_create**: *skapa en TFTP-klient instans*</span><span class="sxs-lookup"><span data-stu-id="d2576-108">**nxd_tftp_client_create**: *Create a TFTP client instance*</span></span>

- <span data-ttu-id="d2576-109">**nxd_tftp_client_delete**: *ta bort en TFTP-klient instans*</span><span class="sxs-lookup"><span data-stu-id="d2576-109">**nxd_tftp_client_delete**: *Delete a TFTP client instance*</span></span>

- <span data-ttu-id="d2576-110">**nxd_tftp_client_error_info_get**: *Hämta klient fel information*</span><span class="sxs-lookup"><span data-stu-id="d2576-110">**nxd_tftp_client_error_info_get**: *Get client error information*</span></span>

- <span data-ttu-id="d2576-111">**nxd_tftp_client_file_close**: *Stäng klient filen*</span><span class="sxs-lookup"><span data-stu-id="d2576-111">**nxd_tftp_client_file_close**: *Close client file*</span></span>

- <span data-ttu-id="d2576-112">**nxd_tftp_client_file_open**: *Öppna klient filen*</span><span class="sxs-lookup"><span data-stu-id="d2576-112">**nxd_tftp_client_file_open**: *Open client file*</span></span>

- <span data-ttu-id="d2576-113">**nxd_tftp_client_file_read**: *läsa ett block från klient filen*</span><span class="sxs-lookup"><span data-stu-id="d2576-113">**nxd_tftp_client_file_read**: *Read a block from client file*</span></span>

- <span data-ttu-id="d2576-114">**nxd_tftp_client_file_write**: *Skriv block till klient filen*</span><span class="sxs-lookup"><span data-stu-id="d2576-114">**nxd_tftp_client_file_write**: *Write block to client file*</span></span>

- <span data-ttu-id="d2576-115">**nxd_tftp_client_packet_allocate**: *allokera paket för skrivning av klient fil*</span><span class="sxs-lookup"><span data-stu-id="d2576-115">**nxd_tftp_client_packet_allocate**: *Allocate packet for client file write*</span></span>

- <span data-ttu-id="d2576-116">**nxd_tftp_client_set_interface**: *Ange det fysiska gränssnittet för TFTP-begäranden*</span><span class="sxs-lookup"><span data-stu-id="d2576-116">**nxd_tftp_client_set_interface**: *Set the physical interface for TFTP requests*</span></span>

- <span data-ttu-id="d2576-117">**nxd_tftp_server_create**: *skapa TFTP-server*</span><span class="sxs-lookup"><span data-stu-id="d2576-117">**nxd_tftp_server_create**: *Create TFTP server*</span></span>

- <span data-ttu-id="d2576-118">**nxd_tftp_server_delete**: *ta bort TFTP-server*</span><span class="sxs-lookup"><span data-stu-id="d2576-118">**nxd_tftp_server_delete**: *Delete TFTP server*</span></span>

- <span data-ttu-id="d2576-119">**nxd_tftp_server_start**: *Starta TFTP-server*</span><span class="sxs-lookup"><span data-stu-id="d2576-119">**nxd_tftp_server_start**: *Start TFTP server*</span></span>

- <span data-ttu-id="d2576-120">**nxd_tftp_server_stop**: *stoppa TFTP-server*</span><span class="sxs-lookup"><span data-stu-id="d2576-120">**nxd_tftp_server_stop**: *Stop TFTP server*</span></span>

> [!NOTE] 
> <span data-ttu-id="d2576-121">IPv4-motsvarigheterna till alla de tjänster som anges ovan är tillgängliga i NetX Duo TFTP-klienten och-servern, t. ex. *nx_tftp_server_create* och *nx_tftp_client_file_open*.</span><span class="sxs-lookup"><span data-stu-id="d2576-121">The IPv4 equivalents of all the services listed above are available in NetX Duo TFTP Client and Server e.g. *nx_tftp_server_create* and *nx_tftp_client_file_open*.</span></span> <span data-ttu-id="d2576-122">Endast API-beskrivningarna Duo, t. ex. tjänster som börjar med *nxd_*, finns på följande sidor.</span><span class="sxs-lookup"><span data-stu-id="d2576-122">Only the ‘Duo’ API descriptions, e.g. services beginning with *nxd_*, are provided in the following pages.</span></span> <span data-ttu-id="d2576-123">När en NXD_ADDRESS \* -inmatare anges, anropar IPv4 motsvarande API för ulong-inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-123">Where an NXD_ADDRESS \* input is specified, the IPv4 equivalent API calls for ULONG input.</span></span> <span data-ttu-id="d2576-124">Annars finns det ingen skillnad i att använda API: et.</span><span class="sxs-lookup"><span data-stu-id="d2576-124">Otherwise there is no difference in using the API.</span></span>

## <a name="nxd_tftp_client_create"></a><span data-ttu-id="d2576-125">nxd_tftp_client_create</span><span class="sxs-lookup"><span data-stu-id="d2576-125">nxd_tftp_client_create</span></span>

<span data-ttu-id="d2576-126">Skapa en TFTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="d2576-126">Create a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-127">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-127">Prototype</span></span>

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="d2576-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-128">Description</span></span>

<span data-ttu-id="d2576-129">Den här tjänsten skapar en TFTP-klient instans för den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d2576-129">This service creates a TFTP Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2576-130">Programmet måste kontrol lera att den angivna IP-adresspoolen och Packet-poolen redan har skapats.</span><span class="sxs-lookup"><span data-stu-id="d2576-130">The application must make certain the supplied IP and packet pool are already created.</span></span> <span data-ttu-id="d2576-131">Dessutom måste UDP vara aktiverat för IP-instansen innan den här tjänsten anropas.</span><span class="sxs-lookup"><span data-stu-id="d2576-131">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-132">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-132">Input Parameters</span></span>

- <span data-ttu-id="d2576-133">**tftp_client_ptr** Pekare till kontroll block för TFTP-klient.</span><span class="sxs-lookup"><span data-stu-id="d2576-133">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="d2576-134">**tftp_client_name** Namnet på den här TFTP-klientcertifikatet</span><span class="sxs-lookup"><span data-stu-id="d2576-134">**tftp_client_name** Name of this TFTP Client instance</span></span>

- <span data-ttu-id="d2576-135">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d2576-135">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="d2576-136">**pool_ptr** Pekare till instansen för Packet-poolens TFTP.</span><span class="sxs-lookup"><span data-stu-id="d2576-136">**pool_ptr** Pointer to packet pool TFTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-137">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-137">Return Values</span></span>

- <span data-ttu-id="d2576-138">**NX_SUCCESS**(0X00) korrekt TFTP-skapande.</span><span class="sxs-lookup"><span data-stu-id="d2576-138">**NX_SUCCESS**(0x00) Successful TFTP create.</span></span>

- <span data-ttu-id="d2576-139">**NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig eller IP-version som inte stöds</span><span class="sxs-lookup"><span data-stu-id="d2576-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid or unsupported IP version</span></span>

- <span data-ttu-id="d2576-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0X08) ogiltig Server-IP-adress togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP address received</span></span>

- <span data-ttu-id="d2576-141">**NX_TFTP_NO_ACK_RECEIVED** (0X09) Server ack har inte tagits emot</span><span class="sxs-lookup"><span data-stu-id="d2576-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK not received</span></span>

- <span data-ttu-id="d2576-142">NX_PTR_ERROR (0x16) ogiltig IP-, pool-eller TFTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="d2576-142">NX_PTR_ERROR (0x16) Invalid IP, pool, or TFTP pointer.</span></span>

- <span data-ttu-id="d2576-143">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="d2576-143">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="d2576-144">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d2576-144">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-145">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-145">Allowed From</span></span>

<span data-ttu-id="d2576-146">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="d2576-146">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-147">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-147">Example</span></span>

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a><span data-ttu-id="d2576-148">nxd_tftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="d2576-148">nxd_tftp_client_delete</span></span>

<span data-ttu-id="d2576-149">Ta bort en TFTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="d2576-149">Delete a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-150">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-150">Prototype</span></span>

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="d2576-151">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-151">Description</span></span>

<span data-ttu-id="d2576-152">Den här tjänsten tar bort en tidigare skapad TFTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="d2576-152">This service deletes a previously created TFTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-153">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-153">Input Parameters</span></span>

- <span data-ttu-id="d2576-154">**tftp_client_ptr** Pekare till tidigare skapad TFTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="d2576-154">**tftp_client_ptr** Pointer to previously created TFTP client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-155">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-155">Return Values</span></span>

- <span data-ttu-id="d2576-156">**NX_SUCCESS** (0X00) lyckad TFTP-klient borttagning.</span><span class="sxs-lookup"><span data-stu-id="d2576-156">**NX_SUCCESS** (0x00) Successful TFTP Client delete.</span></span>

- <span data-ttu-id="d2576-157">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-157">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-158">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d2576-158">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-159">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-159">Allowed From</span></span>

<span data-ttu-id="d2576-160">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-160">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-161">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-161">Example</span></span>

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a><span data-ttu-id="d2576-162">nxd_tftp_client_error_info_get</span><span class="sxs-lookup"><span data-stu-id="d2576-162">nxd_tftp_client_error_info_get</span></span>

<span data-ttu-id="d2576-163">Hämta information om klient fel</span><span class="sxs-lookup"><span data-stu-id="d2576-163">Get client error information</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-164">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-164">Prototype</span></span>

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a><span data-ttu-id="d2576-165">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-165">Description</span></span>

<span data-ttu-id="d2576-166">Den här tjänsten returnerar den senaste felkoden som togs emot och anger pekaren till klientens interna fel sträng.</span><span class="sxs-lookup"><span data-stu-id="d2576-166">This service returns the last error code received and sets the pointer to the client’s internal error string.</span></span> <span data-ttu-id="d2576-167">I fel tillstånd kan användaren se det senaste felet som skickats av servern.</span><span class="sxs-lookup"><span data-stu-id="d2576-167">In error conditions, the user can view the last error sent by the server.</span></span> <span data-ttu-id="d2576-168">En null-felsträng anger att det inte finns något fel.</span><span class="sxs-lookup"><span data-stu-id="d2576-168">A null error string indicates no error is present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-169">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-169">Input Parameters</span></span>

- <span data-ttu-id="d2576-170">**tftp_client_ptr** Pekare till tidigare skapad TFTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="d2576-170">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="d2576-171">**error_code** Pekare till mål arean för felkod</span><span class="sxs-lookup"><span data-stu-id="d2576-171">**error_code** Pointer to destination area for error code</span></span>

- <span data-ttu-id="d2576-172">**ERROR_STRING** Pekare till mål för fel sträng</span><span class="sxs-lookup"><span data-stu-id="d2576-172">**error_string** Pointer to destination for error string</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-173">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-173">Return Values</span></span>

- <span data-ttu-id="d2576-174">**NX_SUCCESS** (0x00) Det gick inte att hämta TFTP-felinformation.</span><span class="sxs-lookup"><span data-stu-id="d2576-174">**NX_SUCCESS** (0x00) Successful TFTP error info get.</span></span>  

- <span data-ttu-id="d2576-175">NX_PTR_ERROR (0x16) ogiltig TFTP-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="d2576-175">NX_PTR_ERROR (0x16) Invalid TFTP Client pointer.</span></span>

- <span data-ttu-id="d2576-176">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d2576-176">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-177">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-177">Allowed From</span></span>

<span data-ttu-id="d2576-178">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-178">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-179">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-179">Example</span></span>

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a><span data-ttu-id="d2576-180">nxd_tftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="d2576-180">nxd_tftp_client_file_close</span></span>

<span data-ttu-id="d2576-181">Stäng klient filen</span><span class="sxs-lookup"><span data-stu-id="d2576-181">Close client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-182">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-182">Prototype</span></span>

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d2576-183">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-183">Description</span></span>

<span data-ttu-id="d2576-184">Den här tjänsten stänger den tidigare öppnade filen av denna TFTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="d2576-184">This service closes the previously opened file by this TFTP Client instance.</span></span> <span data-ttu-id="d2576-185">En TFTP-klientsession får bara ha en fil öppen åt gången.</span><span class="sxs-lookup"><span data-stu-id="d2576-185">A TFTP Client instance is allowed to have only one file open at a time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-186">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-186">Input Parameters</span></span>

- <span data-ttu-id="d2576-187">**tftp_client_ptr** Pekare till tidigare skapad TFTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="d2576-187">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="d2576-188">**ip_type** Ange vilket IP-protokoll som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2576-188">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d2576-189">Giltiga alternativ är IPv4 (4) eller IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d2576-189">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-190">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-190">Return Values</span></span>

- <span data-ttu-id="d2576-191">**NX_SUCCESS** (0X00) TFTP-filen stängs.</span><span class="sxs-lookup"><span data-stu-id="d2576-191">**NX_SUCCESS** (0x00) Successful TFTP file close.</span></span>

- <span data-ttu-id="d2576-192">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-192">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-193">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d2576-193">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="d2576-194">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare.</span><span class="sxs-lookup"><span data-stu-id="d2576-194">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-195">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-195">Allowed From</span></span>

<span data-ttu-id="d2576-196">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-197">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-197">Example</span></span>

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a><span data-ttu-id="d2576-198">nx_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="d2576-198">nx_tftp_client_file_open</span></span>

<span data-ttu-id="d2576-199">Öppna TFTP-klienttjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-199">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-200">Prototype</span></span>

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d2576-201">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-201">Description</span></span>

<span data-ttu-id="d2576-202">Den här tjänsten försöker öppna den angivna filen på TFTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="d2576-202">This service attempts to open the specified file on the TFTP Server at the specified IP address.</span></span> <span data-ttu-id="d2576-203">Filen kommer att öppnas för läsning eller skrivning.</span><span class="sxs-lookup"><span data-stu-id="d2576-203">The file will be opened for either reading or writing.</span></span> 

> [!NOTE] 
> <span data-ttu-id="d2576-204">Detta är begränsat till endast IPv4-paket och är avsett för stöd för NetX TFTP-program.</span><span class="sxs-lookup"><span data-stu-id="d2576-204">This is limited to IPv4 packets only, and is intended for supporting NetX TFTP applications.</span></span> <span data-ttu-id="d2576-205">Utvecklare uppmuntras att hamna i sina program för att använda motsvarande "Duo"- *nxd_tftp_client_file_open.*</span><span class="sxs-lookup"><span data-stu-id="d2576-205">Developers are encouraged to port their applications to using equivalent “duo” service *nxd_tftp_client_file_open.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-206">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-206">Input Parameters</span></span>

- <span data-ttu-id="d2576-207">**tftp_client_ptr** Pekare till TFTP-Control Block.</span><span class="sxs-lookup"><span data-stu-id="d2576-207">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="d2576-208">**file_name** ASCII-filnamn, NULL-avslutad och med lämplig Sök vägs information.</span><span class="sxs-lookup"><span data-stu-id="d2576-208">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="d2576-209">**server_ip_address** Server TFTP-adress.</span><span class="sxs-lookup"><span data-stu-id="d2576-209">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="d2576-210">**open_type** Typ av öppen begäran, antingen:</span><span class="sxs-lookup"><span data-stu-id="d2576-210">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="d2576-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="d2576-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="d2576-212">**NX_TFTP_OPEN_FOR_WRITE** (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="d2576-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="d2576-213">**wait_option** Definierar hur länge tjänsten ska vänta på att TFTP-klienttjänsten är öppen.</span><span class="sxs-lookup"><span data-stu-id="d2576-213">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="d2576-214">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="d2576-214">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d2576-215">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d2576-215">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d2576-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d2576-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span> 
  
  <span data-ttu-id="d2576-217">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills en TFTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="d2576-217">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span> 
  
  <span data-ttu-id="d2576-218">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på TFTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="d2576-218">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="d2576-219">**ip_type** Ange vilket IP-protokoll som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2576-219">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d2576-220">Giltiga alternativ är IPv4 (4) eller IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d2576-220">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-221">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-221">Return Values</span></span>

- <span data-ttu-id="d2576-222">**NX_SUCCESS** (0X00) klient filen är öppen</span><span class="sxs-lookup"><span data-stu-id="d2576-222">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="d2576-223">**NX_TFTP_NOT_CLOSED** -klienten (0xC3) har redan öppen fil</span><span class="sxs-lookup"><span data-stu-id="d2576-223">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="d2576-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d2576-225">**NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern</span><span class="sxs-lookup"><span data-stu-id="d2576-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="d2576-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0X08) ogiltig Server-IP togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="d2576-227">**NX_TFTP_CODE_ERROR** (0X05) tog emot felkod</span><span class="sxs-lookup"><span data-stu-id="d2576-227">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d2576-228">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-228">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-229">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-229">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d2576-230">NX_IP_ADDRESS_ERROR (0x21) ogiltig Server-IP-adress</span><span class="sxs-lookup"><span data-stu-id="d2576-230">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="d2576-231">NX_OPTION_ERROR (0x0A) ogiltig öppen typ</span><span class="sxs-lookup"><span data-stu-id="d2576-231">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-232">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-232">Allowed From</span></span>

<span data-ttu-id="d2576-233">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-234">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-234">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a><span data-ttu-id="d2576-235">nxd_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="d2576-235">nxd_tftp_client_file_open</span></span>

<span data-ttu-id="d2576-236">Öppna TFTP-klienttjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-236">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-237">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-237">Prototype</span></span>

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d2576-238">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-238">Description</span></span>

<span data-ttu-id="d2576-239">Den här tjänsten försöker öppna den angivna filen på TFTP-servern på den angivna IPv6-adressen.</span><span class="sxs-lookup"><span data-stu-id="d2576-239">This service attempts to open the specified file on the TFTP Server at the specified IPv6 address.</span></span> <span data-ttu-id="d2576-240">Filen kommer att öppnas för läsning eller skrivning.</span><span class="sxs-lookup"><span data-stu-id="d2576-240">The file will be opened for either reading or writing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-241">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-241">Input Parameters</span></span>

- <span data-ttu-id="d2576-242">**tftp_client_ptr** Pekare till TFTP-Control Block.</span><span class="sxs-lookup"><span data-stu-id="d2576-242">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="d2576-243">**file_name** ASCII-filnamn, NULL-avslutad och med lämplig Sök vägs information.</span><span class="sxs-lookup"><span data-stu-id="d2576-243">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="d2576-244">**server_ip_address** Server TFTP-adress.</span><span class="sxs-lookup"><span data-stu-id="d2576-244">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="d2576-245">**open_type** Typ av öppen begäran, antingen:</span><span class="sxs-lookup"><span data-stu-id="d2576-245">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="d2576-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="d2576-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="d2576-247">**NX_TFTP_OPEN_FOR_WRITE** (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="d2576-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="d2576-248">**wait_option** Definierar hur länge tjänsten ska vänta på att TFTP-klienttjänsten är öppen.</span><span class="sxs-lookup"><span data-stu-id="d2576-248">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="d2576-249">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="d2576-249">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d2576-250">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d2576-250">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d2576-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d2576-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d2576-252">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills en TFTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="d2576-252">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span>

  <span data-ttu-id="d2576-253">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på TFTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="d2576-253">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="d2576-254">**ip_type** Ange vilket IP-protokoll som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2576-254">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d2576-255">Giltiga alternativ är IPv4 (4) eller IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d2576-255">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-256">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-256">Return Values</span></span>

- <span data-ttu-id="d2576-257">**NX_SUCCESS** (0X00) klient filen är öppen</span><span class="sxs-lookup"><span data-stu-id="d2576-257">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="d2576-258">**NX_TFTP_NOT_CLOSED** -klienten (0xC3) har redan öppen fil</span><span class="sxs-lookup"><span data-stu-id="d2576-258">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="d2576-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d2576-260">**NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern</span><span class="sxs-lookup"><span data-stu-id="d2576-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="d2576-261">**NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig IP-version</span><span class="sxs-lookup"><span data-stu-id="d2576-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="d2576-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0X08) ogiltig Server-IP togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="d2576-263">**NX_TFTP_CODE_ERROR** (0X05) tog emot felkod</span><span class="sxs-lookup"><span data-stu-id="d2576-263">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d2576-264">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-264">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-265">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-265">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d2576-266">NX_IP_ADDRESS_ERROR (0x21) ogiltig Server-IP-adress</span><span class="sxs-lookup"><span data-stu-id="d2576-266">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="d2576-267">NX_OPTION_ERROR (0x0A) ogiltig öppen typ</span><span class="sxs-lookup"><span data-stu-id="d2576-267">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

- <span data-ttu-id="d2576-268">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="d2576-268">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-269">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-269">Allowed From</span></span>

<span data-ttu-id="d2576-270">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-270">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-271">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-271">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a><span data-ttu-id="d2576-272">nxd_tftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="d2576-272">nxd_tftp_client_file_read</span></span>

<span data-ttu-id="d2576-273">Läsa ett block från klient filen</span><span class="sxs-lookup"><span data-stu-id="d2576-273">Read a block from client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-274">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-274">Prototype</span></span>

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d2576-275">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-275">Description</span></span>

<span data-ttu-id="d2576-276">Den här tjänsten läser ett 512-byte-block från den tidigare öppnade TFTP-klientdatorn.</span><span class="sxs-lookup"><span data-stu-id="d2576-276">This service reads a 512-byte block from the previously opened TFTP Client file.</span></span> <span data-ttu-id="d2576-277">Ett block som innehåller färre än 512 byte signalerar slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="d2576-277">A block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-278">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-278">Input Parameters</span></span>

- <span data-ttu-id="d2576-279">**tftp_client_ptr** Pekare till kontroll block för TFTP-klient.</span><span class="sxs-lookup"><span data-stu-id="d2576-279">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="d2576-280">**packet_ptr** Mål för paket som innehåller blocket läst från filen.</span><span class="sxs-lookup"><span data-stu-id="d2576-280">**packet_ptr** Destination for packet containing the block read from the file.</span></span>

- <span data-ttu-id="d2576-281">**wait_option** Definierar hur länge tjänsten ska vänta på att läsningen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="d2576-281">**wait_option** Defines how long the service will wait for the read to complete.</span></span> <span data-ttu-id="d2576-282">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="d2576-282">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d2576-283">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d2576-283">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d2576-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d2576-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d2576-285">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills TFTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="d2576-285">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>

  <span data-ttu-id="d2576-286">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det högsta antalet timer-Tick som ska vara pausat under väntan på att TFTP-servern ska skicka ett block av filen.</span><span class="sxs-lookup"><span data-stu-id="d2576-286">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send a block of the file.</span></span>

- <span data-ttu-id="d2576-287">**ip_type** Ange vilket IP-protokoll som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2576-287">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d2576-288">Giltiga alternativ är IPv4 (4) eller IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d2576-288">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-289">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-289">Return Values</span></span>

- <span data-ttu-id="d2576-290">**NX_SUCCESS** (0X00) lyckad klient block läsning</span><span class="sxs-lookup"><span data-stu-id="d2576-290">**NX_SUCCESS** (0x00) Successful Client block read</span></span>

- <span data-ttu-id="d2576-291">**NX_TFTP_NOT_OPEN** (0xC3) den angivna klient filen är inte öppen för läsning</span><span class="sxs-lookup"><span data-stu-id="d2576-291">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for reading</span></span>

- <span data-ttu-id="d2576-292">**NX_NO_PACKET** (0X01) inget paket togs emot från servern.</span><span class="sxs-lookup"><span data-stu-id="d2576-292">**NX_NO_PACKET** (0x01) No Packet received from Server.</span></span>

- <span data-ttu-id="d2576-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d2576-294">**NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern</span><span class="sxs-lookup"><span data-stu-id="d2576-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from Server</span></span>

- <span data-ttu-id="d2576-295">**NX_TFTP_END_OF_FILE** (0XC5) slutet av filen upptäcktes (inte ett fel).</span><span class="sxs-lookup"><span data-stu-id="d2576-295">**NX_TFTP_END_OF_FILE** (0xC5) End of file detected (not an error).</span></span>

- <span data-ttu-id="d2576-296">**NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig IP-version</span><span class="sxs-lookup"><span data-stu-id="d2576-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="d2576-297">**NX_TFTP_CODE_ERROR** (0X05) tog emot felkod</span><span class="sxs-lookup"><span data-stu-id="d2576-297">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d2576-298">**NX_TFTP_FAILED** (0XC2) Okänd TFTP-kod mottagen</span><span class="sxs-lookup"><span data-stu-id="d2576-298">**NX_TFTP_FAILED** (0xC2) Unknown TFTP code received</span></span>

- <span data-ttu-id="d2576-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0X0a) ogiltigt block nummer togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Invalid block number received</span></span>

- <span data-ttu-id="d2576-300">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-300">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-301">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-301">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d2576-302">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="d2576-302">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-303">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-303">Allowed From</span></span>

<span data-ttu-id="d2576-304">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-304">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-305">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-305">Example</span></span>

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a><span data-ttu-id="d2576-306">nxd_tftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="d2576-306">nxd_tftp_client_file_write</span></span>

<span data-ttu-id="d2576-307">Skriv ett block till klient filen</span><span class="sxs-lookup"><span data-stu-id="d2576-307">Write a block to Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-308">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-308">Prototype</span></span>

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d2576-309">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-309">Description</span></span>

<span data-ttu-id="d2576-310">Den här tjänsten skriver ett 512-byte-block till den tidigare öppnade TFTP-klientdatorn.</span><span class="sxs-lookup"><span data-stu-id="d2576-310">This service writes a 512-byte block to the previously opened TFTP Client file.</span></span> <span data-ttu-id="d2576-311">Om du anger ett block som innehåller färre än 512 byte signalerar du slutet på filen.</span><span class="sxs-lookup"><span data-stu-id="d2576-311">Specifying a block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-312">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-312">Input Parameters</span></span>

- <span data-ttu-id="d2576-313">**tftp_client_ptr** Pekare till kontroll block för TFTP-klient.</span><span class="sxs-lookup"><span data-stu-id="d2576-313">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="d2576-314">**packet_ptr** Paket som innehåller det block som ska skrivas till filen.</span><span class="sxs-lookup"><span data-stu-id="d2576-314">**packet_ptr** Packet containing the block to write to the file.</span></span>

- <span data-ttu-id="d2576-315">**wait_option** Definierar hur länge tjänsten väntar på att skrivningen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="d2576-315">**wait_option** Defines how long the service will wait for the write to complete.</span></span> <span data-ttu-id="d2576-316">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="d2576-316">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d2576-317">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d2576-317">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d2576-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d2576-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d2576-319">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills TFTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="d2576-319">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>
 
  <span data-ttu-id="d2576-320">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på att TFTP-servern ska skicka en bekräftelse för skrivbegäran.</span><span class="sxs-lookup"><span data-stu-id="d2576-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send an ACK for the write request.</span></span>

- <span data-ttu-id="d2576-321">**ip_type** Ange vilket IP-protokoll som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2576-321">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d2576-322">Giltiga alternativ är IPv4 (4) eller IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d2576-322">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-323">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-323">Return Values</span></span>

- <span data-ttu-id="d2576-324">**NX_SUCCESS** (0X00) lyckad klient block skrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-324">**NX_SUCCESS** (0x00) Successful Client block write</span></span>

- <span data-ttu-id="d2576-325">**NX_TFTP_NOT_OPEN** (0xC3) den angivna klient filen är inte öppen för skrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-325">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for writing</span></span>

- <span data-ttu-id="d2576-326">**NX_TFTP_TIMEOUT** (0XC1) timeout vid väntan på Server ack</span><span class="sxs-lookup"><span data-stu-id="d2576-326">**NX_TFTP_TIMEOUT** (0xC1) Timeout waiting for Server ACK</span></span>

- <span data-ttu-id="d2576-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d2576-328">**NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern</span><span class="sxs-lookup"><span data-stu-id="d2576-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="d2576-329">**NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig IP-version</span><span class="sxs-lookup"><span data-stu-id="d2576-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="d2576-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot</span><span class="sxs-lookup"><span data-stu-id="d2576-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d2576-331">**NX_TFTP_CODE_ERROR** (0X05) tog emot felkod</span><span class="sxs-lookup"><span data-stu-id="d2576-331">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d2576-332">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-332">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-333">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-333">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d2576-334">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="d2576-334">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-335">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-335">Allowed From</span></span>

<span data-ttu-id="d2576-336">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-336">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-337">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-337">Example</span></span>

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a><span data-ttu-id="d2576-338">nxd_tftp_client_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d2576-338">nxd_tftp_client_packet_allocate</span></span>

<span data-ttu-id="d2576-339">Allokera paket för skrivning av klient fil</span><span class="sxs-lookup"><span data-stu-id="d2576-339">Allocate packet for Client file write</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-340">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-340">Prototype</span></span>

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d2576-341">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-341">Description</span></span>

<span data-ttu-id="d2576-342">Den här tjänsten allokerar ett UDP-paket från den angivna poolen och gör plats för TFTP-huvudet i 4 byte innan paketet returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="d2576-342">This service allocates a UDP packet from the specified packet pool and makes room for the 4-byte TFTP header before the packet is returned to the caller.</span></span> <span data-ttu-id="d2576-343">Anroparen kan sedan bygga en buffert för att skriva till en klient fil.</span><span class="sxs-lookup"><span data-stu-id="d2576-343">The caller can then build a buffer for writing to a client file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-344">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-344">Input Parameters</span></span>

- <span data-ttu-id="d2576-345">**pool_ptr** Pekare till Packet bassäng.</span><span class="sxs-lookup"><span data-stu-id="d2576-345">**pool_ptr** Pointer to packet pool.</span></span>

- <span data-ttu-id="d2576-346">**packet_ptr** Mål för pekare till allokerat paket.</span><span class="sxs-lookup"><span data-stu-id="d2576-346">**packet_ptr** Destination for pointer to allocated packet.</span></span>

- <span data-ttu-id="d2576-347">**wait_option** Definierar hur länge tjänsten ska vänta på att paket tilldelningen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="d2576-347">**wait_option** Defines how long the service will wait for the packet allocate to complete.</span></span> <span data-ttu-id="d2576-348">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="d2576-348">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d2576-349">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d2576-349">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d2576-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d2576-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d2576-351">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills tilldelningen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="d2576-351">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the allocation completes.</span></span>

  <span data-ttu-id="d2576-352">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på paket tilldelningen.</span><span class="sxs-lookup"><span data-stu-id="d2576-352">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the packet allocation.</span></span>

- <span data-ttu-id="d2576-353">**ip_type** Ange vilket IP-protokoll som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d2576-353">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d2576-354">Giltiga alternativ är IPv4 (4) eller IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d2576-354">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-355">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-355">Return Values</span></span>

- <span data-ttu-id="d2576-356">**NX_SUCCESS** (0x00) paket tilldelningen lyckades</span><span class="sxs-lookup"><span data-stu-id="d2576-356">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>

- <span data-ttu-id="d2576-357">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-357">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-358">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-358">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d2576-359">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="d2576-359">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-360">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-360">Allowed From</span></span>

<span data-ttu-id="d2576-361">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-361">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-362">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-362">Example</span></span>

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a><span data-ttu-id="d2576-363">nxd_tftp_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="d2576-363">nxd_tftp_client_set_interface</span></span>

<span data-ttu-id="d2576-364">Ange fysiskt gränssnitt för TFTP-begäranden</span><span class="sxs-lookup"><span data-stu-id="d2576-364">Set physical interface for TFTP requests</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-365">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-365">Prototype</span></span>

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a><span data-ttu-id="d2576-366">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-366">Description</span></span>

<span data-ttu-id="d2576-367">Tjänsten använder gränssnitts indexet för att ange det fysiska gränssnittet för TFTP-klienten för att skicka och ta emot TFTP-paket.</span><span class="sxs-lookup"><span data-stu-id="d2576-367">This service uses the input interface index to set the physical interface for the TFTP Client to send and receive TFTP packets.</span></span> <span data-ttu-id="d2576-368">Standardvärdet är noll för det primära gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="d2576-368">The default value is zero, for the primary interface.</span></span>

> [!NOTE]
> <span data-ttu-id="d2576-369">NetX Duo måste ha stöd för multihome-adressering (v 5.6 eller senare) för att kunna använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d2576-369">NetX Duo must support multihome addressing (v5.6 or later) to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-370">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-370">Input Parameters</span></span>

- <span data-ttu-id="d2576-371">**tftp_client_ptr** Pekare till TFTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="d2576-371">**tftp_client_ptr** Pointer to TFTP Client instance</span></span>

- <span data-ttu-id="d2576-372">**if_index** Index för det fysiska gränssnitt som ska användas</span><span class="sxs-lookup"><span data-stu-id="d2576-372">**if_index** Index of physical interface to use</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-373">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-373">Return Values</span></span>

- <span data-ttu-id="d2576-374">**NX_SUCCESS** (0X00) har inställt gränssnitt (0X0B) ogiltig gränssnitts information</span><span class="sxs-lookup"><span data-stu-id="d2576-374">**NX_SUCCESS** (0x00) Successfully set interface (0x0B) Invalid interface input</span></span>

- <span data-ttu-id="d2576-375">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-375">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-376">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-376">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d2576-377">NX_TFTP_INVALID_INTERFACE (0x0B) ogiltig gränssnitts information</span><span class="sxs-lookup"><span data-stu-id="d2576-377">NX_TFTP_INVALID_INTERFACE (0x0B) Invalid interface input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-378">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-378">Allowed From</span></span>

<span data-ttu-id="d2576-379">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-380">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-380">Example</span></span>

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a><span data-ttu-id="d2576-381">nxd_tftp_server_create</span><span class="sxs-lookup"><span data-stu-id="d2576-381">nxd_tftp_server_create</span></span>

<span data-ttu-id="d2576-382">Skapa TFTP-server</span><span class="sxs-lookup"><span data-stu-id="d2576-382">Create TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-383">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-383">Prototype</span></span>

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="d2576-384">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-384">Description</span></span>

<span data-ttu-id="d2576-385">Den här tjänsten skapar en TFTP-server som svarar på TFTP-klientbegäran på port 69.</span><span class="sxs-lookup"><span data-stu-id="d2576-385">This service creates a TFTP Server that responds to TFTP Client requests on port 69.</span></span> <span data-ttu-id="d2576-386">Servern måste startas av ett efterföljande anrop till *nxd_tftp_server_start*.</span><span class="sxs-lookup"><span data-stu-id="d2576-386">The Server must be started by a subsequent call to *nxd_tftp_server_start*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2576-387">Programmet måste kontrol lera att den angivna IP-instansen, mediepoolen och FileX-medie instansen redan har skapats.</span><span class="sxs-lookup"><span data-stu-id="d2576-387">The application must make certain the supplied IP instance, packet pool, and FileX media instance are already created.</span></span> <span data-ttu-id="d2576-388">Dessutom måste UDP vara aktiverat för IP-instansen innan den här tjänsten anropas.</span><span class="sxs-lookup"><span data-stu-id="d2576-388">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-389">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-389">Input Parameters</span></span>

- <span data-ttu-id="d2576-390">**tftp_server_ptr** Pekare till kontroll block för TFTP-server.</span><span class="sxs-lookup"><span data-stu-id="d2576-390">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

- <span data-ttu-id="d2576-391">**tftp_server_name** Namnet på den här TFTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="d2576-391">**tftp_server_name** Name of this TFTP Server instance</span></span>

- <span data-ttu-id="d2576-392">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="d2576-392">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="d2576-393">**media_ptr** Pekare till FileX Media-instans.</span><span class="sxs-lookup"><span data-stu-id="d2576-393">**media_ptr** Pointer to FileX media instance.</span></span>

- <span data-ttu-id="d2576-394">**stack_ptr** Pekare till TFTP-serverns stack-yta.</span><span class="sxs-lookup"><span data-stu-id="d2576-394">**stack_ptr** Pointer to TFTP Server stack area.</span></span>

- <span data-ttu-id="d2576-395">**stack_size** Antal byte i TFTP-serverns stack.</span><span class="sxs-lookup"><span data-stu-id="d2576-395">**stack_size** Number of bytes in the TFTP Server stack.</span></span>

- <span data-ttu-id="d2576-396">**pool_ptr** Pekare till TFTP-adresspool.</span><span class="sxs-lookup"><span data-stu-id="d2576-396">**pool_ptr** Pointer to TFTP packet pool.</span></span> 

> [!NOTE]
> <span data-ttu-id="d2576-397">Den angivna poolen måste ha paket nytto laster minst 580 byte stor. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d2576-397">The supplied pool must have packet payloads at least 580 bytes in size.<sup>1</sup></span></span>

<span data-ttu-id="d2576-398"><sup>1</sup> data delen i ett paket är exakt 512 byte, men paketets nytto Last storlek måste vara minst 572 byte.</span><span class="sxs-lookup"><span data-stu-id="d2576-398"><sup>1</sup> The data portion of a packet is exactly 512 bytes, but the packet payload size must be at least 572 bytes.</span></span> <span data-ttu-id="d2576-399">Återstående byte används för rubrikerna UDP, IPv6 och Ethernet och eventuella efterföljande byte som krävs av driv rutinen för justering.</span><span class="sxs-lookup"><span data-stu-id="d2576-399">The remaining bytes are used for the UDP, IPv6, and Ethernet headers and potential trailing bytes required by the driver for alignment.</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-400">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-400">Return Values</span></span>

- <span data-ttu-id="d2576-401">**NX_SUCCESS** (0X00) servern har skapats</span><span class="sxs-lookup"><span data-stu-id="d2576-401">**NX_SUCCESS** (0x00) Successful Server create</span></span>

- <span data-ttu-id="d2576-402">**NX_TFTP_POOL_ERROR** (0XC6) paketets pool har en paket storlek på mindre än 560 byte</span><span class="sxs-lookup"><span data-stu-id="d2576-402">**NX_TFTP_POOL_ERROR** (0xC6) Packet pool has packet size of less than 560 bytes</span></span>

- <span data-ttu-id="d2576-403">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-403">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-404">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-404">Allowed From</span></span>

<span data-ttu-id="d2576-405">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="d2576-405">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-406">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-406">Example</span></span>

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a><span data-ttu-id="d2576-407">nxd_tftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="d2576-407">nxd_tftp_server_delete</span></span>

<span data-ttu-id="d2576-408">Ta bort TFTP-server</span><span class="sxs-lookup"><span data-stu-id="d2576-408">Delete TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-409">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-409">Prototype</span></span>

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="d2576-410">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-410">Description</span></span>

<span data-ttu-id="d2576-411">Den här tjänsten tar bort en tidigare skapad TFTP-server.</span><span class="sxs-lookup"><span data-stu-id="d2576-411">This service deletes a previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-412">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-412">Input Parameters</span></span>

- <span data-ttu-id="d2576-413">**tftp_server_ptr** Pekare till kontroll block för TFTP-server.</span><span class="sxs-lookup"><span data-stu-id="d2576-413">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-414">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-414">Return Values</span></span>

- <span data-ttu-id="d2576-415">**NX_SUCCESS** (0X00) Server borttagning har slutförts</span><span class="sxs-lookup"><span data-stu-id="d2576-415">**NX_SUCCESS** (0x00) Successful Server delete</span></span>

- <span data-ttu-id="d2576-416">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-416">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-417">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-417">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-418">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-418">Allowed From</span></span>

<span data-ttu-id="d2576-419">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-419">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-420">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-420">Example</span></span>

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a><span data-ttu-id="d2576-421">nxd_tftp_server_start</span><span class="sxs-lookup"><span data-stu-id="d2576-421">nxd_tftp_server_start</span></span>

<span data-ttu-id="d2576-422">Starta TFTP-server</span><span class="sxs-lookup"><span data-stu-id="d2576-422">Start TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-423">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-423">Prototype</span></span>

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="d2576-424">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-424">Description</span></span>

<span data-ttu-id="d2576-425">Den här tjänsten startar den tidigare skapade TFTP-servern.</span><span class="sxs-lookup"><span data-stu-id="d2576-425">This service starts the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-426">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-426">Input Parameters</span></span>

- <span data-ttu-id="d2576-427">**tftp_server_ptr** Pekare till kontroll block för TFTP-server.</span><span class="sxs-lookup"><span data-stu-id="d2576-427">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-428">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-428">Return Values</span></span>

- <span data-ttu-id="d2576-429">**NX_SUCCESS** (0X00) Server start har slutförts</span><span class="sxs-lookup"><span data-stu-id="d2576-429">**NX_SUCCESS** (0x00) Successful Server start</span></span>

- <span data-ttu-id="d2576-430">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-430">NX_PTR_ERROR (0x16) Invalid pointer input .</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="d2576-431">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-431">Allowed From</span></span>

<span data-ttu-id="d2576-432">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="d2576-432">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-433">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-433">Example</span></span>

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a><span data-ttu-id="d2576-434">nxd_tftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="d2576-434">nxd_tftp_server_stop</span></span>

<span data-ttu-id="d2576-435">Stoppa TFTP-server</span><span class="sxs-lookup"><span data-stu-id="d2576-435">Stop TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d2576-436">Prototyp</span><span class="sxs-lookup"><span data-stu-id="d2576-436">Prototype</span></span>

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="d2576-437">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2576-437">Description</span></span>

<span data-ttu-id="d2576-438">Den här tjänsten stoppar den tidigare skapade TFTP-servern.</span><span class="sxs-lookup"><span data-stu-id="d2576-438">This service stops the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d2576-439">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="d2576-439">Input Parameters</span></span>

- <span data-ttu-id="d2576-440">**tftp_server_ptr** Pekare till kontroll block för TFTP-server.</span><span class="sxs-lookup"><span data-stu-id="d2576-440">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d2576-441">Retur värden</span><span class="sxs-lookup"><span data-stu-id="d2576-441">Return Values</span></span>

- <span data-ttu-id="d2576-442">**NX_SUCCESS** (0X00) Server stopp har slutförts</span><span class="sxs-lookup"><span data-stu-id="d2576-442">**NX_SUCCESS** (0x00) Successful Server stop</span></span>

- <span data-ttu-id="d2576-443">NX_PTR_ERROR (0x16) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="d2576-443">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d2576-444">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="d2576-444">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d2576-445">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="d2576-445">Allowed From</span></span>

<span data-ttu-id="d2576-446">Konversation</span><span class="sxs-lookup"><span data-stu-id="d2576-446">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d2576-447">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2576-447">Example</span></span>

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```