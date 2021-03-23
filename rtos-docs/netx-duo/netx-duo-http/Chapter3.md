---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo HTTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo-HTTP-tjänster (visas nedan) i alfabetisk ordning förutom för "NetX" (endast IPv4) motsvarande samma tjänst länkas samman).
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 703071cd5a1d0677a3e995fccfe35d8b1dbbd9f3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825968"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a><span data-ttu-id="8d4f3-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo HTTP-tjänster</span><span class="sxs-lookup"><span data-stu-id="8d4f3-103">Chapter 3 - Description of Azure RTOS NetX Duo HTTP Services</span></span>

<span data-ttu-id="8d4f3-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo-HTTP-tjänster (visas nedan) i alfabetisk ordning förutom för "NetX" (endast IPv4) motsvarande samma tjänst länkas samman).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-104">This chapter contains a description of all Azure RTOS NetX Duo HTTP services (listed below) in alphabetical order except for the ‘NetX’ (IPv4 only) equivalent of the same service are paired together).</span></span>

<span data-ttu-id="8d4f3-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i fetstil av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-105">In the “Return Values” section in the following API descriptions, values in BOLD are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="8d4f3-106">**HTTP-klient tjänster:**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="8d4f3-107">**nx_http_client_create** *skapa en http-klient instans*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-107">**nx_http_client_create** *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="8d4f3-108">**nx_http_client_delete** *ta bort en http-klient instans*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-108">**nx_http_client_delete** *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="8d4f3-109">**nx_http_client_get_start** *starta en HTTP GET-begäran (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-109">**nx_http_client_get_start** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="8d4f3-110">**nx_http_client_get_start_extended** *starta en HTTP GET-begäran (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-110">**nx_http_client_get_start_extended** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="8d4f3-111">**nxd_http_client_get_start** *starta en HTTP GET-begäran (IPv4 eller IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-111">**nxd_http_client_get_start** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="8d4f3-112">**nxd_http_client_get_start_extended** *starta en HTTP GET-begäran (IPv4 eller IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-112">**nxd_http_client_get_start_extended** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="8d4f3-113">**nx_http_client_get_packet** *Hämta nästa resurs data paket*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-113">**nx_http_client_get_packet** *Get next resource data packet*</span></span>
- <span data-ttu-id="8d4f3-114">**nx_http_client_put_start** *starta en http-begäran (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-114">**nx_http_client_put_start** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="8d4f3-115">**nx_http_client_put_start_extended** *starta en http-begäran (endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-115">**nx_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="8d4f3-116">**nxd_http_client_put_start** *starta en http-begäran (IPv4 eller IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-116">**nxd_http_client_put_start** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="8d4f3-117">**nxd_http_client_put_start_extended** *starta en http-begäran (IPv4 eller IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-117">**nxd_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="8d4f3-118">**nx_http_client_put_packet** *skicka nästa resurs data paket*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-118">**nx_http_client_put_packet** *Send next resource data packet*</span></span>
- <span data-ttu-id="8d4f3-119">**nx_http_client_set_connect_port** *ändra porten för att ansluta till http-servern*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-119">**nx_http_client_set_connect_port** *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="8d4f3-120">**HTTP-Server tjänster:**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-120">**HTTP server services:**</span></span>

- <span data-ttu-id="8d4f3-121">**nx_http_server_cache_info_callback_set** *Ange motringning för att hämta ålder och senaste ändrings datum för angiven URL*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-121">**nx_http_server_cache_info_callback_set** *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="8d4f3-122">**nx_http_server_callback_data_send** *Skicka HTTP-data från callback-funktionen*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-122">**nx_http_server_callback_data_send** *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="8d4f3-123">**nx_http_server_callback_generate_response_header** *skapa svars huvud i callback-funktioner*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-123">**nx_http_server_callback_generate_response_header** *Create response header in callback functions*</span></span>
- <span data-ttu-id="8d4f3-124">**nx_http_server_callback_generate_response_header_extended** *skapa svars huvud i callback-funktioner*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-124">**nx_http_server_callback_generate_response_header_extended** *Create response header in callback functions*</span></span>
- <span data-ttu-id="8d4f3-125">**nx_http_server_callback_packet_send** *Skicka ett http-paket från ett http-motanrop*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-125">**nx_http_server_callback_packet_send** *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="8d4f3-126">**nx_http_server_callback_response_send** *Skicka svar från callback-funktionen*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-126">**nx_http_server_callback_response_send** *Send response from callback function*</span></span>
- <span data-ttu-id="8d4f3-127">**nx_http_server_callback_response_send_extended** *Skicka svar från callback-funktionen*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-127">**nx_http_server_callback_response_send_extended** *Send response from callback function*</span></span>
- <span data-ttu-id="8d4f3-128">**nx_http_server_content_get** *Hämta innehåll från begäran*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-128">**nx_http_server_content_get** *Get content from the request*</span></span>
- <span data-ttu-id="8d4f3-129">**nx_http_server_content_get_extended** *Hämta innehåll från begäran; stöder tomma (noll innehålls längd) begär Anden*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-129">**nx_http_server_content_get_extended** *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="8d4f3-130">**nx_http_server_content_length_get** *Hämta längden på innehållet i begäran*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-130">**nx_http_server_content_length_get** *Get length of content in the request*</span></span>
- <span data-ttu-id="8d4f3-131">**nx_http_server_content_length_get_extended** *Hämta längden på innehållet i begäran; stöder tomma (noll innehålls längd) begär Anden*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-131">**nx_http_server_content_length_get_extended** *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="8d4f3-132">**nx_http_server_create** *skapa en http-serverinstans*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-132">**nx_http_server_create** *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="8d4f3-133">**nx_http_server_delete** \* ta bort en http-serverinstans \*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-133">**nx_http_server_delete** \* Delete an HTTP Server instance\*</span></span>
- <span data-ttu-id="8d4f3-134">**nx_http_server_get_entity_content** *returnera storlek och plats för enhetens innehåll i URL: en*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-134">**nx_http_server_get_entity_content** *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="8d4f3-135">**nx_http_server_get_entity_header** *extrahera URL-enhetens rubrik till angiven buffert*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-135">**nx_http_server_get_entity_header** *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="8d4f3-136">**nx_http_server_gmt_callback_set** *Ange motringning för att hämta GMT-datum och tid*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-136">**nx_http_server_gmt_callback_set** *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="8d4f3-137">**nx_http_server_invalid_userpassword_notify_set** *Ange motringning för när ogiltigt användar namn och lösen ord tas emot i en klientbegäran*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-137">**nx_http_server_invalid_userpassword_notify_set** *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="8d4f3-138">**nx_http_server_mime_maps_additional_set** *definiera ytterligare MIME-mappningar för HTML*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-138">**nx_http_server_mime_maps_additional_set** *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="8d4f3-139">**nx_http_server_packet_content_find** *extrahera innehålls längd i http-sidhuvudet och ange pekaren till början av innehålls data*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-139">**nx_http_server_packet_content_find** *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="8d4f3-140">**nx_http_server_packet_get** *ta emot klient paket direkt*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-140">**nx_http_server_packet_get** *Receive client packet directly*</span></span>
- <span data-ttu-id="8d4f3-141">**nx_http_server_param_get** *Hämta parameter från begäran*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-141">**nx_http_server_param_get** *Get parameter from the request*</span></span>
- <span data-ttu-id="8d4f3-142">**nx_http_server_query_get** *Hämta fråga från begäran*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-142">**nx_http_server_query_get** *Get query from the request*</span></span>
- <span data-ttu-id="8d4f3-143">**nx_http_server_start** *Starta http-servern*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-143">**nx_http_server_start** *Start the HTTP Server*</span></span>
- <span data-ttu-id="8d4f3-144">**nx_http_server_stop** *stoppa http-servern*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-144">**nx_http_server_stop** *Stop the HTTP Server*</span></span>
- <span data-ttu-id="8d4f3-145">**nx_http_server_type_get (inaktuell)** *extrahera http-typ, t. ex. text/plain från rubriken*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-145">**nx_http_server_type_get (deprecated)** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="8d4f3-146">**nx_http_server_type_get_extended** *extrahera http-typ t. ex. text/plain från rubriken*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-146">**nx_http_server_type_get_extended** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="8d4f3-147">**nx_http_server_digest_authenticate_notify_set** *Ange funktionen Digest-autentisering*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-147">**nx_http_server_digest_authenticate_notify_set** *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="8d4f3-148">funktionen för motringning av **nx_http_server_authentication_check_set** *anger autentisering*</span><span class="sxs-lookup"><span data-stu-id="8d4f3-148">**nx_http_server_authentication_check_set** *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="8d4f3-149">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="8d4f3-149">nx_http_client_create</span></span>

<span data-ttu-id="8d4f3-150">Skapa en PPPoE-klient instans</span><span class="sxs-lookup"><span data-stu-id="8d4f3-150">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-151">Prototype</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="8d4f3-152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-152">Description</span></span>

<span data-ttu-id="8d4f3-153">Den här tjänsten skapar en HTTP-klient instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-153">This service creates an HTTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-154">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-154">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-155">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-155">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-156">**client_name** Namn på HTTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-156">**client_name** Name of HTTP Client instance.</span></span>
 - <span data-ttu-id="8d4f3-157">**ip_ptr** Pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-157">**ip_ptr** Pointer to IP instance.</span></span>
 - <span data-ttu-id="8d4f3-158">**pool_ptr** Pekare till standard paketets pool.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-158">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="8d4f3-159">Observera att paketen i den här poolen måste ha en nytto last som är tillräckligt stor för att hantera hela svars huvudet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-159">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="8d4f3-160">Detta definieras av NX_HTTP_CLIENT_MIN_PACKET_SIZE i *nx_http. h*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-160">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http.h*.</span></span>
 - <span data-ttu-id="8d4f3-161">**window_size** Storlek på klientens mottagnings fönster för TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-161">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-162">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-162">Return Values</span></span>

 - <span data-ttu-id="8d4f3-163">**NX_SUCCESS** (0X00) http-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="8d4f3-163">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
 - <span data-ttu-id="8d4f3-164">NX_PTR_ERROR (0x07) ogiltig pekare för HTTP, ip_ptr eller Packet pool</span><span class="sxs-lookup"><span data-stu-id="8d4f3-164">NX_PTR_ERROR (0x07) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
 - <span data-ttu-id="8d4f3-165">NX_HTTP_POOL_ERROR (0xE9) ogiltig nytto Last storlek i Packet bassäng</span><span class="sxs-lookup"><span data-stu-id="8d4f3-165">NX_HTTP_POOL_ERROR (0xE9) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-166">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-166">Allowed From</span></span>

<span data-ttu-id="8d4f3-167">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-167">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-168">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-168">Example</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="8d4f3-169">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="8d4f3-169">nx_http_client_delete</span></span>

<span data-ttu-id="8d4f3-170">Ta bort en HTTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="8d4f3-170">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-171">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-171">Prototype</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="8d4f3-172">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-172">Description</span></span>

<span data-ttu-id="8d4f3-173">Den här tjänsten tar bort en tidigare skapad HTTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-173">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-174">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-174">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-175">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-175">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-176">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-176">Return Values</span></span>

 - <span data-ttu-id="8d4f3-177">**NX_SUCCESS** (0X00) http-klientbegäran har tagits bort</span><span class="sxs-lookup"><span data-stu-id="8d4f3-177">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
 - <span data-ttu-id="8d4f3-178">NX_PTR_ERROR (0x07) ogiltig HTTP-pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-178">NX_PTR_ERROR (0x07) Invalid HTTP pointer</span></span>
 - <span data-ttu-id="8d4f3-179">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-179">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-180">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-180">Allowed From</span></span>

<span data-ttu-id="8d4f3-181">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-181">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-182">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-182">Example</span></span>

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="8d4f3-183">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="8d4f3-183">nx_http_client_get_start</span></span>

<span data-ttu-id="8d4f3-184">Starta en HTTP GET-begäran över IPv4</span><span class="sxs-lookup"><span data-stu-id="8d4f3-184">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-185">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-185">Prototype</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-186">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-186">Description</span></span>

<span data-ttu-id="8d4f3-187">Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-187">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8d4f3-188">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_http_client_get_packet* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-188">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-189">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-189">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8d4f3-190">Den här tjänsten fungerar bara över IPv4-nätverk.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-190">This service works only over IPv4 network.</span></span> <span data-ttu-id="8d4f3-191">För program som behöver ansluta till ett IPv6-nätverk ska *nxd_http_client_get_start_extended ()* användas.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-191">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="8d4f3-192">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-192">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-193">Utvecklare uppmanas att migrera till *nx_http_client_get_start_extended ()* eller *nxd_http_client_get_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-193">Developers are encouraged to migrate to *nx_http_client_get_start_extended()* or *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-194">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-194">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-195">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-195">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-196">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-196">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-197">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-197">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-198">**input_ptr** Pekare till ytterligare data för GET-begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-198">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="8d4f3-199">Detta är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-199">This is optional.</span></span> <span data-ttu-id="8d4f3-200">Om detta är giltigt placeras angivna indata i meddelandets innehålls områden och ett inlägg används i stället för en GET-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-200">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="8d4f3-201">**input_size** Antal byte i valfria ytterligare invärden som pekas av ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="8d4f3-201">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="8d4f3-202">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-202">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-203">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-203">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-204">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-204">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8d4f3-205">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-205">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="8d4f3-206">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-206">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-208">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-208">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-209">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-209">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-210">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-210">Return Values</span></span>

 - <span data-ttu-id="8d4f3-211">**NX_SUCCESS** (0X00) http-klient har skickats.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-211">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="8d4f3-212">Hämta Start meddelande.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-212">GET start message.</span></span>
 - <span data-ttu-id="8d4f3-213">**NX_HTTP_ERROR** (0XE0) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-213">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="8d4f3-214">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-215">**NX_HTTP_FAILED** (0XE2) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-215">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-216">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="8d4f3-217">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-217">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-218">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-218">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-219">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-219">Allowed From</span></span>

<span data-ttu-id="8d4f3-220">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-221">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-221">Example</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="8d4f3-222">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-222">nx_http_client_get_start_extended</span></span>

<span data-ttu-id="8d4f3-223">Starta en HTTP GET-begäran över IPv4</span><span class="sxs-lookup"><span data-stu-id="8d4f3-223">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-224">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-224">Prototype</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-225">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-225">Description</span></span>

<span data-ttu-id="8d4f3-226">Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-226">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8d4f3-227">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_http_client_get_packet* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-227">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-228">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-228">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8d4f3-229">Den här tjänsten fungerar bara över IPv4-nätverk.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-229">This service works only over IPv4 network.</span></span> <span data-ttu-id="8d4f3-230">För program som behöver ansluta till ett IPv6-nätverk ska *nxd_http_client_get_start_extended ()* användas.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-230">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="8d4f3-231">Den här tjänsten ersätter *nx_http_client_get_start ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-231">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="8d4f3-232">Den kräver att anroparen anger längden på resursen, användar namnet och lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-232">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-233">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-233">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-234">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-234">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-235">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-235">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-236">**resurs pekare** till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-236">**resource Pointer** to URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-237">**resource_length** Längd på URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-237">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-238">**input_ptr** Pekare till ytterligare data för GET-begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-238">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="8d4f3-239">Detta är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-239">This is optional.</span></span> <span data-ttu-id="8d4f3-240">Om detta är giltigt placeras angivna indata i meddelandets innehålls områden och ett inlägg används i stället för en GET-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-240">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="8d4f3-241">**input_size** Antal byte i valfria ytterligare invärden som pekas av ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="8d4f3-241">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="8d4f3-242">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-242">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-243">**username_length** Längden på det valfria användar namnet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-243">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-244">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-244">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-245">**password_length** Det valfria lösen ordets längd för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-245">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-246">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-246">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8d4f3-247">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-248">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-248">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-250">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-250">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-251">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-251">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-252">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-252">Return Values</span></span>

 - <span data-ttu-id="8d4f3-253">**NX_SUCCESS** (0X00) http-klient har skickats.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-253">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="8d4f3-254">Hämta Start meddelande</span><span class="sxs-lookup"><span data-stu-id="8d4f3-254">GET start message</span></span>
 - <span data-ttu-id="8d4f3-255">**NX_HTTP_ERROR** (0XE0) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-255">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="8d4f3-256">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-257">**NX_HTTP_FAILED** (0XE2) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-257">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-258">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="8d4f3-259">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-259">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-260">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-260">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-261">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-261">Allowed From</span></span>

<span data-ttu-id="8d4f3-262">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-262">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-263">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-263">Example</span></span>

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a><span data-ttu-id="8d4f3-264">nxd_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="8d4f3-264">nxd_http_client_get_start</span></span>

<span data-ttu-id="8d4f3-265">Skicka en HTTP GET-begäran (IPv4 eller IPv6)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-265">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-266">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-266">Prototype</span></span>

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-267">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-267">Description</span></span>

<span data-ttu-id="8d4f3-268">Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-268">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8d4f3-269">Den kan användas för att ansluta till IPv4-eller IPv6-nätverk.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-269">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="8d4f3-270">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_http_client_get_packet* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-270">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
><span data-ttu-id="8d4f3-271">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-271">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8d4f3-272">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-272">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-273">Utvecklare uppmanas att migrera till *nxd_http_client_get_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-273">Developers are encouraged to migrate to *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-274">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-274">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-275">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-275">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-276">**Server_ip** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-276">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-277">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-277">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-278">**input_ptr** Pekare till ytterligare data för GET-begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-278">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="8d4f3-279">Detta är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-279">This is optional.</span></span> <span data-ttu-id="8d4f3-280">Om detta är giltigt placeras angivna indata i meddelandets innehålls områden och ett inlägg används i stället för en GET-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-280">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="8d4f3-281">**input_size** Antal byte i valfria ytterligare invärden som pekas av ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="8d4f3-281">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="8d4f3-282">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-282">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-283">**username_length** Längden på det valfria användar namnet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-283">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-284">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-284">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-285">**password_length** Det valfria lösen ordets längd för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-285">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-286">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-286">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8d4f3-287">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-287">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-288">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-288">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-290">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-290">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-291">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-291">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-292">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-292">Return Values</span></span>

 - <span data-ttu-id="8d4f3-293">**NX_SUCCESS** (0X00) har skickat GET-begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-293">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="8d4f3-294">**NX_HTTP_PASSWORD_TOO_LONG** (0XF0) lösen ord överskrider buffertstorleken</span><span class="sxs-lookup"><span data-stu-id="8d4f3-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="8d4f3-295">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-296">**NX_HTTP_FAILED** (0XE2) ogiltiga paket parametrar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-296">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="8d4f3-297">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn eller lösen ord</span><span class="sxs-lookup"><span data-stu-id="8d4f3-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="8d4f3-298">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-298">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-299">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-299">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-300">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-300">Allowed From</span></span>

<span data-ttu-id="8d4f3-301">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-302">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-302">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a><span data-ttu-id="8d4f3-303">nxd_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-303">nxd_http_client_get_start_extended</span></span>

<span data-ttu-id="8d4f3-304">Skicka en HTTP GET-begäran (IPv4 eller IPv6)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-304">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-305">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-305">Prototype</span></span>

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-306">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-306">Description</span></span>

<span data-ttu-id="8d4f3-307">Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-307">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8d4f3-308">Den kan användas för att ansluta till IPv4-eller IPv6-nätverk.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-308">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="8d4f3-309">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_http_client_get_packet* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-309">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-310">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-310">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8d4f3-311">Den här tjänsten ersätter *nxd_http_client_get_start ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-311">This service replaces *nxd_http_client_get_start()*.</span></span> <span data-ttu-id="8d4f3-312">Den kräver att anroparen anger längden på resursen, användar namnet och lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-312">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-313">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-313">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-314">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-314">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-315">**Server_ip** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-315">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-316">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-316">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-317">**resource_length** Längd på URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-317">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-318">**input_ptr** Pekare till ytterligare data för GET-begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-318">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="8d4f3-319">Detta är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-319">This is optional.</span></span> <span data-ttu-id="8d4f3-320">Om detta är giltigt placeras angivna indata i meddelandets innehålls områden och ett inlägg används i stället för en GET-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-320">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="8d4f3-321">**input_size** Antal byte i valfria ytterligare invärden som pekas av ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="8d4f3-321">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="8d4f3-322">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-322">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-323">**username_length** Längden på det valfria användar namnet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-323">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-324">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-324">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-325">**password_length** Det valfria lösen ordets längd för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-325">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-326">**wait_option** Definierar hur länge tjänsten ska vänta på att det ska gå att bearbeta HTTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-326">**wait_option** Defines how long the service will wait internally to process the HTTP Client get start.</span></span> <span data-ttu-id="8d4f3-327">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-327">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-328">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-328">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-330">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-330">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-331">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-331">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-332">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-332">Return Values</span></span>

 - <span data-ttu-id="8d4f3-333">**NX_SUCCESS** (0X00) har skickat GET-begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-333">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="8d4f3-334">**NX_HTTP_PASSWORD_TOO_LONG** (0XF0) lösen ord överskrider buffertstorleken</span><span class="sxs-lookup"><span data-stu-id="8d4f3-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="8d4f3-335">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-336">**NX_HTTP_FAILED** (0XE2) ogiltiga paket parametrar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-336">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="8d4f3-337">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn eller lösen ord</span><span class="sxs-lookup"><span data-stu-id="8d4f3-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="8d4f3-338">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-338">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-339">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-339">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-340">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-340">Allowed From</span></span>

<span data-ttu-id="8d4f3-341">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-342">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-342">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="8d4f3-343">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-343">nx_http_client_get_packet</span></span>

<span data-ttu-id="8d4f3-344">Hämta nästa resurs data paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-344">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-345">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-345">Prototype</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-346">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-346">Description</span></span>

<span data-ttu-id="8d4f3-347">Den här tjänsten hämtar nästa innehålls paket för resursen som begärdes av föregående *nx_http_client_get_start* -anrop.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-347">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="8d4f3-348">Efterföljande anrop till den här rutinen bör göras tills retur statusen för NX_HTTP_GET_DONE tas emot.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-348">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-349">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-349">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-350">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-350">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-351">**packet_ptr** Mål för paket pekare som innehåller partiellt resurs innehåll.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-351">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
 - <span data-ttu-id="8d4f3-352">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klienten ska hämta paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-352">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="8d4f3-353">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-353">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-354">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-354">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-356">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-356">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-357">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-357">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-358">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-358">Return Values</span></span>

 - <span data-ttu-id="8d4f3-359">**NX_SUCCESS** (0X00) http-klient hämta paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-359">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
 - <span data-ttu-id="8d4f3-360">**NX_HTTP_GET_DONE** (0XEC) http-klient hämta paket har slutförts</span><span class="sxs-lookup"><span data-stu-id="8d4f3-360">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
 - <span data-ttu-id="8d4f3-361">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte i get-läge.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
 - <span data-ttu-id="8d4f3-362">**NX_HTTP_BAD_PACKET_LENGTH** (0XED) ogiltig paket längd</span><span class="sxs-lookup"><span data-stu-id="8d4f3-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="8d4f3-363">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-363">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-364">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-364">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-365">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-365">Allowed From</span></span>

<span data-ttu-id="8d4f3-366">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-366">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-367">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-367">Example</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="8d4f3-368">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="8d4f3-368">nx_http_client_put_start</span></span>

<span data-ttu-id="8d4f3-369">Starta en HTTP-begäran över IPv4</span><span class="sxs-lookup"><span data-stu-id="8d4f3-369">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-370">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-370">Prototype</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-371">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-371">Description</span></span>

<span data-ttu-id="8d4f3-372">Den här tjänsten försöker skicka en skicka begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-372">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="8d4f3-373">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-373">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-374">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-374">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8d4f3-375">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-375">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-376">Utvecklare uppmanas att migrera till *nxd_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-376">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-377">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-377">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-378">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-378">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-379">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-379">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-380">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-380">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-381">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-381">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-382">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-382">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-383">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-383">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8d4f3-384">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_http_client_put_packet* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-384">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="8d4f3-385">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klientens placering ska starta.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-385">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="8d4f3-386">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-386">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-387">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-387">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-389">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-389">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-390">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-serverns svar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-390">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-391">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-391">Return Values</span></span>

 - <span data-ttu-id="8d4f3-392">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="8d4f3-392">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="8d4f3-393">**NX_HTTP_USERNAME_TOO_LONG** (0XF1) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="8d4f3-394">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-395">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-395">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-396">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="8d4f3-396">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="8d4f3-397">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-397">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-398">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-398">Allowed From</span></span>

<span data-ttu-id="8d4f3-399">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-400">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-400">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="8d4f3-401">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-401">nx_http_client_put_start_extended</span></span>

<span data-ttu-id="8d4f3-402">Starta en HTTP-begäran över IPv4</span><span class="sxs-lookup"><span data-stu-id="8d4f3-402">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-403">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-403">Prototype</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-404">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-404">Description</span></span>

<span data-ttu-id="8d4f3-405">Den här tjänsten försöker skicka en skicka begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-405">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="8d4f3-406">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-406">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-407">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-407">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8d4f3-408">Den här tjänsten ersätter *nx_http_client_put_start ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-408">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="8d4f3-409">Den kräver att anroparen anger längden på resursen, användar namnet och lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-409">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-410">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-410">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-411">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-411">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-412">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-412">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-413">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-413">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-414">**resource_length** Längd på URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-414">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="8d4f3-415">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-415">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-416">**username_length** Längden på det valfria användar namnet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-416">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-417">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-417">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-418">**password_length** Det valfria lösen ordets längd för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-418">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-419">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-419">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8d4f3-420">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_http_client_put_packet* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-420">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="8d4f3-421">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klientens placering ska starta.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-421">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="8d4f3-422">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-422">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-423">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-423">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-425">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-425">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-426">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-426">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-427">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-427">Return Values</span></span>

 - <span data-ttu-id="8d4f3-428">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="8d4f3-428">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="8d4f3-429">**NX_HTTP_USERNAME_TOO_LONG** (0XF1) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="8d4f3-430">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-431">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-431">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-432">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="8d4f3-432">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="8d4f3-433">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-433">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-434">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-434">Allowed From</span></span>

<span data-ttu-id="8d4f3-435">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-436">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-436">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a><span data-ttu-id="8d4f3-437">nxd_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="8d4f3-437">nxd_http_client_put_start</span></span>

<span data-ttu-id="8d4f3-438">Starta en HTTP-begäran (IPv4 eller IPv6)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-438">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-439">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-439">Prototype</span></span>

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-440">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-440">Description</span></span>

<span data-ttu-id="8d4f3-441">Den här tjänsten försöker placera (skicka) den angivna resursen på HTTP-servern på den angivna IP-adressen via IPv6.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-441">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="8d4f3-442">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-442">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-443">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-443">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8d4f3-444">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-444">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-445">Utvecklare uppmanas att migrera till *nxd_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-445">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-446">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-446">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-447">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-447">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-448">**server_ip** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-448">**server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-449">**resurs** Pekare till URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-449">**resource** Pointer to URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="8d4f3-450">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-450">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-451">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-451">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-452">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-452">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8d4f3-453">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_http_client_put_packet* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-453">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="8d4f3-454">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klientens placering ska starta.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-454">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="8d4f3-455">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-455">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-456">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-456">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-458">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-458">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-459">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-459">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-460">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-460">Return Values</span></span>

 - <span data-ttu-id="8d4f3-461">**NX_SUCCESS** (0X00) har skickat begäran om http-klientbegäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-461">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="8d4f3-462">**NX_HTTP_ERROR** (0XE0) http-klient internt fel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-462">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="8d4f3-463">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-464">**NX_HTTP_FAILED** (0XE2) http-klient fel vid kommunikation med HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="8d4f3-464">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="8d4f3-465">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-465">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-466">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="8d4f3-466">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="8d4f3-467">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-468">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-468">Allowed From</span></span>

<span data-ttu-id="8d4f3-469">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-470">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-470">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a><span data-ttu-id="8d4f3-471">nxd_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-471">nxd_http_client_put_start_extended</span></span>

<span data-ttu-id="8d4f3-472">Starta en HTTP-begäran (IPv4 eller IPv6)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-472">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-473">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-473">Prototype</span></span>

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-474">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-474">Description</span></span>

<span data-ttu-id="8d4f3-475">Den här tjänsten försöker placera (skicka) den angivna resursen på HTTP-servern på den angivna IP-adressen via IPv6.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-475">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="8d4f3-476">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-476">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-477">Resurs strängen kan referera till en lokal fil, t. ex. ``` “/index.htm” ``` , eller så kan den referera till en annan URL, t. ex. ```http://abc.website.com/index.htm``` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-477">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8d4f3-478">Den här tjänsten ersätter *nxd_http_client_put_start ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-478">This service replaces *nxd_http_client_put_start()*.</span></span> <span data-ttu-id="8d4f3-479">Den kräver att anroparen anger längden på resursen, användar namnet och lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-479">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-480">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-480">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-481">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-481">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-482">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-482">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-483">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-483">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="8d4f3-484">**resource_length** Längd på URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-484">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="8d4f3-485">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-485">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-486">**username_length** Längden på det valfria användar namnet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-486">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="8d4f3-487">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-487">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-488">**password_length** Det valfria lösen ordets längd för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-488">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="8d4f3-489">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-489">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8d4f3-490">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_http_client_put_packet* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-490">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="8d4f3-491">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klientens placering ska starta.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-491">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="8d4f3-492">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-492">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-493">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-493">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-495">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-495">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-496">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-496">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-497">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-497">Return Values</span></span>

 - <span data-ttu-id="8d4f3-498">**NX_SUCCESS** (0X00) har skickat begäran om http-klientbegäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-498">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="8d4f3-499">**NX_HTTP_ERROR** (0XE0) http-klient internt fel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-499">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="8d4f3-500">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-501">NX_HTTP_FAILED (0xE2) HTTP-klient fel vid kommunikation med HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="8d4f3-501">NX_HTTP_FAILED (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="8d4f3-502">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-502">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-503">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="8d4f3-503">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="8d4f3-504">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-504">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-505">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-505">Allowed From</span></span>

<span data-ttu-id="8d4f3-506">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-507">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-507">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="8d4f3-508">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-508">nx_http_client_put_packet</span></span>

<span data-ttu-id="8d4f3-509">Skicka nästa resurs data paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-509">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-510">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-510">Prototype</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8d4f3-511">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-511">Description</span></span>

<span data-ttu-id="8d4f3-512">Den här tjänsten försöker skicka nästa paket med resurs innehåll till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-512">This service attempts to send the next packet of resource content to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-513">Den här rutinen bör anropas upprepade gånger tills den kombinerade längden på de paket som skickas är lika med "total_bytes" som anges i föregående *nx_http_client_put_start* -anrop.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-513">This routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start* call.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-514">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-514">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-515">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-515">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-516">**packet_ptr** Pekare till nästa innehåll i resursen som ska skickas till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-516">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
 - <span data-ttu-id="8d4f3-517">**wait_option** Definierar hur länge tjänsten ska vänta internt på att bearbeta HTTP-klientens paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-517">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="8d4f3-518">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-518">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8d4f3-519">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-519">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="8d4f3-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="8d4f3-521">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-521">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="8d4f3-522">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-522">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-523">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-523">Return Values</span></span>

 - <span data-ttu-id="8d4f3-524">**NX_SUCCESS** (0x00) skickade http-klient paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-524">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
 - <span data-ttu-id="8d4f3-525">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="8d4f3-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0XEE) tog emot Server fel kod</span><span class="sxs-lookup"><span data-stu-id="8d4f3-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code</span></span>
 - <span data-ttu-id="8d4f3-527">**NX_HTTP_BAD_PACKET_LENGTH** (0XED) ogiltig paket längd</span><span class="sxs-lookup"><span data-stu-id="8d4f3-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="8d4f3-528">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn och/eller lösen ord</span><span class="sxs-lookup"><span data-stu-id="8d4f3-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
 - <span data-ttu-id="8d4f3-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** -servern (0xEF) svarar innan den har slutförts</span><span class="sxs-lookup"><span data-stu-id="8d4f3-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
 - <span data-ttu-id="8d4f3-530">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-530">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-531">NX_INVALID_PACKET-paketet (0x12) är för litet för TCP-huvud</span><span class="sxs-lookup"><span data-stu-id="8d4f3-531">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
 - <span data-ttu-id="8d4f3-532">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-532">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-533">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-533">Allowed From</span></span>

<span data-ttu-id="8d4f3-534">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-535">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-535">Example</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="8d4f3-536">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="8d4f3-536">nx_http_client_set_connect_port</span></span>

<span data-ttu-id="8d4f3-537">Ange anslutnings porten till servern</span><span class="sxs-lookup"><span data-stu-id="8d4f3-537">Set the connection port to the Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-538">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-538">Prototype</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a><span data-ttu-id="8d4f3-539">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-539">Description</span></span>

<span data-ttu-id="8d4f3-540">Den här tjänsten ändrar anslutnings porten vid anslutning till HTTP-servern till den angivna porten vid körning.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-540">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="8d4f3-541">Annars är anslutnings porten standardvärdet 80.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-541">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="8d4f3-542">Detta måste anropas före *nx_http_client_get_start ()* och *nx_http_client_put_start ()* , t. ex. När http-klienten ansluter till servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-542">This must be called before *nx_http_client_get_start()* and *nx_http_client_put_start()* e.g. when the HTTP Client connects with the Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-543">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-543">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-544">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-544">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="8d4f3-545">**port** Port för att ansluta till servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-545">**port** Port for connecting to the Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-546">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-546">Return Values</span></span>

 - <span data-ttu-id="8d4f3-547">**NX_SUCCESS** (0x00) ändrade porten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-547">**NX_SUCCESS** (0x00) Successfully change port</span></span>
 - <span data-ttu-id="8d4f3-548">NX_INVALID_PORT-porten (0x46) överskrider max gränsen (0xFFFF) eller är noll</span><span class="sxs-lookup"><span data-stu-id="8d4f3-548">NX_INVALID_PORT (0x46) Port exceeds the maximum (0xFFFF) or is zero</span></span>
 - <span data-ttu-id="8d4f3-549">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-549">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-550">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-550">Allowed From</span></span>

<span data-ttu-id="8d4f3-551">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="8d4f3-551">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-552">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-552">Example</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="8d4f3-553">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="8d4f3-553">nx_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="8d4f3-554">Ange återanropet för att hämta URL-högsta ålder och datum</span><span class="sxs-lookup"><span data-stu-id="8d4f3-554">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-555">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-555">Prototype</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a><span data-ttu-id="8d4f3-556">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-556">Description</span></span>

<span data-ttu-id="8d4f3-557">Den här tjänsten anger den callback-tjänst som anropas för att hämta den maximala ålder och senaste ändrings datum för den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-557">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-558">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-558">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-559">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-559">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-560">**cache_info_get** Pekare till motringning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-560">**cache_info_get** Pointer to the callback</span></span>
 - <span data-ttu-id="8d4f3-561">**max_age** Pekare till högsta ålder för en resurs</span><span class="sxs-lookup"><span data-stu-id="8d4f3-561">**max_age** Pointer to maximum age of a resource</span></span>
 - <span data-ttu-id="8d4f3-562">**data** Pekare till senaste ändrings datum som returnerades.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-562">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-563">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-563">Return Values</span></span>

 - <span data-ttu-id="8d4f3-564">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-564">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="8d4f3-565">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-565">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-566">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-566">Allowed From</span></span>

<span data-ttu-id="8d4f3-567">Initiering</span><span class="sxs-lookup"><span data-stu-id="8d4f3-567">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-568">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-568">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="8d4f3-569">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="8d4f3-569">nx_http_server_callback_data_send</span></span>

<span data-ttu-id="8d4f3-570">Skicka data från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-570">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-571">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-571">Prototype</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="8d4f3-572">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-572">Description</span></span>

<span data-ttu-id="8d4f3-573">Den här tjänsten skickar data i det angivna paketet från programmets callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-573">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="8d4f3-574">Detta används vanligt vis för att skicka dynamiska data som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-574">This is typically used to send dynamic data associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-575">Om den här funktionen används ansvarar återkallnings rutinen för att skicka hela svaret i rätt format.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-575">If this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="8d4f3-576">Dessutom måste återanrops rutinen returnera status för NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-576">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-577">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-577">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-578">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-578">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-579">**data_ptr** Pekare till de data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-579">**data_ptr** Pointer to the data to send.</span></span>
 - <span data-ttu-id="8d4f3-580">**data_length**  Antal byte som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-580">**data_length**  Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-581">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-581">Return Values</span></span>

 - <span data-ttu-id="8d4f3-582">**NX_SUCCESS** (0X00) har skickat Server data</span><span class="sxs-lookup"><span data-stu-id="8d4f3-582">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
 - <span data-ttu-id="8d4f3-583">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-583">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-584">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-584">Allowed From</span></span>

<span data-ttu-id="8d4f3-585">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-586">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-586">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="8d4f3-587">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="8d4f3-587">nx_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="8d4f3-588">Skapa ett svars huvud i en callback-funktion</span><span class="sxs-lookup"><span data-stu-id="8d4f3-588">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-589">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-589">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="8d4f3-590">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-590">Description</span></span>

<span data-ttu-id="8d4f3-591">Den här tjänsten anropar den interna funktionen *_nx_http_server_generate_response_header* när HTTP-servern svarar på klienten get-, Delete-och Delete-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-591">This service calls the internal function *_nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="8d4f3-592">Den är avsedd att användas i funktioner för återanrop i HTTP-server när HTTP-serverprogrammet utformar sitt svar på klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-592">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="8d4f3-593">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-593">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-594">Utvecklare uppmanas att migrera till *nxd_http_server_callback_generate_response_header_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-594">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-595">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-595">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-596">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-596">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-597">**packet_pptr** Pekar en paket pekare som har allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="8d4f3-597">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="8d4f3-598">**status_code** Indikerar resurs status.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-598">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="8d4f3-599">Exempel:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-599">Examples:</span></span>
    - <span data-ttu-id="8d4f3-600">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-600">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="8d4f3-601">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-601">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="8d4f3-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="8d4f3-603">**CONTENT_LENGTH** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="8d4f3-603">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="8d4f3-604">**content_type** Typ av HTTP, t. ex. "text/plain"</span><span class="sxs-lookup"><span data-stu-id="8d4f3-604">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="8d4f3-605">**additional_header** Pekare till ytterligare sidhuvud text</span><span class="sxs-lookup"><span data-stu-id="8d4f3-605">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-606">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-606">Return Values</span></span>

 - <span data-ttu-id="8d4f3-607">Ett huvud har skapats för **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-607">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="8d4f3-608">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-608">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-609">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-609">Allowed From</span></span>

<span data-ttu-id="8d4f3-610">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-610">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-611">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-611">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="8d4f3-612">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-612">nx_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="8d4f3-613">Skapa ett svars huvud i en callback-funktion</span><span class="sxs-lookup"><span data-stu-id="8d4f3-613">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-614">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-614">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="8d4f3-615">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-615">Description</span></span>

<span data-ttu-id="8d4f3-616">Den här tjänsten anropar den interna funktionen *_nx_http_server_generate_response_header ()* när HTTP-servern svarar på klienten get-, Delete-och Delete-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-616">This service calls the internal function *_nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="8d4f3-617">Den är avsedd att användas i funktioner för återanrop i HTTP-server när HTTP-serverprogrammet utformar sitt svar på klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-617">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="8d4f3-618">Den här tjänsten ersätter *nx_http_server_callback_generate_response_header ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-618">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="8d4f3-619">Den här versionen ger ytterligare längd information till callback-funktionen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-619">This version supplies additional length information to the callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-620">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-620">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-621">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-621">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-622">**packet_pptr** Pekar en paket pekare som har allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="8d4f3-622">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="8d4f3-623">**status_code** Indikerar resurs status.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-623">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="8d4f3-624">Exempel:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-624">Examples:</span></span>
    - <span data-ttu-id="8d4f3-625">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-625">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="8d4f3-626">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-626">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="8d4f3-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8d4f3-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="8d4f3-628">**status_code** Längd på status kod</span><span class="sxs-lookup"><span data-stu-id="8d4f3-628">**status_code** Length of status code</span></span>
 - <span data-ttu-id="8d4f3-629">**CONTENT_LENGTH** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="8d4f3-629">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="8d4f3-630">**content_type** Typ av HTTP, t. ex. "text/plain"</span><span class="sxs-lookup"><span data-stu-id="8d4f3-630">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="8d4f3-631">**content_type_length** Längd på HTTP-typ</span><span class="sxs-lookup"><span data-stu-id="8d4f3-631">**content_type_length** Length of HTTP type</span></span>
 - <span data-ttu-id="8d4f3-632">**additional_header** Pekare till ytterligare sidhuvud text</span><span class="sxs-lookup"><span data-stu-id="8d4f3-632">**additional_header** Pointer to additional header text</span></span>
 - <span data-ttu-id="8d4f3-633">**additional_header_length** Längd på ytterligare rubrik text</span><span class="sxs-lookup"><span data-stu-id="8d4f3-633">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-634">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-634">Return Values</span></span>

 - <span data-ttu-id="8d4f3-635">Ett huvud har skapats för **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-635">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="8d4f3-636">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-636">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-637">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-637">Allowed From</span></span>

<span data-ttu-id="8d4f3-638">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-638">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-639">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-639">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="8d4f3-640">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="8d4f3-640">nx_http_server_callback_packet_send</span></span>

<span data-ttu-id="8d4f3-641">Skicka ett HTTP-paket från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-641">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-642">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-642">Prototype</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8d4f3-643">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-643">Description</span></span>

<span data-ttu-id="8d4f3-644">Den här tjänsten skickar ett fullständigt HTTP-servernamn från ett HTTP-motanrop.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-644">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="8d4f3-645">HTTP-servern skickar paketet med NX_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-645">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="8d4f3-646">HTTP-huvudet och data måste läggas till i paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-646">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="8d4f3-647">Om retur statusen indikerar ett fel, måste HTTP-programmet släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-647">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="8d4f3-648">Återanropet ska returnera NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-648">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8d4f3-649">Se *nx_http_server_callback_generate_response_header ()* för ett mer detaljerat exempel.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-649">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-650">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-650">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-651">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-651">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-652">**packet_ptr** Pekare till det paket som ska skickas</span><span class="sxs-lookup"><span data-stu-id="8d4f3-652">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-653">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-653">Return Values</span></span>

 - <span data-ttu-id="8d4f3-654">**NX_SUCCESS** (0X00) har skickat Server paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-654">**NX_SUCCESS** (0x00) Successfully sent Server packet</span></span>
 - <span data-ttu-id="8d4f3-655">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-655">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-656">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-656">Allowed From</span></span>

<span data-ttu-id="8d4f3-657">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-657">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-658">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-658">Example</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="8d4f3-659">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="8d4f3-659">nx_http_server_callback_response_send</span></span>

<span data-ttu-id="8d4f3-660">Skicka svar från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-660">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-661">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-661">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="8d4f3-662">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-662">Description</span></span>

<span data-ttu-id="8d4f3-663">Den här tjänsten skickar den levererade svars informationen från appens callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-663">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="8d4f3-664">Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-664">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-665">Om den här funktionen används måste återanrops rutinen returnera status för NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-665">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8d4f3-666">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-666">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-667">Utvecklare uppmanas att migrera till *nxd_http_server_callback_response_send_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-667">Developers are encouraged to migrate to *nxd_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-668">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-668">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-669">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-669">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-670">**sidhuvud** Pekar mot svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-670">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="8d4f3-671">**information** Pekar mot informations strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-671">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="8d4f3-672">**additional_info** Pekare till den ytterligare informations strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-672">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-673">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-673">Return Values</span></span>

 - <span data-ttu-id="8d4f3-674">**NX_SUCCESS** (0x00) skickade Server svaret</span><span class="sxs-lookup"><span data-stu-id="8d4f3-674">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-675">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-675">Allowed From</span></span>

<span data-ttu-id="8d4f3-676">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-677">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-677">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="8d4f3-678">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-678">nx_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="8d4f3-679">Skicka svar från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-679">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-680">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-680">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="8d4f3-681">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-681">Description</span></span>

<span data-ttu-id="8d4f3-682">Den här tjänsten skickar den levererade svars informationen från appens callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-682">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="8d4f3-683">Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-683">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-684">Om den här funktionen används måste återanrops rutinen returnera status för NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-684">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8d4f3-685">Den här tjänsten ersätter *nx_http_server_callback_response_send ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-685">This service replaces *nx_http_server_callback_response_send()*.</span></span> <span data-ttu-id="8d4f3-686">Den här versionen tar ytterligare längd information som argument.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-686">This version takes additional length information as arguments.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-687">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-687">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-688">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-688">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-689">**sidhuvud** Pekar mot svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-689">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="8d4f3-690">**header_length** Längd på svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-690">**header_length** Length of the response header string.</span></span>
 - <span data-ttu-id="8d4f3-691">**information** Pekar mot informations strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-691">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="8d4f3-692">**information_length** Längden på informations strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-692">**information_length** Length of the information string.</span></span>
 - <span data-ttu-id="8d4f3-693">**additional_info** Pekare till den ytterligare informations strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-693">**additional_info** Pointer to the additional information string.</span></span>
 - <span data-ttu-id="8d4f3-694">**additional_info_length** Den ytterligare informations strängens längd.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-694">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-695">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-695">Return Values</span></span>

 - <span data-ttu-id="8d4f3-696">**NX_SUCCESS** (0x00) skickade Server svaret</span><span class="sxs-lookup"><span data-stu-id="8d4f3-696">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-697">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-697">Allowed From</span></span>

<span data-ttu-id="8d4f3-698">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-698">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-699">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-699">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="8d4f3-700">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="8d4f3-700">nx_http_server_content_get</span></span>

<span data-ttu-id="8d4f3-701">Hämta innehåll från begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-701">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-702">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-702">Prototype</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="8d4f3-703">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-703">Description</span></span>

<span data-ttu-id="8d4f3-704">Den här tjänsten försöker hämta den angivna mängden innehåll från begäran eller skicka HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-704">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="8d4f3-705">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-705">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="8d4f3-706">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-706">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-707">Utvecklare uppmanas att migrera till *nx_http_server_content_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-707">Developers are encouraged to migrate to *nx_http_server_content_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-708">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-708">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-709">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-709">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-710">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-710">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8d4f3-711">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-711">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="8d4f3-712">**byte_offset** Antal byte som ska förskjutas i innehålls ytan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-712">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="8d4f3-713">**destination_ptr** Pekar till mål avsnittet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-713">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="8d4f3-714">**destination_size** Maximalt antal byte som är tillgängliga i mål arean.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-714">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="8d4f3-715">**actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-715">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-716">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-716">Return Values</span></span>

 - <span data-ttu-id="8d4f3-717">**NX_SUCCESS** (0X00) http-serverns innehåll Hämta</span><span class="sxs-lookup"><span data-stu-id="8d4f3-717">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
 - <span data-ttu-id="8d4f3-718">Internt fel för **NX_HTTP_ERROR** (0XE0) http-server</span><span class="sxs-lookup"><span data-stu-id="8d4f3-718">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="8d4f3-719">**NX_HTTP_DATA_END** (0XE7) slut på innehåll i begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-719">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="8d4f3-720">**NX_HTTP_TIMEOUT** (0xE1) timeout för http-server i Hämta nästa paket med innehåll</span><span class="sxs-lookup"><span data-stu-id="8d4f3-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
 - <span data-ttu-id="8d4f3-721">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-721">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-722">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-722">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-723">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-723">Allowed From</span></span>

<span data-ttu-id="8d4f3-724">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-724">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-725">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-725">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="8d4f3-726">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-726">nx_http_server_content_get_extended</span></span>

<span data-ttu-id="8d4f3-727">Hämta innehåll från begäran/har stöd för längd för längd innehåll</span><span class="sxs-lookup"><span data-stu-id="8d4f3-727">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-728">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-728">Prototype</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="8d4f3-729">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-729">Description</span></span>

<span data-ttu-id="8d4f3-730">Den här tjänsten är nästan identisk med *nx_http_server_content_get ().* den försöker hämta den angivna mängden innehåll från post-eller klient förfrågan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-730">This service is almost identical to *nx_http_server_content_get();* it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="8d4f3-731">Den hanterar dock begär Anden med innehålls längd noll (' Empty Request ') som en giltig begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-731">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="8d4f3-732">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-732">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8d4f3-733">Den här tjänsten ersätter *nx_http_server_content_get ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-733">This service replaces *nx_http_server_content_get()*.</span></span> <span data-ttu-id="8d4f3-734">Den här versionen kräver att anroparen tillhandahåller ytterligare längd information.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-734">This version requires caller to supply additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-735">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-735">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-736">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-736">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-737">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-737">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8d4f3-738">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-738">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="8d4f3-739">**byte_offset** Antal byte som ska förskjutas i innehålls ytan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-739">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="8d4f3-740">**destination_ptr** Pekar till mål avsnittet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-740">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="8d4f3-741">**destination_size** Maximalt antal byte som är tillgängliga i mål arean.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-741">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="8d4f3-742">**actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-742">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-743">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-743">Return Values</span></span>

 - <span data-ttu-id="8d4f3-744">**NX_SUCCESS** (0X00) http-innehållet Hämta</span><span class="sxs-lookup"><span data-stu-id="8d4f3-744">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
 - <span data-ttu-id="8d4f3-745">Internt fel för **NX_HTTP_ERROR** (0XE0) http-server</span><span class="sxs-lookup"><span data-stu-id="8d4f3-745">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="8d4f3-746">**NX_HTTP_DATA_END** (0XE7) slut på innehåll i begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-746">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="8d4f3-747">**NX_HTTP_TIMEOUT** (0xE1) timeout för http-server i Hämta nästa paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
 - <span data-ttu-id="8d4f3-748">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-748">NX_PTR_ERROR (0x07) Invalid  pointer input</span></span>
 - <span data-ttu-id="8d4f3-749">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-749">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-750">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-750">Allowed From</span></span>

<span data-ttu-id="8d4f3-751">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-752">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-752">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="8d4f3-753">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="8d4f3-753">nx_http_server_content_length_get</span></span>

<span data-ttu-id="8d4f3-754">Hämta längden på innehållet i begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-754">Get length of content in the request</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-755">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-755">Prototype</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8d4f3-756">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-756">Description</span></span>

<span data-ttu-id="8d4f3-757">Den här tjänsten försöker hämta HTTP-innehållets längd i det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-757">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="8d4f3-758">Om det inte finns något HTTP-innehåll returnerar den här rutinen värdet noll.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-758">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="8d4f3-759">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-759">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8d4f3-760">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-760">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-761">Utvecklare uppmanas att migrera till *nx_http_server_content_length_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-761">Developers are encouraged to migrate to *nx_http_server_content_length_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-762">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-762">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-763">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-763">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8d4f3-764">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-764">Note that this packet must not be released by the request notify callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-765">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-765">Return Values</span></span>

 - <span data-ttu-id="8d4f3-766">**innehålls längd** Vid fel returneras värdet noll</span><span class="sxs-lookup"><span data-stu-id="8d4f3-766">**content length** On error, a value of zero is returned</span></span>  

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-767">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-767">Allowed From</span></span>

<span data-ttu-id="8d4f3-768">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-768">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-769">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-769">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="8d4f3-770">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-770">nx_http_server_content_length_get_extended</span></span>

<span data-ttu-id="8d4f3-771">Hämta längden på innehållet i begäran/stöder innehålls längden noll värde</span><span class="sxs-lookup"><span data-stu-id="8d4f3-771">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-772">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-772">Prototype</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="8d4f3-773">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-773">Description</span></span>

<span data-ttu-id="8d4f3-774">Den här tjänsten liknar *nx_http_server_content_length_get.* försöker hämta http-innehållets längd i det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-774">This service is similar to *nx_http_server_content_length_get;* attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="8d4f3-775">Returvärdet visar dock att status för slut för ande har slutförts, och det faktiska värdet för längd returneras i inmatad pekare ```content_length``` .</span><span class="sxs-lookup"><span data-stu-id="8d4f3-775">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer ```content_length```.</span></span> <span data-ttu-id="8d4f3-776">Om det inte finns något HTTP-innehåll/innehålls längd = 0, returnerar den här rutinen fortfarande statusen slutförd och content_length inmatare pekar på en giltig längd (noll).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-776">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="8d4f3-777">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-777">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="8d4f3-778">Den här tjänsten ersätter *nx_http_server_content_length_get ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-778">This service replaces *nx_http_server_content_length_get()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-779">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-779">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-780">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-780">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8d4f3-781">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-781">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="8d4f3-782">**CONTENT_LENGTH** Pekare till värde som hämtats från fältet innehålls längd</span><span class="sxs-lookup"><span data-stu-id="8d4f3-782">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-783">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-783">Return Values</span></span>

 - <span data-ttu-id="8d4f3-784">**NX_SUCCESS** (0X00) lyckades Server innehåll Hämta</span><span class="sxs-lookup"><span data-stu-id="8d4f3-784">**NX_SUCCESS** (0x00) Successful Server content get</span></span>
 - <span data-ttu-id="8d4f3-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0XEF) felaktigt http-huvudformat</span><span class="sxs-lookup"><span data-stu-id="8d4f3-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
 - <span data-ttu-id="8d4f3-786">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-786">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-787">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-787">Allowed From</span></span>

<span data-ttu-id="8d4f3-788">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-789">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-789">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="8d4f3-790">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="8d4f3-790">nx_http_server_create</span></span>

<span data-ttu-id="8d4f3-791">Skapa en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="8d4f3-791">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-792">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-792">Prototype</span></span>

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="8d4f3-793">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-793">Description</span></span>

<span data-ttu-id="8d4f3-794">Den här tjänsten skapar en HTTP-serverinstans som körs i kontexten för en egen ThreadX-tråd.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-794">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="8d4f3-795">De valfria rutinerna för *authentication_check* och request_notify programbegäran ger program kontroll över den grundläggande driften av HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-795">The optional *authentication_check* and request_notify application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-796">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-796">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-797">**http_server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-797">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="8d4f3-798">**http_server_name** Pekare till HTTP-serverns namn.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-798">**http_server_name** Pointer to HTTP Server’s name.</span></span>
 - <span data-ttu-id="8d4f3-799">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-799">**ip_ptr** Pointer to previously created IP instance.</span></span>
 - <span data-ttu-id="8d4f3-800">**media_ptr** Pekare till den tidigare skapade FileX Media-instansen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-800">**media_ptr** Pointer to previously created FileX media instance.</span></span>
 - <span data-ttu-id="8d4f3-801">**stack_ptr** Pekar på ett stack-fält för HTTP-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-801">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
 - <span data-ttu-id="8d4f3-802">**stack_size** Pekare till HTTP-server trådens stack storlek.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-802">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
 - <span data-ttu-id="8d4f3-803">**authentication_check** Funktions pekare till programmets verifierings kontroll rutin.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-803">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="8d4f3-804">Den här rutinen anropas för varje HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-804">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="8d4f3-805">Om den här parametern är NULL utförs ingen autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-805">If this parameter is NULL, no authentication will be performed.</span></span>
 - <span data-ttu-id="8d4f3-806">**request_notify** Funktions pekare till program begär ande aviserings rutin.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-806">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="8d4f3-807">Den här rutinen anropas före HTTP-serverns bearbetning av begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-807">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="8d4f3-808">Detta gör att resurs namnet kan omdirigeras eller fält i en resurs uppdateras innan HTTP-klientbegäran slutförs.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-808">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-809">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-809">Return Values</span></span>

 - <span data-ttu-id="8d4f3-810">**NX_SUCCESS** (0X00) http-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-810">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
 - <span data-ttu-id="8d4f3-811">NX_PTR_ERROR (0x07) ogiltig pekare för HTTP-server, IP, media, stack eller Packet-pool.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-811">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
 - <span data-ttu-id="8d4f3-812">NX_HTTP_POOL_ERROR (0xE9) paket nytto lasten för poolen är inte tillräckligt stor för att rymma fullständig HTTP-begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-812">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-813">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-813">Allowed From</span></span>

<span data-ttu-id="8d4f3-814">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-814">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-815">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-815">Example</span></span>

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="8d4f3-816">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="8d4f3-816">nx_http_server_delete</span></span>

<span data-ttu-id="8d4f3-817">Ta bort en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="8d4f3-817">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-818">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-818">Prototype</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8d4f3-819">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-819">Description</span></span>

<span data-ttu-id="8d4f3-820">Den här tjänsten tar bort en tidigare skapad HTTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-820">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-821">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-821">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-822">**http_server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-822">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-823">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-823">Return Values</span></span>

 - <span data-ttu-id="8d4f3-824">**NX_SUCCESS** (0X00) http-servern har tagits bort</span><span class="sxs-lookup"><span data-stu-id="8d4f3-824">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
 - <span data-ttu-id="8d4f3-825">NX_PTR_ERROR (0x07) ogiltig HTTP-server pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-825">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
 - <span data-ttu-id="8d4f3-826">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-827">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-827">Allowed From</span></span>

<span data-ttu-id="8d4f3-828">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-828">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-829">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-829">Example</span></span>

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="8d4f3-830">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="8d4f3-830">nx_http_server_get_entity_content</span></span>

<span data-ttu-id="8d4f3-831">Hämta plats och längd för enhets data</span><span class="sxs-lookup"><span data-stu-id="8d4f3-831">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-832">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-832">Prototype</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="8d4f3-833">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-833">Description</span></span>

<span data-ttu-id="8d4f3-834">Den här tjänsten bestämmer platsen för starten av data i den aktuella flerdelade entiteten i mottagna klient meddelanden och längden på data som inte inkluderar begränsnings strängen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-834">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="8d4f3-835">Internt HTTP-Server uppdaterar sina egna förskjutningar så att den här funktionen kan anropas igen på samma klient-datagram för meddelanden med flera entiteter.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-835">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="8d4f3-836">Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-836">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-837">NX_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-837">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="8d4f3-838">Se [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) för mer information.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-838">See [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-839">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-839">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-840">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="8d4f3-840">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="8d4f3-841">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-841">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="8d4f3-842">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-842">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="8d4f3-843">**available_offset** Pekare för förskjutning av enhets data från paketets lägga-pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-843">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
 - <span data-ttu-id="8d4f3-844">**available_length** Pekare till längd på enhets data</span><span class="sxs-lookup"><span data-stu-id="8d4f3-844">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-845">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-845">Return Values</span></span>

 - <span data-ttu-id="8d4f3-846">**NX_SUCCESS** (0X00) har hämtat storlek och plats för enhetens innehåll</span><span class="sxs-lookup"><span data-stu-id="8d4f3-846">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
 - <span data-ttu-id="8d4f3-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) för HTTP-serverns interna flerdelade markörer finns redan</span><span class="sxs-lookup"><span data-stu-id="8d4f3-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server  internal multipart markers is already found</span></span>
 - <span data-ttu-id="8d4f3-848">Internt HTTP-fel NX_HTTP_ERROR (0xE0)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-848">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="8d4f3-849">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-849">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-850">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-850">Allowed From</span></span>

<span data-ttu-id="8d4f3-851">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-851">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-852">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-852">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="8d4f3-853">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="8d4f3-853">nx_http_server_get_entity_header</span></span>

<span data-ttu-id="8d4f3-854">Hämta innehållet i enhets huvudet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-854">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-855">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-855">Prototype</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="8d4f3-856">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-856">Description</span></span>

<span data-ttu-id="8d4f3-857">Den här tjänsten hämtar enhets rubriken till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-857">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="8d4f3-858">Internt HTTP-Server uppdaterar sin egen pekare för att hitta nästa flerdelade entitet i ett klient-datagram med flera entitets-rubriker.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-858">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="8d4f3-859">Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-859">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-860">NX_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-860">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-861">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-861">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-862">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="8d4f3-862">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="8d4f3-863">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-863">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="8d4f3-864">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-864">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="8d4f3-865">**entity_header_buffer** Pekare till plats för lagring av enhets huvud</span><span class="sxs-lookup"><span data-stu-id="8d4f3-865">**entity_header_buffer** Pointer to location to store entity header</span></span>
 - <span data-ttu-id="8d4f3-866">**buffer_size** Storlek på indatabufferten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-866">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-867">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-867">Return Values</span></span>

 - <span data-ttu-id="8d4f3-868">**NX_SUCCESS** (0X00) har hämtat enhets huvud</span><span class="sxs-lookup"><span data-stu-id="8d4f3-868">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
 - <span data-ttu-id="8d4f3-869">Det gick inte att hitta **NX_HTTP_NOT_FOUND** **(0xE6)** entitets huvud fält</span><span class="sxs-lookup"><span data-stu-id="8d4f3-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Entity header field not found</span></span>
 - <span data-ttu-id="8d4f3-870">**NX_HTTP_TIMEOUT** **(0xE1)** tid för att ta emot nästa paket för klient meddelande med multipaket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-870">**NX_HTTP_TIMEOUT** **(0xE1)** Time expired to receive next packet for multipacket client message</span></span>
 - <span data-ttu-id="8d4f3-871">Internt HTTP-fel NX_HTTP_ERROR (0xE0)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-871">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="8d4f3-872">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-872">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-873">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-873">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-874">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-874">Allowed From</span></span>

<span data-ttu-id="8d4f3-875">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-875">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-876">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-876">Example</span></span>

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
  NX_SUCCESS)
 {
                nx_packet_release(response_pkt);
     }
    }


}
else
{
    /* Indicate we have not processed the response to client yet.*/
    return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="8d4f3-877">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="8d4f3-877">nx_http_server_gmt_callback_set</span></span>

<span data-ttu-id="8d4f3-878">Ange återanropet för att få GMT-datum och-tid</span><span class="sxs-lookup"><span data-stu-id="8d4f3-878">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-879">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-879">Prototype</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="8d4f3-880">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-880">Description</span></span>

<span data-ttu-id="8d4f3-881">Den här tjänsten anger återanropet för att hämta GMT-datum och-tid med en tidigare skapad HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-881">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="8d4f3-882">Den här tjänsten anropas med HTTP-servern för att skapa en rubrik i HTTP-server svar på klienten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-882">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-883">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-883">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-884">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="8d4f3-884">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="8d4f3-885">**gmt_getv** Pekare till GMT-motanrop</span><span class="sxs-lookup"><span data-stu-id="8d4f3-885">**gmt_getv** Pointer to GMT callback</span></span>
 - <span data-ttu-id="8d4f3-886">**Datev** Pekare till det datum som hämtades</span><span class="sxs-lookup"><span data-stu-id="8d4f3-886">**datev** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-887">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-887">Return Values</span></span>

 - <span data-ttu-id="8d4f3-888">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-888">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="8d4f3-889">NX_PTR_ERROR (0x07) ogiltig paket-eller parameter pekare.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-889">NX_PTR_ERROR (0x07)  Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-890">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-890">Allowed From</span></span>

<span data-ttu-id="8d4f3-891">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-892">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-892">Example</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="8d4f3-893">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="8d4f3-893">nx_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="8d4f3-894">Ange motringning till för att hantera Ogiltig användare/lösen ord</span><span class="sxs-lookup"><span data-stu-id="8d4f3-894">Set the callback to to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-895">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-895">Prototype</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="8d4f3-896">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-896">Description</span></span>

<span data-ttu-id="8d4f3-897">Den här tjänsten anger återanropet som anropas när ett ogiltigt användar namn och lösen ord tas emot i en klient get-,-eller Delete-begäran, antingen av Digest eller grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-897">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="8d4f3-898">HTTP-servern måste ha skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-898">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-899">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-899">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-900">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="8d4f3-900">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="8d4f3-901">**invalid_username_password_callback** Pekare till Ogiltig användare/pass motringning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-901">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
 - <span data-ttu-id="8d4f3-902">**resurs** Pekare till resursen som anges av klienten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-902">**resource** Pointer to the resource specified by the client</span></span>
 - <span data-ttu-id="8d4f3-903">**client_address** Pekare till klient adress.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-903">**client_address** Pointer to client address.</span></span> <span data-ttu-id="8d4f3-904">Kan vara IPv4 eller IPv6</span><span class="sxs-lookup"><span data-stu-id="8d4f3-904">Can be IPv4 or IPv6</span></span>
 - <span data-ttu-id="8d4f3-905">**request_type** Anger typ av klient förfrågan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-905">**request_type** Indicates client request type.</span></span> <span data-ttu-id="8d4f3-906">Kanske:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-906">May be:</span></span>
    - <span data-ttu-id="8d4f3-907">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8d4f3-907">NX_HTTP_SERVER_GET_REQUEST</span></span>
    - <span data-ttu-id="8d4f3-908">NX_HTTP_SERVER_POST_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8d4f3-908">NX_HTTP_SERVER_POST_REQUEST</span></span>
    - <span data-ttu-id="8d4f3-909">NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8d4f3-909">NX_HTTP_SERVER_HEAD_REQUEST</span></span>
    - <span data-ttu-id="8d4f3-910">NX_HTTP_SERVER_PUT_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8d4f3-910">NX_HTTP_SERVER_PUT_REQUEST</span></span>
    - <span data-ttu-id="8d4f3-911">NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8d4f3-911">NX_HTTP_SERVER_DELETE_REQUEST</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-912">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-912">Return Values</span></span>

 - <span data-ttu-id="8d4f3-913">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-913">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="8d4f3-914">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-914">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-915">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-915">Allowed From</span></span>

<span data-ttu-id="8d4f3-916">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-916">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-917">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-917">Example</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="8d4f3-918">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="8d4f3-918">nx_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="8d4f3-919">Ange ytterligare MIME-mappningar för HTML</span><span class="sxs-lookup"><span data-stu-id="8d4f3-919">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-920">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-920">Prototype</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="8d4f3-921">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-921">Description</span></span>

<span data-ttu-id="8d4f3-922">Med den här tjänsten kan HTTP-programutvecklaren lägga till ytterligare MIME-typer från de standard-MIME-typer som tillhandahålls av NetX Duo HTTP-servern (se *nx_http_server_get_type* för lista över definierade typer).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-922">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX Duo HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="8d4f3-923">När en klientbegäran tas emot, t. ex. en GET-begäran, parsar HTTP-servern den begärda filtypen från HTTP-huvudet med en prioriterad uppsättning av ytterligare MIME-mappningar och om ingen matchning hittas söker den efter en matchning i standard-MIME-mappningen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-923">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="8d4f3-924">Om ingen matchning hittas är MIME-typen Standard text/plain.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-924">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="8d4f3-925">Om begär ande aviserings funktionen har registrerats med HTTP-servern kan aviseringen meddela motringning anropa *nx_http_server_type_retrieve ()* för att parsa filtypen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-925">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_retrieve()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-926">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-926">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-927">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-927">**server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="8d4f3-928">**mime_maps** Pekare till en MIME-kart mat ris</span><span class="sxs-lookup"><span data-stu-id="8d4f3-928">**mime_maps** Pointer to a MIME map array</span></span>
 - <span data-ttu-id="8d4f3-929">**mime_map_num** Antal MIME-mappningar i matrisen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-929">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-930">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-930">Return Values</span></span>

 - <span data-ttu-id="8d4f3-931">**NX_SUCCESS** (0X00) http-SERVERNS MIME-mappning har angetts</span><span class="sxs-lookup"><span data-stu-id="8d4f3-931">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
 - <span data-ttu-id="8d4f3-932">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-932">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-933">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-933">Allowed From</span></span>

<span data-ttu-id="8d4f3-934">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-934">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-935">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-935">Example</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="8d4f3-936">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="8d4f3-936">nx_http_server_packet_content_find</span></span>

<span data-ttu-id="8d4f3-937">Extrahera innehålls längd och ange pekare till början av data</span><span class="sxs-lookup"><span data-stu-id="8d4f3-937">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-938">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-938">Prototype</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="8d4f3-939">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-939">Description</span></span>

<span data-ttu-id="8d4f3-940">Den här tjänsten extraherar innehålls längden från HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-940">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="8d4f3-941">Den uppdaterar också det tillhandahållna paketet enligt följande: paketets lägga-pekare (start på platsen för den pakettyp som ska skrivas till) har angetts till HTTP-innehållet (data) precis skickade HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-941">It also  updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="8d4f3-942">Om början av innehållet inte hittas i det aktuella paketet väntar funktionen på nästa paket som ska tas emot med alternativet NX_HTTP_SERVER_TIMEOUT_RECEIVE vänta.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-942">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-943">Detta ska inte anropas innan *nx_http_server_get_entity_header* anropas eftersom den ändrar lägga-pekaren förbi enhets huvudet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-943">This should not be called before calling *nx_http_server_get_entity_header* because it modifies the prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-944">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-944">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-945">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-945">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="8d4f3-946">**packet_ptr** Pekare till paket pekare för att returnera paketet med uppdaterad lägga-pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-946">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
 - <span data-ttu-id="8d4f3-947">**CONTENT_LENGTH** Pekare som ska extraheras ```content_length```</span><span class="sxs-lookup"><span data-stu-id="8d4f3-947">**content_length** Pointer to extracted ```content_length```</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-948">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-948">Return Values</span></span>

 - <span data-ttu-id="8d4f3-949">**NX_SUCCESS** (0X00) http-innehålls längd hittades och paketet har uppdaterats</span><span class="sxs-lookup"><span data-stu-id="8d4f3-949">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
 - <span data-ttu-id="8d4f3-950">**NX_HTTP_TIMEOUT** (0XE1) tid för att vänta på nästa paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-950">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="8d4f3-951">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-951">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-952">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-952">Allowed From</span></span>

<span data-ttu-id="8d4f3-953">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-953">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-954">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-954">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="8d4f3-955">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="8d4f3-955">nx_http_server_packet_get</span></span>

<span data-ttu-id="8d4f3-956">Ta emot nästa HTTP-paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-956">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-957">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-957">Prototype</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8d4f3-958">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-958">Description</span></span>

<span data-ttu-id="8d4f3-959">Den här tjänsten returnerar nästa paket som tas emot på HTTP-serverns socket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-959">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="8d4f3-960">Alternativet vänte för att ta emot ett paket är NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-960">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-961">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-961">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-962">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-962">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="8d4f3-963">**packet_ptr** Pekare till mottaget paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-963">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-964">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-964">Return Values</span></span>

 - <span data-ttu-id="8d4f3-965">**NX_SUCCESS** (0X00) har tagit emot nästa paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-965">**NX_SUCCESS** (0x00) Successfully received next packet</span></span>
 - <span data-ttu-id="8d4f3-966">**NX_HTTP_TIMEOUT** (0XE1) tid för att vänta på nästa paket</span><span class="sxs-lookup"><span data-stu-id="8d4f3-966">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="8d4f3-967">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-967">NX_PTR_ERROR (0x07)  Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-968">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-968">Allowed From</span></span>

<span data-ttu-id="8d4f3-969">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-969">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-970">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-970">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="8d4f3-971">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="8d4f3-971">nx_http_server_param_get</span></span>

<span data-ttu-id="8d4f3-972">Hämta parameter från begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-972">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-973">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-973">Prototype</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="8d4f3-974">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-974">Description</span></span>

<span data-ttu-id="8d4f3-975">Den här tjänsten försöker hämta angiven HTTP URL-parameter i det angivna paketet för begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-975">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="8d4f3-976">Om den begärda HTTP-parametern inte finns, returnerar den här rutinen statusen NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-976">If the requested HTTP parameter is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="8d4f3-977">Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-977">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-978">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-978">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-979">**packet_ptr** Pekare till HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-979">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="8d4f3-980">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-980">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="8d4f3-981">**param_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i parameter listan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-981">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
 - <span data-ttu-id="8d4f3-982">**param_ptr** Mål arean för att kopiera parametern.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-982">**param_ptr** Destination area to copy the parameter.</span></span>
 - <span data-ttu-id="8d4f3-983">**max_param_size** Maximal storlek för parameter mål arean.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-983">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-984">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-984">Return Values</span></span>

 - <span data-ttu-id="8d4f3-985">**NX_SUCCESS** (0X00) http-server parametern get har slutförts</span><span class="sxs-lookup"><span data-stu-id="8d4f3-985">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
 - <span data-ttu-id="8d4f3-986">Det gick inte att hitta den angivna parametern **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-986">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
 - <span data-ttu-id="8d4f3-987">Parametern för **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) är inte korrekt avslutad</span><span class="sxs-lookup"><span data-stu-id="8d4f3-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
 - <span data-ttu-id="8d4f3-988">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-988">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-989">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-989">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-990">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-990">Allowed From</span></span>

<span data-ttu-id="8d4f3-991">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-991">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-992">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-992">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="8d4f3-993">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="8d4f3-993">nx_http_server_query_get</span></span>

<span data-ttu-id="8d4f3-994">Hämta fråga från begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-994">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-995">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-995">Prototype</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="8d4f3-996">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-996">Description</span></span>

<span data-ttu-id="8d4f3-997">Den här tjänsten försöker hämta angiven HTTP URL-fråga i det angivna paketet för begäran.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-997">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="8d4f3-998">Om begärd HTTP-fråga inte finns, returnerar den här rutinen statusen NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-998">If the requested HTTP query is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="8d4f3-999">Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-999">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-1000">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1000">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-1001">**packet_ptr** Pekare till HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1001">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="8d4f3-1002">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1002">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="8d4f3-1003">**query_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i listan över frågor.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1003">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
 - <span data-ttu-id="8d4f3-1004">**query_ptr** Mål områden för att kopiera frågan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1004">**query_ptr** Destination area to copy the query.</span></span>
 - <span data-ttu-id="8d4f3-1005">**max_query_size** Maximal storlek på mål arean för frågan.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1005">**max_query_size** Maximum size of the query destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-1006">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1006">Return Values</span></span>

 - <span data-ttu-id="8d4f3-1007">**NX_SUCCESS** (0X00) lyckad http-server fråga Hämta</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1007">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
 - <span data-ttu-id="8d4f3-1008">**NX_HTTP_FAILED** (0XE2) frågan är för liten.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1008">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
 - <span data-ttu-id="8d4f3-1009">Det gick inte att hitta den angivna frågan för **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1009">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
 - <span data-ttu-id="8d4f3-1010">**NX_HTTP_NO_QUERY_PARSED** (0XF2) ingen fråga i klient förfrågan</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
 - <span data-ttu-id="8d4f3-1011">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1011">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-1012">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1012">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-1013">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1013">Allowed From</span></span>

<span data-ttu-id="8d4f3-1014">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1014">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-1015">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1015">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a><span data-ttu-id="8d4f3-1016">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1016">nx_http_server_start</span></span>

<span data-ttu-id="8d4f3-1017">Starta HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1017">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-1018">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1018">Prototype</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8d4f3-1019">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1019">Description</span></span>

<span data-ttu-id="8d4f3-1020">Den här tjänsten startar den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1020">This service starts the previously create HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-1021">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1021">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-1022">**http_server_ptr** Pekare till HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1022">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-1023">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1023">Return Values</span></span>

 - <span data-ttu-id="8d4f3-1024">**NX_SUCCESS** (0X00) Server start har slutförts</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1024">**NX_SUCCESS** (0x00) Successful Server start</span></span>
 - <span data-ttu-id="8d4f3-1025">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1025">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-1026">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1026">Allowed From</span></span>

<span data-ttu-id="8d4f3-1027">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1027">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-1028">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1028">Example</span></span>

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="8d4f3-1029">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1029">nx_http_server_stop</span></span>

<span data-ttu-id="8d4f3-1030">Stoppa HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1030">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-1031">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1031">Prototype</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8d4f3-1032">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1032">Description</span></span>

<span data-ttu-id="8d4f3-1033">Den här tjänsten stoppar den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1033">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="8d4f3-1034">Den här rutinen ska anropas innan en HTTP-serverinstans tas bort.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1034">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-1035">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1035">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-1036">**http_server_ptr** Pekare till HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1036">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-1037">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1037">Return Values</span></span>

 - <span data-ttu-id="8d4f3-1038">**NX_SUCCESS** (0X00) Server stopp har slutförts</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1038">**NX_SUCCESS** (0x00) Successful Server stop</span></span>
 - <span data-ttu-id="8d4f3-1039">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1039">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-1040">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1040">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-1041">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1041">Allowed From</span></span>

<span data-ttu-id="8d4f3-1042">Konversation</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1042">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-1043">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1043">Example</span></span>

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="8d4f3-1044">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1044">nx_http_server_type_get</span></span>

<span data-ttu-id="8d4f3-1045">Extrahera filtypen från klientens HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1045">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-1046">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1046">Prototype</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a><span data-ttu-id="8d4f3-1047">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1047">Description</span></span>

> [!NOTE]
> <span data-ttu-id="8d4f3-1048">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1048">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-1049">Användarna uppmanas att använda tjänsten *nx_http_server_type_retrieve ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1049">Users are encouraged to use the service *nx_http_server_type_retrieve()*.</span></span>

<span data-ttu-id="8d4f3-1050">Den här tjänsten extraherar typen av HTTP-begäran i bufferten http_type_string och dess längd i returvärdet från indatabufferten, vanligt vis URL: en.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1050">This service extracts the HTTP request type in the buffer http_type_string and its length in the return value from the input buffer name, usually the URL.</span></span> <span data-ttu-id="8d4f3-1051">Om det inte går att hitta någon MIME-mappning används standard typen text/plain.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1051">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="8d4f3-1052">Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1052">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="8d4f3-1053">Standard-MIME-mappningarna i NetX Duo HTTP-server är:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1053">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="8d4f3-1054">**HTML-** text/html</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1054">**html** text/html</span></span>
 - <span data-ttu-id="8d4f3-1055">**htm** -text/html</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1055">**htm** text/html</span></span>
 - <span data-ttu-id="8d4f3-1056">**txt** -text/plain</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1056">**txt** text/plain</span></span>
 - <span data-ttu-id="8d4f3-1057">**GIF** -bild/gif</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1057">**gif** image/gif</span></span>
 - <span data-ttu-id="8d4f3-1058">**jpg** -bild/JPEG</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1058">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="8d4f3-1059">**ICO** -bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1059">**ico** image/x-icon</span></span>

<span data-ttu-id="8d4f3-1060">Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1060">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="8d4f3-1061">Se *nx_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1061">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="8d4f3-1062">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1062">This service is deprecated.</span></span> <span data-ttu-id="8d4f3-1063">Utvecklare uppmanas att migrera till *nx_http_server_type_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1063">Developers are encouraged to migrate to *nx_http_server_type_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-1064">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1064">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-1065">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1065">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="8d4f3-1066">**namn pekare** som ska genomsökas</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1066">**name Pointer** to buffer to search</span></span>
 - <span data-ttu-id="8d4f3-1067">**http_type_string** (pekare till extraherad HTML-typ)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1067">**http_type_string** (Pointer to extracted HTML type)</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-1068">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1068">Return Values</span></span>

 - <span data-ttu-id="8d4f3-1069">**Sträng längd i byte** Ett värde som inte är noll har slutförts.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1069">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="8d4f3-1070">Noll indikerar fel.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1070">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-1071">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1071">Allowed From</span></span>

<span data-ttu-id="8d4f3-1072">Program</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1072">Application</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-1073">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1073">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="8d4f3-1074">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1074">nx_http_server_type_get_extended</span></span>

<span data-ttu-id="8d4f3-1075">Extrahera filtypen från klientens HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1075">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-1076">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1076">Prototype</span></span>

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a><span data-ttu-id="8d4f3-1077">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1077">Description</span></span>

<span data-ttu-id="8d4f3-1078">Den här tjänsten extraherar typen av HTTP-begäran i bufferten *http_type_string* och dess längd i returvärdet från *indatabufferten, vanligt vis URL: en*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1078">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="8d4f3-1079">Om det inte går att hitta någon MIME-mappning används standard typen text/plain.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1079">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="8d4f3-1080">Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1080">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="8d4f3-1081">Standard-MIME-mappningarna i NetX Duo HTTP-server är:</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1081">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="8d4f3-1082">**HTML-** text/html</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1082">**html** text/html</span></span>
 - <span data-ttu-id="8d4f3-1083">**htm** -text/html</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1083">**htm** text/html</span></span>
 - <span data-ttu-id="8d4f3-1084">**txt** -text/plain</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1084">**txt** text/plain</span></span>
 - <span data-ttu-id="8d4f3-1085">**GIF** -bild/gif</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1085">**gif** image/gif</span></span>
 - <span data-ttu-id="8d4f3-1086">**jpg** -bild/JPEG</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1086">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="8d4f3-1087">**ICO** -bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1087">**ico** image/x-icon</span></span>

<span data-ttu-id="8d4f3-1088">Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1088">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="8d4f3-1089">Se *nx_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1089">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="8d4f3-1090">Den här tjänsten ersätter *nx_http_server_type_get ()*.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1090">This service replaces *nx_http_server_type_get()*.</span></span> <span data-ttu-id="8d4f3-1091">Den här versionen tillhandahåller ytterligare längd information.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1091">This version supplies additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-1092">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1092">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-1093">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1093">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="8d4f3-1094">**namn** Pekare för att söka</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1094">**name** Pointer to buffer to search</span></span>
 - <span data-ttu-id="8d4f3-1095">**name_length** Längd på buffert att söka i</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1095">**name_length** Length of buffer to search</span></span>
 - <span data-ttu-id="8d4f3-1096">**http_type_string** (pekare till extraherad HTML-typ)</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1096">**http_type_string** (Pointer to extracted HTML type)</span></span>
 - <span data-ttu-id="8d4f3-1097">**http_type_string_max_size** Storlek på http_type_string-bufferten</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1097">**http_type_string_max_size** Size of the http_type_string buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-1098">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1098">Return Values</span></span>

 - <span data-ttu-id="8d4f3-1099">**Sträng längd i byte** Ett värde som inte är noll har slutförts.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1099">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="8d4f3-1100">Noll indikerar fel.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1100">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-1101">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1101">Allowed From</span></span>

<span data-ttu-id="8d4f3-1102">Program</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1102">Application</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-1103">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1103">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="8d4f3-1104">Ett mer detaljerat exempel finns i beskrivningen av [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1104">For a more detailed example, see the description for [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="8d4f3-1105">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1105">nx_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="8d4f3-1106">Ange funktionen Digest-autentisering</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1106">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-1107">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1107">Prototype</span></span>

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
```

### <a name="description"></a><span data-ttu-id="8d4f3-1108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1108">Description</span></span>

<span data-ttu-id="8d4f3-1109">Den här tjänsten anger återanropet som anropas när Digest-autentisering utförs.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1109">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-1110">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1110">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-1111">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1111">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="8d4f3-1112">**digest_authenticate_callback** Pekare till sammanfattad autentisering av motringning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1112">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-1113">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1113">Return Values</span></span>

 - <span data-ttu-id="8d4f3-1114">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1114">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="8d4f3-1115">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1115">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="8d4f3-1116">NX_NOT_SUPPORTED (0x4B) Digest-autentisering är inte aktiverat</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1116">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-1117">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1117">Allowed From</span></span>

<span data-ttu-id="8d4f3-1118">Program</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1118">Application</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-1119">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1119">Example</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="8d4f3-1120">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1120">nx_http_server_authentication_check_set</span></span>

<span data-ttu-id="8d4f3-1121">Ange återanrops funktion för autentisering</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1121">Set authentication checking callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8d4f3-1122">Prototyp</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1122">Prototype</span></span>

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a><span data-ttu-id="8d4f3-1123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1123">Description</span></span>

<span data-ttu-id="8d4f3-1124">Den här tjänsten anger återanrops funktionen för autentisering.</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1124">This service sets the callback function of authentication checking.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8d4f3-1125">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1125">Input Parameters</span></span>

 - <span data-ttu-id="8d4f3-1126">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1126">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="8d4f3-1127">**authentication_check_extended** Pekare till programmets verifierings kontroll</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1127">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

### <a name="return-values"></a><span data-ttu-id="8d4f3-1128">Retur värden</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1128">Return Values</span></span>

 - <span data-ttu-id="8d4f3-1129">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1129">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="8d4f3-1130">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1130">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8d4f3-1131">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1131">Allowed From</span></span>

<span data-ttu-id="8d4f3-1132">Program</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1132">Application</span></span>

### <a name="example"></a><span data-ttu-id="8d4f3-1133">Exempel</span><span class="sxs-lookup"><span data-stu-id="8d4f3-1133">Example</span></span>

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
