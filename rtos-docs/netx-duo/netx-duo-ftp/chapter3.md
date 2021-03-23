---
title: Kapitel 3 – Beskrivning av FTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX FTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825980"
---
# <a name="chapter-3---description-of-ftp-services"></a><span data-ttu-id="ab21d-103">Kapitel 3 – Beskrivning av FTP-tjänster</span><span class="sxs-lookup"><span data-stu-id="ab21d-103">Chapter 3 - Description of FTP services</span></span>

<span data-ttu-id="ab21d-104">Det här kapitlet innehåller en beskrivning av alla NetX FTP-tjänster (visas nedan) i alfabetisk ordning (förutom där IPv4-och IPv6-motsvarigheter till samma tjänst paras ihop).</span><span class="sxs-lookup"><span data-stu-id="ab21d-104">This chapter contains a description of all NetX FTP services (listed below) in alphabetic order (except where IPv4 and IPv6 equivalents of the same service are paired together).</span></span>

> [!NOTE]
> <span data-ttu-id="ab21d-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="ab21d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="ab21d-106">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ab21d-106">nx_ftp_client_connect</span></span>

<span data-ttu-id="ab21d-107">Ansluta till en FTP-server via IPv4</span><span class="sxs-lookup"><span data-stu-id="ab21d-107">Connect to an FTP Server over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-108">Prototype</span></span>

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-109">Description</span></span>

<span data-ttu-id="ab21d-110">Den här tjänsten ansluter den tidigare skapade FTP-NetX till FTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-110">This service connects the previously created NetX FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-111">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-111">Input Parameters</span></span>

- <span data-ttu-id="ab21d-112">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-112">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-113">**server_ip** IP-adressen för FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="ab21d-113">**server_ip** IP address of FTP Server.</span></span>
- <span data-ttu-id="ab21d-114">**användar namn** Klientens användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="ab21d-114">**username** Client username for authentication.</span></span>
- <span data-ttu-id="ab21d-115">**lösen ord** Klient lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="ab21d-115">**password** Client password for authentication.</span></span>
- <span data-ttu-id="ab21d-116">**wait_option** Definierar hur länge tjänsten ska vänta på anslutning till FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-116">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="ab21d-117">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-117">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-118">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-118">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-119">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-120">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-120">Return Values</span></span>

- <span data-ttu-id="ab21d-121">**NX_SUCCESS** (0X00) slutförd FTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="ab21d-121">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="ab21d-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) fick inget 22X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="ab21d-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) fick inget 23X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="ab21d-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) fick inget 33X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="ab21d-125">**NX_FTP_NOT_DISCONNECTED** (0xD4)-klienten är redan ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="ab21d-126">NX_PTR_ERROR (0x07) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab21d-126">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="ab21d-127">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-127">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ab21d-128">NX_IP_ADDRESS_ERROR (0x21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="ab21d-128">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-129">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-129">Allowed From</span></span>

<span data-ttu-id="ab21d-130">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-130">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-131">Example</span></span>

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="ab21d-132">Se även</span><span class="sxs-lookup"><span data-stu-id="ab21d-132">See Also</span></span>

<span data-ttu-id="ab21d-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ab21d-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span></span>

## <a name="nxd_ftp_client_connect"></a><span data-ttu-id="ab21d-134">nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ab21d-134">nxd_ftp_client_connect</span></span>

<span data-ttu-id="ab21d-135">Ansluta till en FTP-server med IPv6-stöd</span><span class="sxs-lookup"><span data-stu-id="ab21d-135">Connect to an FTP Server with IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-136">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-136">Prototype</span></span>

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-137">Description</span></span>

<span data-ttu-id="ab21d-138">Den här tjänsten ansluter den tidigare skapade NetX Duo FTP-serverinstansen till FTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-138">This service connects the previously created NetX Duo FTP Client instance to the FTP Server at the supplied IP address.</span></span> <span data-ttu-id="ab21d-139">Både IPv4-och IPv6-nätverk stöds.</span><span class="sxs-lookup"><span data-stu-id="ab21d-139">Both IPv4 and IPv6 networks are supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-140">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-140">Input Parameters</span></span>

- <span data-ttu-id="ab21d-141">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-141">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-142">**server_ipduo** IP-adressen för FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="ab21d-142">**server_ipduo** IP address of the FTP Server.</span></span>
- <span data-ttu-id="ab21d-143">**användar namn** Klientens användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="ab21d-143">**username** Client username for authentication.</span></span>
- <span data-ttu-id="ab21d-144">**lösen ord** Klient lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="ab21d-144">**password** Client password for authentication.</span></span>
- <span data-ttu-id="ab21d-145">**wait_option** Definierar hur länge tjänsten ska vänta på anslutning till FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-145">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="ab21d-146">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-146">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-147">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-147">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-148">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-149">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-149">Return Values</span></span>

- <span data-ttu-id="ab21d-150">**NX_SUCCESS** (0X00) slutförd FTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="ab21d-150">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="ab21d-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) fick inget 22X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="ab21d-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) fick inget 23X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="ab21d-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) fick inget 33X-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="ab21d-154">**NX_FTP_NOT_DISCONNECTED** -klienten (0xD4) är redan ansluten</span><span class="sxs-lookup"><span data-stu-id="ab21d-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected</span></span>
- <span data-ttu-id="ab21d-155">NX_PTR_ERROR (0x07) ogiltigt nedpilens Inout.</span><span class="sxs-lookup"><span data-stu-id="ab21d-155">NX_PTR_ERROR (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="ab21d-156">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-156">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ab21d-157">NX_IP_ADDRESS_ERROR (0x21) ogiltig IP-adress.</span><span class="sxs-lookup"><span data-stu-id="ab21d-157">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-158">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-158">Allowed From</span></span>

<span data-ttu-id="ab21d-159">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-159">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-160">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-160">Example</span></span>

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="ab21d-161">Se även</span><span class="sxs-lookup"><span data-stu-id="ab21d-161">See Also</span></span>

<span data-ttu-id="ab21d-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ab21d-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span></span>

## <a name="nx_ftp_client_create"></a><span data-ttu-id="ab21d-163">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="ab21d-163">nx_ftp_client_create</span></span>

<span data-ttu-id="ab21d-164">Skapa en instans av FTP-klienten</span><span class="sxs-lookup"><span data-stu-id="ab21d-164">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-165">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-165">Prototype</span></span>

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ab21d-166">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-166">Description</span></span>

<span data-ttu-id="ab21d-167">Den här tjänsten skapar en FTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="ab21d-167">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-168">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-168">Input Parameters</span></span>

- <span data-ttu-id="ab21d-169">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-169">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-170">**ftp_client_name** Namn på FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-170">**ftp_client_name** Name of FTP Client.</span></span>
- <span data-ttu-id="ab21d-171">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-171">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ab21d-172">**window_size** Annonserad fönster storlek för TCP-Sockets för den här FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-172">**window_size** Advertised window size for TCP sockets of this FTP Client.</span></span>
- <span data-ttu-id="ab21d-173">**pool_ptr** Pekar på den här FTP-klientens standardpool för paket.</span><span class="sxs-lookup"><span data-stu-id="ab21d-173">**pool_ptr** Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="ab21d-174">Observera att den minsta paket nytto lasten måste vara tillräckligt stor för att rymma fullständig sökväg och fil-eller katalog namnet.</span><span class="sxs-lookup"><span data-stu-id="ab21d-174">Note that the minimum packet payload must be large enough to hold  complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-175">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-175">Return Values</span></span>

- <span data-ttu-id="ab21d-176">**NX_SUCCESS** (0X00) slutförd FTP-klient skapa.</span><span class="sxs-lookup"><span data-stu-id="ab21d-176">**NX_SUCCESS** (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="ab21d-177">NX_PTR_ERROR (0x07) ogiltig pekare inmatade.</span><span class="sxs-lookup"><span data-stu-id="ab21d-177">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-178">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-178">Allowed From</span></span>

<span data-ttu-id="ab21d-179">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="ab21d-179">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-180">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-180">Example</span></span>

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="ab21d-181">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="ab21d-181">nx_ftp_client_delete</span></span>

<span data-ttu-id="ab21d-182">Ta bort en FTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="ab21d-182">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-183">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-183">Prototype</span></span>

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="ab21d-184">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-184">Description</span></span>

<span data-ttu-id="ab21d-185">Den här tjänsten tar bort en instans av FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-185">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-186">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-186">Input Parameters</span></span>

- <span data-ttu-id="ab21d-187">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-187">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-188">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-188">Return Values</span></span>

- <span data-ttu-id="ab21d-189">**NX_SUCCESS** (0X00) slutförd FTP-klient ta bort.</span><span class="sxs-lookup"><span data-stu-id="ab21d-189">**NX_SUCCESS** (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="ab21d-190">**NX_FTP_NOT_DISCONNECTED** (0XD4) FTP-klienten är inte frånkopplad</span><span class="sxs-lookup"><span data-stu-id="ab21d-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP client not disconnected</span></span>
- <span data-ttu-id="ab21d-191">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-191">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-192">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-192">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-193">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-193">Allowed From</span></span>

<span data-ttu-id="ab21d-194">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-194">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-195">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-195">Example</span></span>

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="ab21d-196">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="ab21d-196">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="ab21d-197">Skapa en katalog på en FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-197">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-198">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-198">Prototype</span></span>

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-199">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-199">Description</span></span>

<span data-ttu-id="ab21d-200">Den här tjänsten skapar den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-200">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-201">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-201">Input Parameters</span></span>

- <span data-ttu-id="ab21d-202">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-202">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-203">**directory_name** Namnet på den katalog som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="ab21d-203">**directory_name** Name of directory to create.</span></span>
- <span data-ttu-id="ab21d-204">**wait_option** Definierar hur länge tjänsten ska vänta på att FTP-katalogen ska skapas.</span><span class="sxs-lookup"><span data-stu-id="ab21d-204">**wait_option** Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="ab21d-205">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-205">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-206">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-206">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-207">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-208">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-208">Return Values</span></span>

- <span data-ttu-id="ab21d-209">**NX_SUCCESS** (0X00) slutförd FTP-katalog skapa.</span><span class="sxs-lookup"><span data-stu-id="ab21d-209">**NX_SUCCESS** (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="ab21d-210">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-212">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-212">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-213">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-213">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-214">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-214">Allowed From</span></span>

<span data-ttu-id="ab21d-215">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-216">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-216">Example</span></span>

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="ab21d-217">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ab21d-217">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="ab21d-218">Ange standard katalog på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-218">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-219">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-219">Prototype</span></span>

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-220">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-220">Description</span></span>

<span data-ttu-id="ab21d-221">Den här tjänsten anger standard katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-221">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="ab21d-222">Den här standard katalogen gäller endast för den här klientens anslutning.</span><span class="sxs-lookup"><span data-stu-id="ab21d-222">This default directory applies only to this client’s connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-223">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-223">Input Parameters</span></span>

- <span data-ttu-id="ab21d-224">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-224">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-225">**directory_path** Namnet på den katalog Sök väg som ska anges.</span><span class="sxs-lookup"><span data-stu-id="ab21d-225">**directory_path** Name of directory path to set.</span></span>
- <span data-ttu-id="ab21d-226">**wait_option** Definierar hur länge tjänsten ska vänta på katalog uppsättningen för FTP-katalogen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-226">**wait_option** Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="ab21d-227">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-227">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-228">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-228">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-229">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-230">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-230">Return Values</span></span>

- <span data-ttu-id="ab21d-231">**NX_SUCCESS** (0X00) slutförd FTP standard uppsättning.</span><span class="sxs-lookup"><span data-stu-id="ab21d-231">**NX_SUCCESS** (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="ab21d-232">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-234">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-234">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-235">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-235">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-236">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-236">Allowed From</span></span>

<span data-ttu-id="ab21d-237">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-238">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-238">Example</span></span>

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="ab21d-239">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ab21d-239">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="ab21d-240">Ta bort katalog på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-240">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-241">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-241">Prototype</span></span>

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-242">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-242">Description</span></span>

<span data-ttu-id="ab21d-243">Den här tjänsten tar bort den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-243">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-244">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-244">Input Parameters</span></span>

- <span data-ttu-id="ab21d-245">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-245">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-246">**directory_name** Namnet på den katalog som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ab21d-246">**directory_name** Name of directory to delete.</span></span>
- <span data-ttu-id="ab21d-247">**wait_option** Definierar hur länge tjänsten ska vänta på borttagning av FTP-katalogen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-247">**wait_option** Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="ab21d-248">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-248">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-249">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-249">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-250">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-251">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-251">Return Values</span></span>

- <span data-ttu-id="ab21d-252">**NX_SUCCESS** (0X00) FTP-katalogen har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="ab21d-252">**NX_SUCCESS** (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="ab21d-253">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-255">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-255">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-256">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-256">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-257">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-257">Allowed From</span></span>

<span data-ttu-id="ab21d-258">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-258">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-259">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-259">Example</span></span>

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="ab21d-260">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="ab21d-260">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="ab21d-261">Hämta katalog lista från FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-261">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-262">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-262">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-263">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-263">Description</span></span>

<span data-ttu-id="ab21d-264">Den här tjänsten hämtar innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-264">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="ab21d-265">Den tillhandahållna paket pekaren innehåller en eller flera katalog poster.</span><span class="sxs-lookup"><span data-stu-id="ab21d-265">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="ab21d-266">Varje post avgränsas med en \<cr/lf\> kombination.</span><span class="sxs-lookup"><span data-stu-id="ab21d-266">Each entry is separated by a \<cr/lf\> combination.</span></span> <span data-ttu-id="ab21d-267">***Nx_ftp_client_directory_listing_continue*** ska anropas för att slutföra hämtningen av katalogen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-267">The ***nx_ftp_client_directory_listing_continue*** should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-268">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-268">Input Parameters</span></span>

- <span data-ttu-id="ab21d-269">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-269">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-270">**directory_name** Namnet på den katalog som innehållet ska hämtas från.</span><span class="sxs-lookup"><span data-stu-id="ab21d-270">**directory_name** Name of directory to get contents of.</span></span>
- <span data-ttu-id="ab21d-271">**packet_ptr** Pekare till pekare för mål paket.</span><span class="sxs-lookup"><span data-stu-id="ab21d-271">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="ab21d-272">Om det lyckas kommer paketets nytto last att innehålla en eller flera katalog poster.</span><span class="sxs-lookup"><span data-stu-id="ab21d-272">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="ab21d-273">**wait_option** Definierar hur länge tjänsten ska vänta på lista över FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="ab21d-273">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="ab21d-274">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-274">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-275">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-275">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-276">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-277">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-277">Return Values</span></span>

- <span data-ttu-id="ab21d-278">**NX_SUCCESS** (0x00) lista över slutförda FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="ab21d-278">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="ab21d-279">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-280">Tjänsten **NX_NOT_ENABLED** (0x14) (IPv6) är inte aktive rad</span><span class="sxs-lookup"><span data-stu-id="ab21d-280">**NX_NOT_ENABLED** (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="ab21d-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) fick inget 1xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="ab21d-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-283">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-283">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-284">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-284">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-285">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-285">Allowed From</span></span>

<span data-ttu-id="ab21d-286">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-287">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-287">Example</span></span>

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="ab21d-288">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="ab21d-288">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="ab21d-289">Fortsätt katalog listan från FTP-servern</span><span class="sxs-lookup"><span data-stu-id="ab21d-289">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-290">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-290">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-291">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-291">Description</span></span>

<span data-ttu-id="ab21d-292">Den här tjänsten fortsätter att hämta innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-292">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="ab21d-293">Det bör ha föregås av ett anrop till ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="ab21d-293">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="ab21d-294">Om det lyckas kommer den tillhandahållna paket pekaren innehålla en eller flera katalog poster.</span><span class="sxs-lookup"><span data-stu-id="ab21d-294">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="ab21d-295">Den här rutinen ska anropas tills en NX_FTP_END_OF_LISTING-status tas emot.</span><span class="sxs-lookup"><span data-stu-id="ab21d-295">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-296">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-296">Input Parameters</span></span>

- <span data-ttu-id="ab21d-297">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-297">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-298">**packet_ptr** Pekare till pekare för mål paket.</span><span class="sxs-lookup"><span data-stu-id="ab21d-298">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="ab21d-299">Om det lyckas innehåller paketets nytto Last en eller flera katalog poster, avgränsade med <CR/LF>.</span><span class="sxs-lookup"><span data-stu-id="ab21d-299">If successful, the packet payload will contain one or more directory entries, separated by a <cr/lf>.</span></span>
- <span data-ttu-id="ab21d-300">**wait_option** Definierar hur länge tjänsten ska vänta på lista över FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="ab21d-300">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="ab21d-301">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-301">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-302">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-302">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-303">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-304">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-304">Return Values</span></span>

- <span data-ttu-id="ab21d-305">**NX_SUCCESS** (0x00) lista över slutförda FTP-kataloger.</span><span class="sxs-lookup"><span data-stu-id="ab21d-305">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="ab21d-306">**NX_FTP_END_OF_LISTING** (0XD8) inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-306">**NX_FTP_END_OF_LISTING** (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="ab21d-307">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-309">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-309">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-310">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-310">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-311">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-311">Allowed From</span></span>

<span data-ttu-id="ab21d-312">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-313">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-313">Example</span></span>

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="ab21d-314">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="ab21d-314">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="ab21d-315">Koppla från FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-315">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-316">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-316">Prototype</span></span>

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-317">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-317">Description</span></span>

<span data-ttu-id="ab21d-318">Den här tjänsten kopplar från en tidigare upprättad FTP-server-anslutning till den angivna FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-318">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-319">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-319">Input Parameters</span></span>

- <span data-ttu-id="ab21d-320">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-320">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-321">**wait_option** Definierar hur länge tjänsten ska vänta tills FTP-klienten kopplas från.</span><span class="sxs-lookup"><span data-stu-id="ab21d-321">**wait_option** Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="ab21d-322">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-322">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-323">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-323">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-324">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-325">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-325">Return Values</span></span>

- <span data-ttu-id="ab21d-326">**NX_SUCCESS** (0X00) slutförd FTP-anslutning.</span><span class="sxs-lookup"><span data-stu-id="ab21d-326">**NX_SUCCESS** (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="ab21d-327">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-329">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-329">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-330">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-330">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-331">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-331">Allowed From</span></span>

<span data-ttu-id="ab21d-332">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-332">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-333">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-333">Example</span></span>

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="ab21d-334">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="ab21d-334">nx_ftp_client_file_close</span></span>

<span data-ttu-id="ab21d-335">Stäng klient filen</span><span class="sxs-lookup"><span data-stu-id="ab21d-335">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-336">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-336">Prototype</span></span>

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-337">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-337">Description</span></span>

<span data-ttu-id="ab21d-338">Den här tjänsten stänger en tidigare öppnad fil på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="ab21d-338">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-339">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-339">Input Parameters</span></span>

- <span data-ttu-id="ab21d-340">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-340">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-341">**wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientprogramvaran stängs.</span><span class="sxs-lookup"><span data-stu-id="ab21d-341">**wait_option** Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="ab21d-342">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-342">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-343">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-343">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-344">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-345">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-345">Return Values</span></span>

- <span data-ttu-id="ab21d-346">**NX_SUCCESS** (0X00) slutförd FTP-fil.</span><span class="sxs-lookup"><span data-stu-id="ab21d-346">**NX_SUCCESS** (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="ab21d-347">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-348">**NX_FTP_NOT_OPEN (0xD5)** Filen är inte öppen; Det går inte att stänga den</span><span class="sxs-lookup"><span data-stu-id="ab21d-348">**NX_FTP_NOT_OPEN (0xD5)** File not open; cannot close it</span></span>
- <span data-ttu-id="ab21d-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-350">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-350">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-351">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-351">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-352">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-352">Allowed From</span></span>

<span data-ttu-id="ab21d-353">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-354">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-354">Example</span></span>

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="ab21d-355">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="ab21d-355">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="ab21d-356">Ta bort fil på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-356">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-357">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-357">Prototype</span></span>

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-358">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-358">Description</span></span>

<span data-ttu-id="ab21d-359">Den här tjänsten tar bort den angivna filen på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="ab21d-359">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-360">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-360">Input Parameters</span></span>

- <span data-ttu-id="ab21d-361">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-361">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-362">**file_name** Namn på filen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ab21d-362">**file_name** Name of file to delete.</span></span>
- <span data-ttu-id="ab21d-363">**wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klienttjänsten ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ab21d-363">**wait_option** Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="ab21d-364">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-364">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-365">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-365">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-366">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-367">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-367">Return Values</span></span>

- <span data-ttu-id="ab21d-368">**NX_SUCCESS** (0X00) FTP-filen har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="ab21d-368">**NX_SUCCESS** (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="ab21d-369">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-371">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-371">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-372">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-372">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-373">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-373">Allowed From</span></span>

<span data-ttu-id="ab21d-374">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-374">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-375">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-375">Example</span></span>

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="ab21d-376">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="ab21d-376">nx_ftp_client_file_open</span></span>

<span data-ttu-id="ab21d-377">Öppnar filen på FTP-servern</span><span class="sxs-lookup"><span data-stu-id="ab21d-377">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-378">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-378">Prototype</span></span>

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-379">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-379">Description</span></span>

<span data-ttu-id="ab21d-380">Den här tjänsten öppnar den angivna filen – för att läsa eller skriva – på FTP-servern som tidigare var ansluten till den angivna klient instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-380">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-381">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-381">Input Parameters</span></span>

- <span data-ttu-id="ab21d-382">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-382">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-383">**file_name** Namnet på filen som ska öppnas.</span><span class="sxs-lookup"><span data-stu-id="ab21d-383">**file_name** Name of file to open.</span></span>
- <span data-ttu-id="ab21d-384">**open_type** Antingen **NX_FTP_OPEN_FOR_READ** eller **NX_FTP_OPEN_FOR_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="ab21d-384">**open_type** Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="ab21d-385">**wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klienttjänsten är öppen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-385">**wait_option** Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="ab21d-386">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-386">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-387">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-387">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-388">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-389">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-389">Return Values</span></span>

- <span data-ttu-id="ab21d-390">**NX_SUCCESS** (0X00) slutförd FTP-fil öppen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-390">**NX_SUCCESS** (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="ab21d-391">**NX_OPTION_ERROR** (0X0a) ogiltig öppen typ.</span><span class="sxs-lookup"><span data-stu-id="ab21d-391">**NX_OPTION_ERROR** (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="ab21d-392">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-393">**NX_FTP_NOT_CLOSED** (0XD6) FTP-klienten har redan öppnats.</span><span class="sxs-lookup"><span data-stu-id="ab21d-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="ab21d-394">**NX_NO_FREE_PORTS** (0x45) det finns inga tillgängliga TCP-portar att tilldela</span><span class="sxs-lookup"><span data-stu-id="ab21d-394">**NX_NO_FREE_PORTS** (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="ab21d-395">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-395">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-396">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-396">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-397">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-397">Allowed From</span></span>

<span data-ttu-id="ab21d-398">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-399">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-399">Example</span></span>

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="ab21d-400">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="ab21d-400">nx_ftp_client_file_read</span></span>

<span data-ttu-id="ab21d-401">Läsa från fil</span><span class="sxs-lookup"><span data-stu-id="ab21d-401">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-402">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-402">Prototype</span></span>

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-403">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-403">Description</span></span>

<span data-ttu-id="ab21d-404">Den här tjänsten läser ett paket från en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="ab21d-404">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="ab21d-405">Den bör anropas upprepade gånger tills en status för NX_FTP_END_OF_FILE tas emot.</span><span class="sxs-lookup"><span data-stu-id="ab21d-405">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="ab21d-406">Observera att anroparen inte allokerar ett paket för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-406">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="ab21d-407">Du behöver bara ange en pekare till en paket pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-407">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="ab21d-408">Den här tjänsten kommer att uppdatera paket pekaren så att den pekar på ett paket som hämtats från socket Receive-kön.</span><span class="sxs-lookup"><span data-stu-id="ab21d-408">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="ab21d-409">Om statusen lyckades returneras, innebär det att det fanns ett tillgängligt paket och att det är anroparens ansvar att frigöra paketet när det är klart.</span><span class="sxs-lookup"><span data-stu-id="ab21d-409">If a successful status is returned, that means there was a packet available, and it is the caller’s responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="ab21d-410">Om en status som inte är noll (antingen en fel status eller NX_FTP_END_OF_FILE) returneras, frigörs inte paketet av anroparen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-410">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="ab21d-411">Annars genereras ett fel när paket pekaren är NULL.</span><span class="sxs-lookup"><span data-stu-id="ab21d-411">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-412">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-412">Input Parameters</span></span>

- <span data-ttu-id="ab21d-413">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-413">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-414">**packet_ptr** Pekare till målet för data paket pekaren som ska lagras.</span><span class="sxs-lookup"><span data-stu-id="ab21d-414">**packet_ptr** Pointer to destination for the data packet pointer to be stored.</span></span> <span data-ttu-id="ab21d-415">Om det lyckas kan paketet vara en del av eller alla innehåller filen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-415">If successful, the packet some or all the contains of the file.</span></span>
- <span data-ttu-id="ab21d-416">**wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientdatorn läses.</span><span class="sxs-lookup"><span data-stu-id="ab21d-416">**wait_option** Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="ab21d-417">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-417">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-418">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-418">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-419">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-420">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-420">Return Values</span></span>

- <span data-ttu-id="ab21d-421">**NX_SUCCESS** (0x00) en lyckad FTP-fil har lästs.</span><span class="sxs-lookup"><span data-stu-id="ab21d-421">**NX_SUCCESS** (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="ab21d-422">**NX_FTP_NOT_OPEN** (0XD5) FTP-klienten är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-422">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="ab21d-423">**NX_FTP_END_OF_FILE** (0xD7) fil villkoret är slut.</span><span class="sxs-lookup"><span data-stu-id="ab21d-423">**NX_FTP_END_OF_FILE** (0xD7) End of file condition.</span></span>
- <span data-ttu-id="ab21d-424">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-424">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-425">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-425">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-426">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-426">Allowed From</span></span>

<span data-ttu-id="ab21d-427">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-428">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-428">Example</span></span>

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

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

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="ab21d-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="ab21d-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="ab21d-430">Byt namn på fil på FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-431">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-431">Prototype</span></span>

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-432">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-432">Description</span></span>

<span data-ttu-id="ab21d-433">Den här tjänsten byter namn på en fil på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="ab21d-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-434">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-434">Input Parameters</span></span>

- <span data-ttu-id="ab21d-435">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-435">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-436">**filename** Aktuellt fil namn.</span><span class="sxs-lookup"><span data-stu-id="ab21d-436">**filename** Current name of file.</span></span>
- <span data-ttu-id="ab21d-437">**new_filename** Nytt namn på filen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-437">**new_filename** New name for file.</span></span>
- <span data-ttu-id="ab21d-438">**wait_option** Definierar hur länge tjänsten ska vänta på att byta namn på FTP-klienter.</span><span class="sxs-lookup"><span data-stu-id="ab21d-438">**wait_option** Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="ab21d-439">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-440">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-440">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-441">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-442">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-442">Return Values</span></span>

- <span data-ttu-id="ab21d-443">**NX_SUCCESS** (0x00) namn på slutförd FTP-fil.</span><span class="sxs-lookup"><span data-stu-id="ab21d-443">**NX_SUCCESS** (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="ab21d-444">**NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ab21d-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) fick inte svar på 3xx (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="ab21d-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)</span><span class="sxs-lookup"><span data-stu-id="ab21d-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ab21d-447">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-447">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-448">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-448">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-449">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-449">Allowed From</span></span>

<span data-ttu-id="ab21d-450">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-450">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-451">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-451">Example</span></span>

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="ab21d-452">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="ab21d-452">nx_ftp_client_file_write</span></span>

<span data-ttu-id="ab21d-453">Skriv till fil</span><span class="sxs-lookup"><span data-stu-id="ab21d-453">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-454">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-454">Prototype</span></span>

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ab21d-455">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-455">Description</span></span>

<span data-ttu-id="ab21d-456">Den här tjänsten skriver ett data paket till den tidigare öppnade filen på FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="ab21d-456">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-457">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-457">Input Parameters</span></span>

- <span data-ttu-id="ab21d-458">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-458">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-459">**packet_ptr** Paket pekare som innehåller data som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="ab21d-459">**packet_ptr** Packet pointer containing data to write.</span></span>
- <span data-ttu-id="ab21d-460">**wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientdatorn skriver.</span><span class="sxs-lookup"><span data-stu-id="ab21d-460">**wait_option** Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="ab21d-461">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab21d-461">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ab21d-462">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.</span><span class="sxs-lookup"><span data-stu-id="ab21d-462">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ab21d-463">**TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="ab21d-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-464">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-464">Return Values</span></span>

- <span data-ttu-id="ab21d-465">**NX_SUCCESS** (0X00) lyckad FTP-fil skrivning.</span><span class="sxs-lookup"><span data-stu-id="ab21d-465">**NX_SUCCESS** (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="ab21d-466">**NX_FTP_NOT_OPEN** (0XD5) FTP-klienten är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-466">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="ab21d-467">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-467">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-468">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-469">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-469">Allowed From</span></span>

<span data-ttu-id="ab21d-470">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-471">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-471">Example</span></span>

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="ab21d-472">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="ab21d-472">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="ab21d-473">Aktivera eller inaktivera passivt överförings läge</span><span class="sxs-lookup"><span data-stu-id="ab21d-473">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-474">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-474">Prototype</span></span>

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="ab21d-475">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-475">Description</span></span>

<span data-ttu-id="ab21d-476">Den här tjänsten aktiverar passivt överförings läge om passive_mode_enabled indatatypen är inställd på NX_TRUE på en tidigare skapad FTP-serverinstans, så att efterföljande anrop till läsa eller skriva filer (RETR, lagr) eller hämtning av en katalog lista (NLST) görs i överförings läge.</span><span class="sxs-lookup"><span data-stu-id="ab21d-476">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="ab21d-477">Om du vill inaktivera överföring i passivt läge och återgå till standard beteendet för aktivt överförings läge, anropar du den här funktionen med passive_mode_enabled indatamängden för att NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="ab21d-477">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-478">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-478">Input Parameters</span></span>

- <span data-ttu-id="ab21d-479">**ftp_client_ptr** Pekare till kontroll block för FTP-klient.</span><span class="sxs-lookup"><span data-stu-id="ab21d-479">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ab21d-480">**passive_mode_enabled** Om värdet är NX_TRUE aktive ras passivt läge.</span><span class="sxs-lookup"><span data-stu-id="ab21d-480">**passive_mode_enabled** If set to NX_TRUE, passive mode is enabled.</span></span><br /><span data-ttu-id="ab21d-481">Om värdet är NX_FALSE inaktive ras passivt läge.</span><span class="sxs-lookup"><span data-stu-id="ab21d-481">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-482">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-482">Return Values</span></span>

- <span data-ttu-id="ab21d-483">**NX_SUCCESS** (0x00) har angetts i passivt läge.</span><span class="sxs-lookup"><span data-stu-id="ab21d-483">**NX_SUCCESS** (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="ab21d-484">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-484">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-485">NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="ab21d-485">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-486">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-486">Allowed From</span></span>

<span data-ttu-id="ab21d-487">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-488">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-488">Example</span></span>

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="ab21d-489">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="ab21d-489">nx_ftp_server_create</span></span>

<span data-ttu-id="ab21d-490">Skapa FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-490">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-491">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-491">Prototype</span></span>

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="ab21d-492">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-492">Description</span></span>

<span data-ttu-id="ab21d-493">Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-493">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="ab21d-494">Observera att FTP-servern måste startas med ett anrop till ***nx_ftp_server_start*** för att det ska kunna starta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ab21d-494">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-495">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-495">Input Parameters</span></span>

- <span data-ttu-id="ab21d-496">**ftp_server_ptr** Pekare till kontroll block för FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-496">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="ab21d-497">**ftp_server_name** Namn på FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-497">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="ab21d-498">**ip_ptr** Pekare till den associerade NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-498">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="ab21d-499">Obs! det kan bara finnas en FTP-server för en IP-instans.</span><span class="sxs-lookup"><span data-stu-id="ab21d-499">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="ab21d-500">**media_ptr** Pekare till den associerade FileX Media-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-500">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="ab21d-501">**stack_ptr** Pekar på minne för den interna FTP-serverns stack-tråd.</span><span class="sxs-lookup"><span data-stu-id="ab21d-501">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="ab21d-502">**stack_size** Storlek på det stack områden som anges av *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="ab21d-502">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="ab21d-503">**pool_ptr** Pekare till standard NetX.</span><span class="sxs-lookup"><span data-stu-id="ab21d-503">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="ab21d-504">Observera nytto Last storleken för paket i poolen måste vara tillräckligt stor för att rymma största fil namn/sökväg.</span><span class="sxs-lookup"><span data-stu-id="ab21d-504">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="ab21d-505">**ftp_login** Funktions pekare till programmets inloggnings funktion.</span><span class="sxs-lookup"><span data-stu-id="ab21d-505">**ftp_login** Function pointer to application’s login function.</span></span> <span data-ttu-id="ab21d-506">Den här funktionen anges användar namn och lösen ord från klienten som begär en anslutning och klient adressen i data typen ULONG.</span><span class="sxs-lookup"><span data-stu-id="ab21d-506">This function is supplied the username and password from the Client requesting a connection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="ab21d-507">Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ab21d-507">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="ab21d-508">**ftp_logout** Funktions pekare till programmets utloggnings funktion.</span><span class="sxs-lookup"><span data-stu-id="ab21d-508">**ftp_logout** Function pointer to application’s logout function.</span></span> <span data-ttu-id="ab21d-509">Den här funktionen anges användar namn och lösen ord från klienten som begär en från koppling och klient adressen i data typen ULONG.</span><span class="sxs-lookup"><span data-stu-id="ab21d-509">This function is supplied the username and password from the Client requesting a disconnection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="ab21d-510">Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ab21d-510">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-511">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-511">Return Values</span></span>

- <span data-ttu-id="ab21d-512">**NX_SUCCESS** (0X00) slutförd FTP-server skapa.</span><span class="sxs-lookup"><span data-stu-id="ab21d-512">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="ab21d-513">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-513">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-514">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-514">Allowed From</span></span>

<span data-ttu-id="ab21d-515">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="ab21d-515">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-516">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-516">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a><span data-ttu-id="ab21d-517">nxd_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="ab21d-517">nxd_ftp_server_create</span></span>

<span data-ttu-id="ab21d-518">Skapa FTP-server med stöd för IPv4 och IPv6</span><span class="sxs-lookup"><span data-stu-id="ab21d-518">Create FTP Server with IPv4 and IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-519">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-519">Prototype</span></span>

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="ab21d-520">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-520">Description</span></span>

<span data-ttu-id="ab21d-521">Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-521">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="ab21d-522">Observera att FTP-servern fortfarande måste startas med ett anrop till ***nx_ftp_server_start*** för att den ska kunna påbörjas när servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="ab21d-522">Note the FTP Server still needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation after the Server is created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-523">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-523">Input Parameters</span></span>

- <span data-ttu-id="ab21d-524">**ftp_server_ptr** Pekare till kontroll block för FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-524">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="ab21d-525">**ftp_server_name** Namn på FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-525">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="ab21d-526">**ip_ptr** Pekare till den associerade NetX IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-526">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="ab21d-527">Obs! det kan bara finnas en FTP-server för en IP-instans.</span><span class="sxs-lookup"><span data-stu-id="ab21d-527">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="ab21d-528">**media_ptr** Pekare till den associerade FileX Media-instansen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-528">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="ab21d-529">**stack_ptr** Pekar på minne för den interna FTP-serverns stack-tråd.</span><span class="sxs-lookup"><span data-stu-id="ab21d-529">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="ab21d-530">**stack_size** Storlek på det stack områden som anges av *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="ab21d-530">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="ab21d-531">**pool_ptr** Pekare till standard NetX.</span><span class="sxs-lookup"><span data-stu-id="ab21d-531">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="ab21d-532">Observera nytto Last storleken för paket i poolen måste vara tillräckligt stor för att rymma största fil namn/sökväg.</span><span class="sxs-lookup"><span data-stu-id="ab21d-532">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="ab21d-533">**ftp_login_duo** Funktions pekare till programmets inloggnings funktion.</span><span class="sxs-lookup"><span data-stu-id="ab21d-533">**ftp_login_duo** Function pointer to application’s login function.</span></span> <span data-ttu-id="ab21d-534">Den här funktionen anges användar namn och lösen ord från klienten som begär en anslutning och en pekare till klient adressen i NXD_ADDRESS data typen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-534">This function is supplied the username and password from the Client requesting a connection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="ab21d-535">Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ab21d-535">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="ab21d-536">**ftp_logout_duo** Funktions pekare till programmets utloggnings funktion.</span><span class="sxs-lookup"><span data-stu-id="ab21d-536">**ftp_logout_duo** Function pointer to application’s logout function.</span></span> <span data-ttu-id="ab21d-537">Den här funktionen anges användar namn och lösen ord från klienten som begär en från koppling, och en pekare till klient adressen i NXD_ADDRESS data typen.</span><span class="sxs-lookup"><span data-stu-id="ab21d-537">This function is supplied the username and password from the Client requesting a disconnection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="ab21d-538">Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ab21d-538">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-539">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-539">Return Values</span></span>

- <span data-ttu-id="ab21d-540">**NX_SUCCESS** (0X00) slutförd FTP-server skapa.</span><span class="sxs-lookup"><span data-stu-id="ab21d-540">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="ab21d-541">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-541">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-542">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-542">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-543">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-543">Allowed From</span></span>

<span data-ttu-id="ab21d-544">Initiering och trådar</span><span class="sxs-lookup"><span data-stu-id="ab21d-544">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-545">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-545">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="ab21d-546">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="ab21d-546">nx_ftp_server_delete</span></span>

<span data-ttu-id="ab21d-547">Ta bort FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-547">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-548">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-548">Prototype</span></span>

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ab21d-549">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-549">Description</span></span>

<span data-ttu-id="ab21d-550">Den här tjänsten tar bort en instans av en tidigare skapad FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-550">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-551">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-551">Input Parameters</span></span>

- <span data-ttu-id="ab21d-552">**ftp_server_ptr** Pekare till kontroll block för FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-552">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-553">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-553">Return Values</span></span>

- <span data-ttu-id="ab21d-554">**NX_SUCCESS** (0X00) slutförd borttagning av FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-554">**NX_SUCCESS** (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="ab21d-555">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-555">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-556">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-556">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-557">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-557">Allowed From</span></span>

<span data-ttu-id="ab21d-558">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-558">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-559">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-559">Example</span></span>

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="ab21d-560">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="ab21d-560">nx_ftp_server_start</span></span>

<span data-ttu-id="ab21d-561">Starta FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-561">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-562">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-562">Prototype</span></span>

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ab21d-563">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-563">Description</span></span>

<span data-ttu-id="ab21d-564">Den här tjänsten startar en instans av en tidigare skapad FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-564">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-565">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-565">Input Parameters</span></span>

- <span data-ttu-id="ab21d-566">**ftp_server_ptr** Pekare till kontroll block för FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-566">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-567">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-567">Return Values</span></span>

- <span data-ttu-id="ab21d-568">**NX_SUCCESS** (0X00) SLUTFÖRDE FTP-servern.</span><span class="sxs-lookup"><span data-stu-id="ab21d-568">**NX_SUCCESS** (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="ab21d-569">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-569">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-570">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-570">Allowed From</span></span>

<span data-ttu-id="ab21d-571">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-571">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-572">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-572">Example</span></span>

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="ab21d-573">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="ab21d-573">nx_ftp_server_stop</span></span>

<span data-ttu-id="ab21d-574">Stoppa FTP-Server</span><span class="sxs-lookup"><span data-stu-id="ab21d-574">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ab21d-575">Prototyp</span><span class="sxs-lookup"><span data-stu-id="ab21d-575">Prototype</span></span>

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ab21d-576">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab21d-576">Description</span></span>

<span data-ttu-id="ab21d-577">Den här tjänsten stoppar en instans av en tidigare skapad och startad FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-577">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ab21d-578">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="ab21d-578">Input Parameters</span></span>

- <span data-ttu-id="ab21d-579">**ftp_server_ptr** Pekare till kontroll block för FTP-server.</span><span class="sxs-lookup"><span data-stu-id="ab21d-579">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ab21d-580">Retur värden</span><span class="sxs-lookup"><span data-stu-id="ab21d-580">Return Values</span></span>

- <span data-ttu-id="ab21d-581">**NX_SUCCESS** (0x00) en slutförd FTP-server stoppades.</span><span class="sxs-lookup"><span data-stu-id="ab21d-581">**NX_SUCCESS** (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="ab21d-582">NX_PTR_ERROR (0x07) ogiltig FTP-pekare.</span><span class="sxs-lookup"><span data-stu-id="ab21d-582">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ab21d-583">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab21d-583">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ab21d-584">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="ab21d-584">Allowed From</span></span>

<span data-ttu-id="ab21d-585">Konversation</span><span class="sxs-lookup"><span data-stu-id="ab21d-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ab21d-586">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab21d-586">Example</span></span>

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
