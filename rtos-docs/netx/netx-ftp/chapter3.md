---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX FTP Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX FTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826721"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a><span data-ttu-id="12190-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX FTP Services</span><span class="sxs-lookup"><span data-stu-id="12190-103">Chapter 3 - Description of Azure RTOS NetX FTP services</span></span>

<span data-ttu-id="12190-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX FTP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="12190-104">This chapter contains a description of all Azure RTOS NetX FTP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="12190-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="12190-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="12190-106">**nx_ftp_client_connect**: *Anslut till FTP-server*</span><span class="sxs-lookup"><span data-stu-id="12190-106">**nx_ftp_client_connect**: *Connect to FTP Server*</span></span>
- <span data-ttu-id="12190-107">**nx_ftp_client_create**: *skapa en instans av FTP-klienten*</span><span class="sxs-lookup"><span data-stu-id="12190-107">**nx_ftp_client_create**: *Create an FTP Client instance*</span></span>
- <span data-ttu-id="12190-108">**nx_ftp_client_delete**: *ta bort en instans av FTP-klienten*</span><span class="sxs-lookup"><span data-stu-id="12190-108">**nx_ftp_client_delete**: *Delete an FTP Client instance*</span></span>
- <span data-ttu-id="12190-109">**nx_ftp_client_directory_create**: *skapa en katalog på servern*</span><span class="sxs-lookup"><span data-stu-id="12190-109">**nx_ftp_client_directory_create**: *Create a directory on Server*</span></span>
- <span data-ttu-id="12190-110">**nx_ftp_client_directory_default_set**: *Ange standard katalog på servern*</span><span class="sxs-lookup"><span data-stu-id="12190-110">**nx_ftp_client_directory_default_set**: *Set default directory on Server*</span></span>
- <span data-ttu-id="12190-111">**nx_ftp_client_directory_delete**: *ta bort en katalog på servern*</span><span class="sxs-lookup"><span data-stu-id="12190-111">**nx_ftp_client_directory_delete**: *Delete a directory on Server*</span></span>
- <span data-ttu-id="12190-112">**nx_ftp_client_directory_listing_get**: *Hämta katalog lista från Server*</span><span class="sxs-lookup"><span data-stu-id="12190-112">**nx_ftp_client_directory_listing_get**: *Get directory listing from Server*</span></span>
- <span data-ttu-id="12190-113">**nx_ftp_client_directory_listing_continue**: *Fortsätt katalog listan från servern*</span><span class="sxs-lookup"><span data-stu-id="12190-113">**nx_ftp_client_directory_listing_continue**: *Continue directory listing from Server*</span></span>
- <span data-ttu-id="12190-114">**nx_ftp_client_disconnect**: *Koppla från FTP-server*</span><span class="sxs-lookup"><span data-stu-id="12190-114">**nx_ftp_client_disconnect**: *Disconnect from FTP Server*</span></span>
- <span data-ttu-id="12190-115">**nx_ftp_client_file_close**: *Stäng klient filen*</span><span class="sxs-lookup"><span data-stu-id="12190-115">**nx_ftp_client_file_close**: *Close Client file*</span></span>
- <span data-ttu-id="12190-116">**nx_ftp_client_file_delete**: *ta bort filen på servern*</span><span class="sxs-lookup"><span data-stu-id="12190-116">**nx_ftp_client_file_delete**: *Delete file on Server*</span></span>
- <span data-ttu-id="12190-117">**nx_ftp_client_file_open**: *Öppna klient filen*</span><span class="sxs-lookup"><span data-stu-id="12190-117">**nx_ftp_client_file_open**: *Open Client file*</span></span>
- <span data-ttu-id="12190-118">**nx_ftp_client_file_read**: *läsa från fil*</span><span class="sxs-lookup"><span data-stu-id="12190-118">**nx_ftp_client_file_read**: *Read from file*</span></span>
- <span data-ttu-id="12190-119">**nx_ftp_client_file_rename**: *Byt namn på filen på servern*</span><span class="sxs-lookup"><span data-stu-id="12190-119">**nx_ftp_client_file_rename**: *Rename file on Server*</span></span>
- <span data-ttu-id="12190-120">**nx_ftp_client_file_write**: *Skriv till fil*</span><span class="sxs-lookup"><span data-stu-id="12190-120">**nx_ftp_client_file_write**: *Write to file*</span></span>
- <span data-ttu-id="12190-121">**nx_ftp_server_create**: *Skapa FTP-server*</span><span class="sxs-lookup"><span data-stu-id="12190-121">**nx_ftp_server_create**: *Create FTP Server*</span></span>
- <span data-ttu-id="12190-122">**nx_ftp_server_delete**: *ta bort FTP-server*</span><span class="sxs-lookup"><span data-stu-id="12190-122">**nx_ftp_server_delete**: *Delete FTP Server*</span></span>
- <span data-ttu-id="12190-123">**nx_ftp_server_start**: *starta FTP-server*</span><span class="sxs-lookup"><span data-stu-id="12190-123">**nx_ftp_server_start**: *Start FTP Server*</span></span>
- <span data-ttu-id="12190-124">**nx_ftp_server_stop**: *Stoppa FTP-server*</span><span class="sxs-lookup"><span data-stu-id="12190-124">**nx_ftp_server_stop**: *Stop FTP Server*</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="12190-125">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="12190-125">nx_ftp_client_connect</span></span>

<span data-ttu-id="12190-126">Ansluta till en FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-126">Connect to an FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-127">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-127">Prototype</span></span>

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-128">Description</span></span>

<span data-ttu-id="12190-129">Den här tjänsten ansluter den tidigare skapade FTP-klienttjänsten till FTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="12190-129">This service connects the previously created FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-130">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-130">Input Parameters</span></span>

- <span data-ttu-id="12190-131">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-131">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-132">**server_ip**: IP-adressen för FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="12190-132">**server_ip**: IP address of FTP Server.</span></span>
- <span data-ttu-id="12190-133">**username**: klientens användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="12190-133">**username**: Client username for authentication.</span></span>
- <span data-ttu-id="12190-134">**lösen ord**: klient lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="12190-134">**password**: Client password for authentication.</span></span>
- <span data-ttu-id="12190-135">**wait_option**: anger hur länge tjänsten ska vänta på anslutning till FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-135">**wait_option**: Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="12190-136">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-136">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-137">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-137">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-138">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-139">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-139">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-140">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-140">Return Values</span></span>

- <span data-ttu-id="12190-141">**NX_SUCCESS**: (0X00) slutförd FTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="12190-141">**NX_SUCCESS**: (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="12190-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) fick inget 22X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="12190-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) fick inget 23X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="12190-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) fick inget 33X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="12190-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4)-klienten är redan ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="12190-146">NX_PTR_ERROR: (0x07) ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-146">NX_PTR_ERROR: (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="12190-147">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-147">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="12190-148">NX_IP_ADDRESS_ERROR: (0x21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="12190-148">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-149">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-149">Allowed From</span></span>

<span data-ttu-id="12190-150">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-150">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-151">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-151">Example</span></span>

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a><span data-ttu-id="12190-152">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="12190-152">nx_ftp_client_create</span></span>

<span data-ttu-id="12190-153">Skapa en instans av FTP-klienten</span><span class="sxs-lookup"><span data-stu-id="12190-153">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-154">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-154">Prototype</span></span>

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="12190-155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-155">Description</span></span>

<span data-ttu-id="12190-156">Den här tjänsten skapar en FTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="12190-156">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-157">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-157">Input Parameters</span></span>

- <span data-ttu-id="12190-158">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-158">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-159">**ftp_client_name**: namnet på FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-159">**ftp_client_name**: Name of FTP Client.</span></span>
- <span data-ttu-id="12190-160">**ip_ptr**: pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="12190-160">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="12190-161">**window_size**: annonserad fönster storlek för TCP-socket för denna FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="12190-161">**window_size**: Advertised window size for TCP socket of this FTP Client.</span></span>
- <span data-ttu-id="12190-162">**pool_ptr**: pekar mot standardpoolen för den här FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-162">**pool_ptr**: Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="12190-163">Observera att den minsta paket nytto lasten måste vara tillräckligt stor för att rymma fullständig sökväg och fil-eller katalog namnet.</span><span class="sxs-lookup"><span data-stu-id="12190-163">Note that the minimum packet payload must be large enough to hold complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-164">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-164">Return Values</span></span>

- <span data-ttu-id="12190-165">**NX_SUCCESS**: (0X00) lyckad FTP-klient skapa.</span><span class="sxs-lookup"><span data-stu-id="12190-165">**NX_SUCCESS**: (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="12190-166">NX_PTR_ERROR: (0x16) ogiltig FTP, IP-pekare eller adresspool.</span><span class="sxs-lookup"><span data-stu-id="12190-166">NX_PTR_ERROR: (0x16) Invalid FTP, IP pointer, or packet pool pointer.</span></span> <span data-ttu-id="12190-167">lösen ords pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-167">password pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-168">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-168">Allowed From</span></span>

<span data-ttu-id="12190-169">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="12190-169">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-170">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-170">Example</span></span>

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="12190-171">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="12190-171">nx_ftp_client_delete</span></span>

<span data-ttu-id="12190-172">Ta bort en FTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="12190-172">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-173">Prototype</span></span>

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="12190-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-174">Description</span></span>

<span data-ttu-id="12190-175">Den här tjänsten tar bort en instans av FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-175">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-176">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-176">Input Parameters</span></span>

- <span data-ttu-id="12190-177">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-177">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-178">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-178">Return Values</span></span>

- <span data-ttu-id="12190-179">**NX_SUCCESS**: (0X00) slutförd FTP-klient ta bort.</span><span class="sxs-lookup"><span data-stu-id="12190-179">**NX_SUCCESS**: (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="12190-180">**NX_FTP_NOT_DISCONNECTED**: (0XD4) FTP-klient ta bort fel.</span><span class="sxs-lookup"><span data-stu-id="12190-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP Client delete error.</span></span>
- <span data-ttu-id="12190-181">NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-181">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-182">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-182">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-183">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-183">Allowed From</span></span>

<span data-ttu-id="12190-184">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-185">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-185">Example</span></span>

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="12190-186">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="12190-186">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="12190-187">Skapa en katalog på en FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-187">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-188">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-188">Prototype</span></span>

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-189">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-189">Description</span></span>

<span data-ttu-id="12190-190">Den här tjänsten skapar den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-190">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-191">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-191">Input Parameters</span></span>

- <span data-ttu-id="12190-192">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-192">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-193">**directory_name**: namnet på den katalog som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="12190-193">**directory_name**: Name of directory to create.</span></span>
- <span data-ttu-id="12190-194">**wait_option**: anger hur länge tjänsten ska vänta på att FTP-katalogen ska skapas.</span><span class="sxs-lookup"><span data-stu-id="12190-194">**wait_option**: Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="12190-195">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-195">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-196">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-196">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-197">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-198">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-198">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-199">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-199">Return Values</span></span>

- <span data-ttu-id="12190-200">**NX_SUCCESS**: (0X00) lyckad FTP-katalog skapa.</span><span class="sxs-lookup"><span data-stu-id="12190-200">**NX_SUCCESS**: (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="12190-201">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="12190-203">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-203">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="12190-204">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-205">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-205">Allowed From</span></span>

<span data-ttu-id="12190-206">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-206">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-207">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-207">Example</span></span>

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="12190-208">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="12190-208">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="12190-209">Ange standard katalog på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-209">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-210">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-210">Prototype</span></span>

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-211">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-211">Description</span></span>

<span data-ttu-id="12190-212">Den här tjänsten anger standard katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-212">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="12190-213">Den här standard katalogen gäller endast för den här klientens anslutning.</span><span class="sxs-lookup"><span data-stu-id="12190-213">This default directory applies only to this client's connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-214">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-214">Input Parameters</span></span>

- <span data-ttu-id="12190-215">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-215">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-216">**directory_path**: namnet på den katalog Sök väg som ska anges.</span><span class="sxs-lookup"><span data-stu-id="12190-216">**directory_path**: Name of directory path to set.</span></span>
- <span data-ttu-id="12190-217">**wait_option**: definierar hur länge tjänsten ska vänta på katalog uppsättningen för FTP-katalogen.</span><span class="sxs-lookup"><span data-stu-id="12190-217">**wait_option**: Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="12190-218">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-218">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-219">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-219">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-220">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-221">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-221">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-222">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-222">Return Values</span></span>

- <span data-ttu-id="12190-223">**NX_SUCCESS**: (0X00) lyckad FTP standard uppsättning.</span><span class="sxs-lookup"><span data-stu-id="12190-223">**NX_SUCCESS**: (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="12190-224">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="12190-226">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-226">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="12190-227">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-227">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-228">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-228">Allowed From</span></span>

<span data-ttu-id="12190-229">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-230">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-230">Example</span></span>

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="12190-231">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="12190-231">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="12190-232">Ta bort katalog på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-232">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-233">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-233">Prototype</span></span>

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-234">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-234">Description</span></span>

<span data-ttu-id="12190-235">Den här tjänsten tar bort den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-235">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-236">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-236">Input Parameters</span></span>

- <span data-ttu-id="12190-237">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-237">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-238">**directory_name**: namnet på den katalog som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="12190-238">**directory_name**: Name of directory to delete.</span></span>
- <span data-ttu-id="12190-239">**wait_option**: anger hur länge tjänsten ska vänta på borttagning av FTP-katalogen.</span><span class="sxs-lookup"><span data-stu-id="12190-239">**wait_option**: Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="12190-240">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-240">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-241">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-241">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-242">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-243">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-243">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-244">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-244">Return Values</span></span>

- <span data-ttu-id="12190-245">**NX_SUCCESS**: (0X00) slutförd borttagning av FTP-katalogen.</span><span class="sxs-lookup"><span data-stu-id="12190-245">**NX_SUCCESS**: (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="12190-246">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="12190-248">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-248">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="12190-249">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-249">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-250">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-250">Allowed From</span></span>

<span data-ttu-id="12190-251">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-252">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-252">Example</span></span>

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="12190-253">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="12190-253">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="12190-254">Hämta katalog lista från FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-254">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-255">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-255">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-256">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-256">Description</span></span>

<span data-ttu-id="12190-257">Den här tjänsten hämtar innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-257">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="12190-258">Den tillhandahållna paket pekaren innehåller en eller flera katalog poster.</span><span class="sxs-lookup"><span data-stu-id="12190-258">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="12190-259">Varje post skiljs åt av en &lt; CR/LF \-kombination.</span><span class="sxs-lookup"><span data-stu-id="12190-259">Each entry is separated by a &lt;cr/lf\combination.</span></span> <span data-ttu-id="12190-260">***Nx_ftp_client_directory_listing_continue***: ska anropas för att slutföra hämtningen av katalogen.</span><span class="sxs-lookup"><span data-stu-id="12190-260">The ***nx_ftp_client_directory_listing_continue***: should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-261">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-261">Input Parameters</span></span>

- <span data-ttu-id="12190-262">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-262">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-263">**directory_name**: namnet på den katalog som innehållet ska hämtas från.</span><span class="sxs-lookup"><span data-stu-id="12190-263">**directory_name**: Name of directory to get contents of.</span></span>
- <span data-ttu-id="12190-264">**packet_ptr**: pekar mot mål paket pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-264">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="12190-265">Om det lyckas kommer paketets nytto last att innehålla en eller flera katalog poster.</span><span class="sxs-lookup"><span data-stu-id="12190-265">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="12190-266">**wait_option**: definierar hur länge tjänsten ska vänta på listan över FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="12190-266">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="12190-267">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-267">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-268">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-268">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-269">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-270">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-270">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-271">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-271">Return Values</span></span>

- <span data-ttu-id="12190-272">**NX_SUCCESS**: (0x00) lista över lyckade FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="12190-272">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="12190-273">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-274">**NX_NOT_ENABLED**: (0X14) service (IPv6) är inte aktive rad</span><span class="sxs-lookup"><span data-stu-id="12190-274">**NX_NOT_ENABLED**: (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="12190-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) fick inget 1xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="12190-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="12190-277">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-277">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-278">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-278">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-279">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-279">Allowed From</span></span>

<span data-ttu-id="12190-280">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-281">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-281">Example</span></span>

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="12190-282">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="12190-282">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="12190-283">Fortsätt katalog listan från FTP-servern</span><span class="sxs-lookup"><span data-stu-id="12190-283">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-284">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-284">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-285">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-285">Description</span></span>

<span data-ttu-id="12190-286">Den här tjänsten fortsätter att hämta innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-286">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="12190-287">Det bör ha föregås av ett anrop till ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="12190-287">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="12190-288">Om det lyckas kommer den tillhandahållna paket pekaren innehålla en eller flera katalog poster.</span><span class="sxs-lookup"><span data-stu-id="12190-288">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="12190-289">Den här rutinen ska anropas tills en NX_FTP_END_OF_LISTING-status tas emot.</span><span class="sxs-lookup"><span data-stu-id="12190-289">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-290">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-290">Input Parameters</span></span>

- <span data-ttu-id="12190-291">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-291">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-292">**packet_ptr**: pekar mot mål paket pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-292">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="12190-293">Om det lyckas innehåller paketets nytto Last en eller flera katalog poster, avgränsade med &lt; CR/LF &gt; .</span><span class="sxs-lookup"><span data-stu-id="12190-293">If successful, the packet payload will contain one or more directory entries, separated by a &lt;cr/lf&gt;.</span></span>
- <span data-ttu-id="12190-294">**wait_option**: definierar hur länge tjänsten ska vänta på listan över FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="12190-294">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="12190-295">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-295">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-296">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-296">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-297">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-298">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-298">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-299">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-299">Return Values</span></span>

- <span data-ttu-id="12190-300">**NX_SUCCESS**: (0x00) lista över lyckade FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="12190-300">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="12190-301">**NX_FTP_END_OF_LISTING**: (0XD8) inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="12190-301">**NX_FTP_END_OF_LISTING**: (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="12190-302">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="12190-304">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-304">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-305">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-305">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-306">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-306">Allowed From</span></span>

<span data-ttu-id="12190-307">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-308">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-308">Example</span></span>

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="12190-309">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="12190-309">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="12190-310">Koppla från FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-310">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-311">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-311">Prototype</span></span>

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-312">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-312">Description</span></span>

<span data-ttu-id="12190-313">Den här tjänsten kopplar från en tidigare upprättad FTP-server-anslutning till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-313">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-314">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-314">Input Parameters</span></span>

- <span data-ttu-id="12190-315">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-315">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-316">**wait_option**: anger hur länge tjänsten ska vänta tills FTP-klienten kopplas från.</span><span class="sxs-lookup"><span data-stu-id="12190-316">**wait_option**: Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="12190-317">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-317">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-318">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-318">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-319">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-320">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-321">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-321">Return Values</span></span>

- <span data-ttu-id="12190-322">**NX_SUCCESS**: (0X00) lyckad FTP-från koppling.</span><span class="sxs-lookup"><span data-stu-id="12190-322">**NX_SUCCESS**: (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="12190-323">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="12190-325">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-325">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-326">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-327">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-327">Allowed From</span></span>

<span data-ttu-id="12190-328">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-329">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-329">Example</span></span>

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="12190-330">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="12190-330">nx_ftp_client_file_close</span></span>

<span data-ttu-id="12190-331">Stäng klient filen</span><span class="sxs-lookup"><span data-stu-id="12190-331">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-332">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-332">Prototype</span></span>

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-333">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-333">Description</span></span>

<span data-ttu-id="12190-334">Den här tjänsten stänger en tidigare öppnad fil på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="12190-334">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-335">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-335">Input Parameters</span></span>

- <span data-ttu-id="12190-336">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-336">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-337">**wait_option**: anger hur länge tjänsten ska vänta på att FTP-klientprogramvaran stängs.</span><span class="sxs-lookup"><span data-stu-id="12190-337">**wait_option**: Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="12190-338">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-338">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-339">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-339">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-340">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-341">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-341">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-342">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-342">Return Values</span></span>

- <span data-ttu-id="12190-343">**NX_SUCCESS**: (0X00) lyckad FTP-fil stängs.</span><span class="sxs-lookup"><span data-stu-id="12190-343">**NX_SUCCESS**: (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="12190-344">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-345">**NX_FTP_NOT_OPEN (0xD5)**: filen är inte öppen. Det går inte att stänga den</span><span class="sxs-lookup"><span data-stu-id="12190-345">**NX_FTP_NOT_OPEN (0xD5)**: File not open; cannot close it</span></span>
- <span data-ttu-id="12190-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="12190-347">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-347">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-348">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-348">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-349">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-349">Allowed From</span></span>

<span data-ttu-id="12190-350">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-351">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-351">Example</span></span>

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="12190-352">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="12190-352">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="12190-353">Ta bort fil på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-353">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-354">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-354">Prototype</span></span>

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-355">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-355">Description</span></span>

<span data-ttu-id="12190-356">Den här tjänsten tar bort den angivna filen på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="12190-356">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-357">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-357">Input Parameters</span></span>

- <span data-ttu-id="12190-358">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-358">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-359">**file_name**: namnet på filen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="12190-359">**file_name**: Name of file to delete.</span></span>
- <span data-ttu-id="12190-360">**wait_option**: anger hur länge tjänsten ska vänta på att ta bort FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-360">**wait_option**: Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="12190-361">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-361">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-362">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-362">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-363">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-364">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-364">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-365">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-365">Return Values</span></span>

- <span data-ttu-id="12190-366">**NX_SUCCESS**: (0X00) lyckad FTP-fil borttagning.</span><span class="sxs-lookup"><span data-stu-id="12190-366">**NX_SUCCESS**: (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="12190-367">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="12190-369">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-369">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-370">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-371">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-371">Allowed From</span></span>

<span data-ttu-id="12190-372">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-373">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-373">Example</span></span>

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="12190-374">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="12190-374">nx_ftp_client_file_open</span></span>

<span data-ttu-id="12190-375">Öppnar filen på FTP-servern</span><span class="sxs-lookup"><span data-stu-id="12190-375">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-376">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-376">Prototype</span></span>

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-377">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-377">Description</span></span>

<span data-ttu-id="12190-378">Den här tjänsten öppnar den angivna filen – för att läsa eller skriva – på FTP-servern som tidigare var ansluten till den angivna klient instansen.</span><span class="sxs-lookup"><span data-stu-id="12190-378">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-379">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-379">Input Parameters</span></span>

- <span data-ttu-id="12190-380">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-380">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-381">**file_name**: namnet på filen som ska öppnas.</span><span class="sxs-lookup"><span data-stu-id="12190-381">**file_name**: Name of file to open.</span></span>
- <span data-ttu-id="12190-382">**open_type**: antingen **NX_FTP_OPEN_FOR_READ** eller **NX_FTP_OPEN_FOR_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="12190-382">**open_type**: Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="12190-383">**wait_option**: anger hur länge tjänsten ska vänta på att FTP-klienttjänsten är öppen.</span><span class="sxs-lookup"><span data-stu-id="12190-383">**wait_option**: Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="12190-384">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-384">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-385">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-385">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-386">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-387">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-387">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-388">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-388">Return Values</span></span>

- <span data-ttu-id="12190-389">**NX_SUCCESS**: (0X00) lyckad FTP-fil öppen.</span><span class="sxs-lookup"><span data-stu-id="12190-389">**NX_SUCCESS**: (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="12190-390">**NX_OPTION_ERROR**: (0X0a) ogiltig öppen typ.</span><span class="sxs-lookup"><span data-stu-id="12190-390">**NX_OPTION_ERROR**: (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="12190-391">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-392">**NX_FTP_NOT_CLOSED**: (0XD6) FTP-klienten har redan öppnats.</span><span class="sxs-lookup"><span data-stu-id="12190-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="12190-393">**NX_NO_FREE_PORTS**: (0x45) det finns inga tillgängliga TCP-portar att tilldela</span><span class="sxs-lookup"><span data-stu-id="12190-393">**NX_NO_FREE_PORTS**: (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="12190-394">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-394">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-395">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-395">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-396">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-396">Allowed From</span></span>

<span data-ttu-id="12190-397">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-398">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-398">Example</span></span>

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="12190-399">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="12190-399">nx_ftp_client_file_read</span></span>

<span data-ttu-id="12190-400">Läsa från fil</span><span class="sxs-lookup"><span data-stu-id="12190-400">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-401">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-401">Prototype</span></span>

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-402">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-402">Description</span></span>

<span data-ttu-id="12190-403">Den här tjänsten läser ett paket från en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="12190-403">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="12190-404">Den bör anropas upprepade gånger tills en status för NX_FTP_END_OF_FILE tas emot.</span><span class="sxs-lookup"><span data-stu-id="12190-404">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="12190-405">Observera att anroparen inte allokerar ett paket för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-405">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="12190-406">Du behöver bara ange en pekare till en paket pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-406">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="12190-407">Den här tjänsten kommer att uppdatera paket pekaren så att den pekar på ett paket som hämtats från socket Receive-kön.</span><span class="sxs-lookup"><span data-stu-id="12190-407">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="12190-408">Om statusen lyckades returneras, innebär det att det fanns ett tillgängligt paket och att det är anroparens ansvar att frigöra paketet när det är klart.</span><span class="sxs-lookup"><span data-stu-id="12190-408">If a successful status is returned, that means there was a packet available, and it is the caller's responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="12190-409">Om en status som inte är noll (antingen en fel status eller NX_FTP_END_OF_FILE) returneras, frigörs inte paketet av anroparen.</span><span class="sxs-lookup"><span data-stu-id="12190-409">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="12190-410">Annars genereras ett fel när paket pekaren är NULL.</span><span class="sxs-lookup"><span data-stu-id="12190-410">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-411">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-411">Input Parameters</span></span>

- <span data-ttu-id="12190-412">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-412">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-413">**packet_ptr**: pekare till målet för data paket pekaren som hämtades från kön.</span><span class="sxs-lookup"><span data-stu-id="12190-413">**packet_ptr**: Pointer to destination for the data packet pointer retrieved from the queue.</span></span> <span data-ttu-id="12190-414">Om det lyckas innehåller paket data en del av eller hela filen.</span><span class="sxs-lookup"><span data-stu-id="12190-414">If successful, the packet data contains some or all of the file.</span></span>
- <span data-ttu-id="12190-415">**wait_option**: anger hur länge tjänsten ska vänta på att FTP-klientdatorn läses.</span><span class="sxs-lookup"><span data-stu-id="12190-415">**wait_option**: Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="12190-416">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-416">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-417">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-417">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-418">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-419">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-419">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-420">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-420">Return Values</span></span>

- <span data-ttu-id="12190-421">**NX_SUCCESS**: (0X00) lyckad FTP-fil har lästs.</span><span class="sxs-lookup"><span data-stu-id="12190-421">**NX_SUCCESS**: (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="12190-422">**NX_FTP_NOT_OPEN**: (0XD5) FTP-klienten är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="12190-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="12190-423">**NX_FTP_END_OF_FILE**: (0xD7) fil villkoret är slut.</span><span class="sxs-lookup"><span data-stu-id="12190-423">**NX_FTP_END_OF_FILE**: (0xD7) End of file condition.</span></span>
- <span data-ttu-id="12190-424">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-424">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-425">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-425">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-426">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-426">Allowed From</span></span>

<span data-ttu-id="12190-427">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-428">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-428">Example</span></span>

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

        /* Check status.  */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }
        else
        {
            /* Release packet when done with it. */
            nx_packet_release(my_packet);
        }

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="12190-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="12190-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="12190-430">Byt namn på fil på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-431">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-431">Prototype</span></span>

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-432">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-432">Description</span></span>

<span data-ttu-id="12190-433">Den här tjänsten byter namn på en fil på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="12190-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-434">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-434">Input Parameters</span></span>

- <span data-ttu-id="12190-435">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-435">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-436">**filename**: aktuellt fil namn.</span><span class="sxs-lookup"><span data-stu-id="12190-436">**filename**: Current name of file.</span></span>
- <span data-ttu-id="12190-437">**new_filename**: nytt namn på filen.</span><span class="sxs-lookup"><span data-stu-id="12190-437">**new_filename**: New name for file.</span></span>
- <span data-ttu-id="12190-438">**wait_option**: anger hur länge tjänsten ska vänta på att byta namn på FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="12190-438">**wait_option**: Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="12190-439">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-440">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-440">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-441">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-442">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-442">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-443">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-443">Return Values</span></span>

- <span data-ttu-id="12190-444">**NX_SUCCESS**: (0X00) lyckades FTP-filens namn.</span><span class="sxs-lookup"><span data-stu-id="12190-444">**NX_SUCCESS**: (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="12190-445">**NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="12190-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="12190-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) fick inte svar på 3xx (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="12190-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="12190-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="12190-448">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-448">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-449">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-449">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-450">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-450">Allowed From</span></span>

<span data-ttu-id="12190-451">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-452">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-452">Example</span></span>

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="12190-453">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="12190-453">nx_ftp_client_file_write</span></span>

<span data-ttu-id="12190-454">Skriv till fil</span><span class="sxs-lookup"><span data-stu-id="12190-454">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-455">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-455">Prototype</span></span>

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="12190-456">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-456">Description</span></span>

<span data-ttu-id="12190-457">Den här tjänsten skriver ett data paket till den tidigare öppnade filen på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="12190-457">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-458">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-458">Input Parameters</span></span>

- <span data-ttu-id="12190-459">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-459">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-460">**packet_ptr**: paket pekare som innehåller data som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="12190-460">**packet_ptr**: Packet pointer containing data to write.</span></span>
- <span data-ttu-id="12190-461">**wait_option**: anger hur länge tjänsten ska vänta på att FTP-klientdatorn skriver.</span><span class="sxs-lookup"><span data-stu-id="12190-461">**wait_option**: Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="12190-462">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="12190-462">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="12190-463">**timeout-värde**: (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="12190-463">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="12190-464">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="12190-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="12190-465">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="12190-465">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-466">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-466">Return Values</span></span>

- <span data-ttu-id="12190-467">**NX_SUCCESS**: (0X00) lyckad FTP-fil skrivning.</span><span class="sxs-lookup"><span data-stu-id="12190-467">**NX_SUCCESS**: (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="12190-468">**NX_FTP_NOT_OPEN**: (0XD5) FTP-klienten är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="12190-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="12190-469">NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-469">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-470">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-470">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-471">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-471">Allowed From</span></span>

<span data-ttu-id="12190-472">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-473">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-473">Example</span></span>

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="12190-474">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="12190-474">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="12190-475">Aktivera eller inaktivera passivt överförings läge</span><span class="sxs-lookup"><span data-stu-id="12190-475">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-476">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-476">Prototype</span></span>

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="12190-477">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-477">Description</span></span>

<span data-ttu-id="12190-478">Den här tjänsten aktiverar passivt överförings läge om passive_mode_enabled indatatypen är inställd på NX_TRUE på en tidigare skapad FTP-serverinstans, så att efterföljande anrop till läsa eller skriva filer (RETR, lagr) eller hämtning av en katalog lista (NLST) görs i överförings läge.</span><span class="sxs-lookup"><span data-stu-id="12190-478">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="12190-479">Om du vill inaktivera överföring i passivt läge och återgå till standard beteendet för aktivt överförings läge, anropar du den här funktionen med passive_mode_enabled indatamängden för att NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="12190-479">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-480">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-480">Input Parameters</span></span>

- <span data-ttu-id="12190-481">**ftp_client_ptr**: pekar mot FTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="12190-481">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="12190-482">**passive_mode_enabled**:</span><span class="sxs-lookup"><span data-stu-id="12190-482">**passive_mode_enabled**:</span></span>
  - <span data-ttu-id="12190-483">Om värdet är NX_TRUE aktive ras passivt läge.</span><span class="sxs-lookup"><span data-stu-id="12190-483">If set to NX_TRUE, passive mode is enabled.</span></span>
  - <span data-ttu-id="12190-484">Om värdet är NX_FALSE inaktive ras passivt läge.</span><span class="sxs-lookup"><span data-stu-id="12190-484">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-485">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-485">Return Values</span></span>

- <span data-ttu-id="12190-486">**NX_SUCCESS**: (0X00) lyckades passivt läge.</span><span class="sxs-lookup"><span data-stu-id="12190-486">**NX_SUCCESS**: (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="12190-487">NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-487">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-488">NX_INVALID_PARAMETERS: (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="12190-488">NX_INVALID_PARAMETERS: (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-489">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-489">Allowed From</span></span>

<span data-ttu-id="12190-490">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-491">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-491">Example</span></span>

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="12190-492">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="12190-492">nx_ftp_server_create</span></span>

<span data-ttu-id="12190-493">Skapa FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-493">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-494">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-494">Prototype</span></span>

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="12190-495">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-495">Description</span></span>

<span data-ttu-id="12190-496">Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="12190-496">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="12190-497">Observera att FTP-servern måste startas med ett anrop till ***nx_ftp_server_start*** för att det ska kunna starta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="12190-497">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-498">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-498">Input Parameters</span></span>

- <span data-ttu-id="12190-499">**ftp_server_ptr**: pekare till FTP Server Control Block.</span><span class="sxs-lookup"><span data-stu-id="12190-499">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="12190-500">**ftp_server_name**: namnet på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="12190-500">**ftp_server_name**: Name of FTP Server.</span></span>
- <span data-ttu-id="12190-501">**ip_ptr**: pekar mot associerad netx IP-instans.</span><span class="sxs-lookup"><span data-stu-id="12190-501">**ip_ptr**: Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="12190-502">Obs! det kan bara finnas en FTP-server för en IP-instans.</span><span class="sxs-lookup"><span data-stu-id="12190-502">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="12190-503">**media_ptr**: pekar mot associerad FileX Media-instans.</span><span class="sxs-lookup"><span data-stu-id="12190-503">**media_ptr**: Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="12190-504">**stack_ptr**: pekar på minne för den interna FTP-serverns stack-tråd.</span><span class="sxs-lookup"><span data-stu-id="12190-504">**stack_ptr**: Pointer to memory for the internal FTP Server thread's stack area.</span></span>
- <span data-ttu-id="12190-505">**stack_size**: storleken på det stack områden som anges av *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="12190-505">**stack_size**: Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="12190-506">**pool_ptr**: pekar mot standard netx.</span><span class="sxs-lookup"><span data-stu-id="12190-506">**pool_ptr**: Pointer to default NetX packet pool.</span></span> <span data-ttu-id="12190-507">Observera nytto Last storleken för paket i poolen måste vara tillräckligt stor för att rymma största fil namn/sökväg.</span><span class="sxs-lookup"><span data-stu-id="12190-507">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="12190-508">**ftp_login**: funktions pekare till programmets inloggnings funktion.</span><span class="sxs-lookup"><span data-stu-id="12190-508">**ftp_login**: Function pointer to application's login function.</span></span> <span data-ttu-id="12190-509">Den här funktionen anges användar namn och lösen ord från klienten som begär en anslutning.</span><span class="sxs-lookup"><span data-stu-id="12190-509">This function is supplied the username and password from the Client requesting a connection.</span></span> <span data-ttu-id="12190-510">Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="12190-510">If this is valid, the application's login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="12190-511">**ftp_logout**: funktions pekare till programmets utloggnings funktion.</span><span class="sxs-lookup"><span data-stu-id="12190-511">**ftp_logout**: Function pointer to application's logout function.</span></span> <span data-ttu-id="12190-512">Den här funktionen anges användar namn och lösen ord från klienten som begär en från koppling.</span><span class="sxs-lookup"><span data-stu-id="12190-512">This function is supplied the username and password from the Client requesting a disconnection.</span></span> <span data-ttu-id="12190-513">Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="12190-513">If this is valid, the application's login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-514">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-514">Return Values</span></span>

- <span data-ttu-id="12190-515">**NX_SUCCESS**: (0X00) lyckad FTP-server skapa.</span><span class="sxs-lookup"><span data-stu-id="12190-515">**NX_SUCCESS**: (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="12190-516">NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-516">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-517">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-517">Allowed From</span></span>

<span data-ttu-id="12190-518">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="12190-518">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-519">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-519">Example</span></span>

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="12190-520">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="12190-520">nx_ftp_server_delete</span></span>

<span data-ttu-id="12190-521">Ta bort FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-521">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-522">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-522">Prototype</span></span>

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="12190-523">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-523">Description</span></span>

<span data-ttu-id="12190-524">Den här tjänsten tar bort en instans av en tidigare skapad FTP-server.</span><span class="sxs-lookup"><span data-stu-id="12190-524">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-525">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-525">Input Parameters</span></span>

- <span data-ttu-id="12190-526">**ftp_server_ptr**: pekare till FTP Server Control Block.</span><span class="sxs-lookup"><span data-stu-id="12190-526">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-527">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-527">Return Values</span></span>

- <span data-ttu-id="12190-528">**NX_SUCCESS**: (0X00) slutförd borttagning av FTP-server.</span><span class="sxs-lookup"><span data-stu-id="12190-528">**NX_SUCCESS**: (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="12190-529">NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-529">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-530">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-530">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-531">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-531">Allowed From</span></span>

<span data-ttu-id="12190-532">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-533">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-533">Example</span></span>

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="12190-534">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="12190-534">nx_ftp_server_start</span></span>

<span data-ttu-id="12190-535">Starta FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-535">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-536">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-536">Prototype</span></span>

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="12190-537">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-537">Description</span></span>

<span data-ttu-id="12190-538">Den här tjänsten startar en instans av en tidigare skapad FTP-server.</span><span class="sxs-lookup"><span data-stu-id="12190-538">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-539">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-539">Input Parameters</span></span>

- <span data-ttu-id="12190-540">**ftp_server_ptr**: pekare till FTP Server Control Block.</span><span class="sxs-lookup"><span data-stu-id="12190-540">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-541">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-541">Return Values</span></span>

- <span data-ttu-id="12190-542">**NX_SUCCESS**: (0X00) lyckad FTP-server startar.</span><span class="sxs-lookup"><span data-stu-id="12190-542">**NX_SUCCESS**: (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="12190-543">NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-543">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-544">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-544">Allowed From</span></span>

<span data-ttu-id="12190-545">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="12190-545">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-546">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-546">Example</span></span>

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="12190-547">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="12190-547">nx_ftp_server_stop</span></span>

<span data-ttu-id="12190-548">Stoppa FTP-Server</span><span class="sxs-lookup"><span data-stu-id="12190-548">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="12190-549">Prototyp</span><span class="sxs-lookup"><span data-stu-id="12190-549">Prototype</span></span>

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="12190-550">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12190-550">Description</span></span>

<span data-ttu-id="12190-551">Den här tjänsten stoppar en instans av en tidigare skapad och startad FTP-server.</span><span class="sxs-lookup"><span data-stu-id="12190-551">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="12190-552">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="12190-552">Input Parameters</span></span>

- <span data-ttu-id="12190-553">**ftp_server_ptr**: pekare till FTP Server Control Block.</span><span class="sxs-lookup"><span data-stu-id="12190-553">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="12190-554">Retur värden</span><span class="sxs-lookup"><span data-stu-id="12190-554">Return Values</span></span>

- <span data-ttu-id="12190-555">**NX_SUCCESS**: (0x00) en slutförd FTP-server stoppas.</span><span class="sxs-lookup"><span data-stu-id="12190-555">**NX_SUCCESS**: (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="12190-556">NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="12190-556">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="12190-557">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="12190-557">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="12190-558">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="12190-558">Allowed From</span></span>

<span data-ttu-id="12190-559">Konversation</span><span class="sxs-lookup"><span data-stu-id="12190-559">Threads</span></span>

### <a name="example"></a><span data-ttu-id="12190-560">Exempel</span><span class="sxs-lookup"><span data-stu-id="12190-560">Example</span></span>

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
