---
title: Kapitel 3 – Beskrivning av NetX HTTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX HTTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826712"
---
# <a name="chapter-3---description-of-netx-http-services"></a><span data-ttu-id="1aada-103">Kapitel 3 – Beskrivning av NetX HTTP-tjänster</span><span class="sxs-lookup"><span data-stu-id="1aada-103">Chapter 3 - Description of NetX HTTP services</span></span>

<span data-ttu-id="1aada-104">Det här kapitlet innehåller en beskrivning av alla NetX HTTP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="1aada-104">This chapter contains a description of all NetX HTTP services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="1aada-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="1aada-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="1aada-106">**HTTP-klient tjänster:**</span><span class="sxs-lookup"><span data-stu-id="1aada-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="1aada-107">nx_http_client_create *skapa en HTTP-klient instans*</span><span class="sxs-lookup"><span data-stu-id="1aada-107">nx_http_client_create *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="1aada-108">nx_http_client_delete *ta bort en HTTP-klient instans*</span><span class="sxs-lookup"><span data-stu-id="1aada-108">nx_http_client_delete *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="1aada-109">nx_http_client_get_start *starta en HTTP GET-begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-109">nx_http_client_get_start *Start an HTTP GET request*</span></span>
- <span data-ttu-id="1aada-110">nx_http_client_get_start_extended *starta en HTTP GET-begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-110">nx_http_client_get_start_extended *Start an HTTP GET request*</span></span>
- <span data-ttu-id="1aada-111">nx_http_client_get_packet *Hämta nästa resurs data paket*</span><span class="sxs-lookup"><span data-stu-id="1aada-111">nx_http_client_get_packet *Get next resource data packet*</span></span>
- <span data-ttu-id="1aada-112">nx_http_client_put_start *starta en HTTP-begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-112">nx_http_client_put_start *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="1aada-113">nx_http_client_put_start_extended *starta en HTTP-begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-113">nx_http_client_put_start_extended *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="1aada-114">nx_http_client_put_packet *skicka nästa resurs data paket*</span><span class="sxs-lookup"><span data-stu-id="1aada-114">nx_http_client_put_packet *Send next resource data packet*</span></span>
- <span data-ttu-id="1aada-115">*nx_http_client_set_connect_port* *ändra porten för att ansluta till http-servern*</span><span class="sxs-lookup"><span data-stu-id="1aada-115">*nx_http_client_set_connect_port* *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="1aada-116">**HTTP-Server tjänster:**</span><span class="sxs-lookup"><span data-stu-id="1aada-116">**HTTP Server services:**</span></span>

- <span data-ttu-id="1aada-117">nx_http_server_cache_info_callback_set *Ange motringning för att hämta ålder och senaste ändrings datum för angiven URL*</span><span class="sxs-lookup"><span data-stu-id="1aada-117">nx_http_server_cache_info_callback_set *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="1aada-118">nx_http_server_callback_data_send *Skicka HTTP-data från callback-funktionen*</span><span class="sxs-lookup"><span data-stu-id="1aada-118">nx_http_server_callback_data_send *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="1aada-119">nx_http_server_callback_generate_response_header *skapa svars huvud i callback-funktioner*</span><span class="sxs-lookup"><span data-stu-id="1aada-119">nx_http_server_callback_generate_response_header *Create response header in callback functions*</span></span>
- <span data-ttu-id="1aada-120">nx_http_server_callback_generate_response_header_extended *skapa svars huvud i callback-funktioner*</span><span class="sxs-lookup"><span data-stu-id="1aada-120">nx_http_server_callback_generate_response_header_extended *Create response header in callback functions*</span></span>
- <span data-ttu-id="1aada-121">nx_http_server_callback_packet_send *Skicka ett HTTP-paket från ett HTTP-motanrop*</span><span class="sxs-lookup"><span data-stu-id="1aada-121">nx_http_server_callback_packet_send *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="1aada-122">nx_http_server_callback_response_send *Skicka svar från callback-funktionen*</span><span class="sxs-lookup"><span data-stu-id="1aada-122">nx_http_server_callback_response_send *Send response from callback function*</span></span>
- <span data-ttu-id="1aada-123">nx_http_server_callback_response_send_extended *Skicka svar från callback-funktionen*</span><span class="sxs-lookup"><span data-stu-id="1aada-123">nx_http_server_callback_response_send_extended *Send response from callback function*</span></span>
- <span data-ttu-id="1aada-124">nx_http_server_content_get *Hämta innehåll från begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-124">nx_http_server_content_get *Get content from the request*</span></span>
- <span data-ttu-id="1aada-125">nx_http_server_content_get_extended *Hämta innehåll från begäran; stöder tomma (noll innehålls längd) begär Anden*</span><span class="sxs-lookup"><span data-stu-id="1aada-125">nx_http_server_content_get_extended *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="1aada-126">nx_http_server_content_length_get *Hämta längden på innehållet i begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-126">nx_http_server_content_length_get *Get length of content in the request*</span></span>
- <span data-ttu-id="1aada-127">nx_http_server_content_length_get_extended *Hämta längden på innehållet i begäran; stöder tomma (noll innehålls längd) begär Anden*</span><span class="sxs-lookup"><span data-stu-id="1aada-127">nx_http_server_content_length_get_extended *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="1aada-128">nx_http_server_create *skapa en HTTP-serverinstans*</span><span class="sxs-lookup"><span data-stu-id="1aada-128">nx_http_server_create *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="1aada-129">nx_http_server_delete *ta bort en HTTP-serverinstans*</span><span class="sxs-lookup"><span data-stu-id="1aada-129">nx_http_server_delete *Delete an HTTP Server instance*</span></span>
- <span data-ttu-id="1aada-130">nx_http_server_get_entity_content *returnera storlek och plats för enhetens innehåll i URL: en*</span><span class="sxs-lookup"><span data-stu-id="1aada-130">nx_http_server_get_entity_content *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="1aada-131">nx_http_server_get_entity_header *EXTRAHERA URL-enhetens rubrik till angiven buffert*</span><span class="sxs-lookup"><span data-stu-id="1aada-131">nx_http_server_get_entity_header *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="1aada-132">nx_http_server_gmt_callback_set *Ange motringning för att hämta GMT-datum och tid*</span><span class="sxs-lookup"><span data-stu-id="1aada-132">nx_http_server_gmt_callback_set *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="1aada-133">nx_http_server_invalid_userpassword_notify_set *Ange motringning för när ogiltigt användar namn och lösen ord tas emot i en klientbegäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-133">nx_http_server_invalid_userpassword_notify_set *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="1aada-134">nx_http_server_mime_maps_additional_set *definiera ytterligare MIME-mappningar för HTML*</span><span class="sxs-lookup"><span data-stu-id="1aada-134">nx_http_server_mime_maps_additional_set *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="1aada-135">nx_http_server_packet_content_find *extrahera innehålls längd i HTTP-sidhuvudet och ange pekaren till början av innehålls data*</span><span class="sxs-lookup"><span data-stu-id="1aada-135">nx_http_server_packet_content_find *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="1aada-136">nx_http_server_packet_get *ta emot klient paket direkt*</span><span class="sxs-lookup"><span data-stu-id="1aada-136">nx_http_server_packet_get *Receive client packet directly*</span></span>
- <span data-ttu-id="1aada-137">nx_http_server_param_get *Hämta parameter från begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-137">nx_http_server_param_get *Get parameter from the request*</span></span>
- <span data-ttu-id="1aada-138">nx_http_server_query_get *Hämta fråga från begäran*</span><span class="sxs-lookup"><span data-stu-id="1aada-138">nx_http_server_query_get *Get query from the request*</span></span>
- <span data-ttu-id="1aada-139">nx_http_server_start *Starta HTTP-servern*</span><span class="sxs-lookup"><span data-stu-id="1aada-139">nx_http_server_start *Start the HTTP Server*</span></span>
- <span data-ttu-id="1aada-140">nx_http_server_stop *stoppa HTTP-servern*</span><span class="sxs-lookup"><span data-stu-id="1aada-140">nx_http_server_stop *Stop the HTTP Server*</span></span>
- <span data-ttu-id="1aada-141">nx_http_server_type_get *extrahera HTTP-typ t. ex. text/plain från rubriken*</span><span class="sxs-lookup"><span data-stu-id="1aada-141">nx_http_server_type_get *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="1aada-142">nx_http_server_type_get_extended *extrahera HTTP-typ t. ex. text/plain från rubriken*</span><span class="sxs-lookup"><span data-stu-id="1aada-142">nx_http_server_type_get_extended *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="1aada-143">nx_http_server_digest_authenticate_notify_set *Ange funktionen Digest-autentisering*</span><span class="sxs-lookup"><span data-stu-id="1aada-143">nx_http_server_digest_authenticate_notify_set *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="1aada-144">funktionen för motringning av nx_http_server_authentication_check_set *anger autentisering*</span><span class="sxs-lookup"><span data-stu-id="1aada-144">nx_http_server_authentication_check_set *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="1aada-145">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="1aada-145">nx_http_client_create</span></span>

### <a name="create-an-http-client-instance"></a><span data-ttu-id="1aada-146">Skapa en HTTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="1aada-146">Create an HTTP Client Instance</span></span>

<span data-ttu-id="1aada-147">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-147">**Prototype**</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

<span data-ttu-id="1aada-148">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-148">**Description**</span></span>

<span data-ttu-id="1aada-149">Den här tjänsten skapar en HTTP-klient instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-149">This service creates an HTTP Client instance on the specified IP instance.</span></span>

<span data-ttu-id="1aada-150">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-150">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-151">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-151">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-152">**client_name** Namn på HTTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="1aada-152">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="1aada-153">**ip_ptr** Pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="1aada-153">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="1aada-154">**pool_ptr** Pekare till standard paketets pool.</span><span class="sxs-lookup"><span data-stu-id="1aada-154">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="1aada-155">Observera att paketen i den här poolen måste ha en nytto last som är tillräckligt stor för att hantera hela svars huvudet.</span><span class="sxs-lookup"><span data-stu-id="1aada-155">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="1aada-156">Detta definieras av NX_HTTP_CLIENT_MIN_PACKET_SIZE i *nx_http_client. h*.</span><span class="sxs-lookup"><span data-stu-id="1aada-156">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http_client.h*.</span></span>
- <span data-ttu-id="1aada-157">**window_size** Storlek på klientens mottagnings fönster för TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="1aada-157">**window_size** Size of the Client’s TCP socket receive window.</span></span>

<span data-ttu-id="1aada-158">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-158">**Return Values**</span></span>

- <span data-ttu-id="1aada-159">**NX_SUCCESS** (0X00) http-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="1aada-159">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="1aada-160">NX_PTR_ERROR (0x16) ogiltig pekare för HTTP, ip_ptr eller Packet pool</span><span class="sxs-lookup"><span data-stu-id="1aada-160">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="1aada-161">NX_HTTP_POOL_ERROR (0xE9) ogiltig nytto Last storlek i Packet bassäng</span><span class="sxs-lookup"><span data-stu-id="1aada-161">NX_HTTP_POOL_ERROR(0xE9) Invalid payload size in packet pool</span></span>

<span data-ttu-id="1aada-162">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-162">**Allowed From**</span></span>

<span data-ttu-id="1aada-163">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="1aada-163">Initialization, Threads</span></span>

<span data-ttu-id="1aada-164">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-164">**Example**</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="1aada-165">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="1aada-165">nx_http_client_delete</span></span>

### <a name="delete-an-http-client-instance"></a><span data-ttu-id="1aada-166">Ta bort en HTTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="1aada-166">Delete an HTTP Client Instance</span></span>

<span data-ttu-id="1aada-167">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-167">**Prototype**</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

<span data-ttu-id="1aada-168">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-168">**Description**</span></span>

<span data-ttu-id="1aada-169">Den här tjänsten tar bort en tidigare skapad HTTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="1aada-169">This service deletes a previously created HTTP Client instance.</span></span>

<span data-ttu-id="1aada-170">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-170">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-171">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-171">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="1aada-172">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-172">**Return Values**</span></span>

- <span data-ttu-id="1aada-173">**NX_SUCCESS** (0X00) http-klientbegäran har tagits bort</span><span class="sxs-lookup"><span data-stu-id="1aada-173">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="1aada-174">NX_PTR_ERROR (0x16) ogiltig HTTP-pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-174">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="1aada-175">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-175">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-176">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-176">**Allowed From**</span></span>

<span data-ttu-id="1aada-177">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-177">Threads</span></span>

<span data-ttu-id="1aada-178">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-178">**Example**</span></span>

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="1aada-179">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="1aada-179">nx_http_client_get_start</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="1aada-180">Starta en HTTP GET-begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-180">Start an HTTP GET request</span></span>

<span data-ttu-id="1aada-181">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-181">**Prototype**</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

<span data-ttu-id="1aada-182">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-182">**Description**</span></span>

<span data-ttu-id="1aada-183">Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-183">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="1aada-184">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_http_client_get_packet* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="1aada-184">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="1aada-185">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="1aada-185">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="1aada-186">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="1aada-186">This service is deprecated.</span></span> <span data-ttu-id="1aada-187">Utvecklare uppmanas att migrera till *nx_http_client_get_start_extended ()*</span><span class="sxs-lookup"><span data-stu-id="1aada-187">Developers are encouraged to migrate to *nx_http_client_get_start_extended()*</span></span>

<span data-ttu-id="1aada-188">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-188">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-189">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-189">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-190">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-190">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="1aada-191">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="1aada-191">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="1aada-192">**input_ptr** Pekare till ytterligare data för GET-begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-192">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="1aada-193">Detta är valfritt.</span><span class="sxs-lookup"><span data-stu-id="1aada-193">This is optional.</span></span> <span data-ttu-id="1aada-194">Om detta är giltigt placeras angivna indata i meddelandets innehålls områden och ett inlägg används i stället för en GET-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="1aada-194">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="1aada-195">**input_size** Antal byte i valfria ytterligare ininput_ptr.</span><span class="sxs-lookup"><span data-stu-id="1aada-195">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="1aada-196">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-196">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="1aada-197">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-197">**password** Pointer to optional password for authentication.</span></span><span data-ttu-id="1aada-198">
-\*\*wait_option*\* Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="1aada-198">
-\*\*wait_option*\* Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="1aada-199">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1aada-199">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1aada-200">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1aada-200">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1aada-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="1aada-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="1aada-202">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-202">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="1aada-203">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="1aada-203">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="1aada-204">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-204">**Return Values**</span></span>

- <span data-ttu-id="1aada-205">**NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="1aada-205">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="1aada-206">**NX_HTTP_ERROR** (0XE0) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="1aada-206">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="1aada-207">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="1aada-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="1aada-208">**NX_HTTP_FAILED** (0XE2) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-208">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="1aada-209">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="1aada-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="1aada-210">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-210">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-211">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1aada-211">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="1aada-212">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-212">**Allowed From**</span></span>

<span data-ttu-id="1aada-213">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-213">Threads</span></span>

<span data-ttu-id="1aada-214">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-214">**Example**</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="1aada-215">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="1aada-215">nx_http_client_get_start_extended</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="1aada-216">Starta en HTTP GET-begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-216">Start an HTTP GET request</span></span>

<span data-ttu-id="1aada-217">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-217">**Prototype**</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

<span data-ttu-id="1aada-218">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-218">**Description**</span></span>

<span data-ttu-id="1aada-219">Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-219">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="1aada-220">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_http_client_get_packet* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="1aada-220">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="1aada-221">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="1aada-221">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="1aada-222">Den här tjänsten ersätter *nx_http_client_get_start ()*.</span><span class="sxs-lookup"><span data-stu-id="1aada-222">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="1aada-223">Den kräver att anroparen anger längden på resursen, användar namnet och lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="1aada-223">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="1aada-224">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-224">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-225">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-225">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-226">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-226">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="1aada-227">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="1aada-227">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="1aada-228">**resource_length** Längd på URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="1aada-228">**resource_length** Length of URL string for requested resource.</span></span>
- <span data-ttu-id="1aada-229">**input_ptr** Pekare till ytterligare data för GET-begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-229">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="1aada-230">Detta är valfritt.</span><span class="sxs-lookup"><span data-stu-id="1aada-230">This is optional.</span></span> <span data-ttu-id="1aada-231">Om detta är giltigt placeras angivna indata i meddelandets innehålls områden och ett inlägg används i stället för en GET-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="1aada-231">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="1aada-232">**input_size** Antal byte i valfria ytterligare ininput_ptr.</span><span class="sxs-lookup"><span data-stu-id="1aada-232">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="1aada-233">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-233">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="1aada-234">**username_length** Längden på det valfria användar namnet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-234">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="1aada-235">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-235">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="1aada-236">**password_length** Det valfria lösen ordets längd för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-236">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="1aada-237">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="1aada-237">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="1aada-238">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1aada-238">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1aada-239">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1aada-239">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1aada-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="1aada-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="1aada-241">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-241">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="1aada-242">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="1aada-242">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="1aada-243">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-243">**Return Values**</span></span>

- <span data-ttu-id="1aada-244">**NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="1aada-244">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="1aada-245">**NX_HTTP_ERROR** (0XE0) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="1aada-245">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="1aada-246">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="1aada-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="1aada-247">**NX_HTTP_FAILED** (0XE2) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-247">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="1aada-248">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="1aada-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="1aada-249">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-249">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-250">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1aada-250">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="1aada-251">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-251">**Allowed From**</span></span>

<span data-ttu-id="1aada-252">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-252">Threads</span></span>

<span data-ttu-id="1aada-253">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-253">**Example**</span></span>
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="1aada-254">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="1aada-254">nx_http_client_get_packet</span></span>

### <a name="get-next-resource-data-packet"></a><span data-ttu-id="1aada-255">Hämta nästa resurs data paket</span><span class="sxs-lookup"><span data-stu-id="1aada-255">Get next resource data packet</span></span>

<span data-ttu-id="1aada-256">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-256">**Prototype**</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="1aada-257">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-257">**Description**</span></span>

<span data-ttu-id="1aada-258">Den här tjänsten hämtar nästa innehålls paket för resursen som begärdes av föregående *nx_http_client_get_start* -anrop.</span><span class="sxs-lookup"><span data-stu-id="1aada-258">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="1aada-259">Efterföljande anrop till den här rutinen bör göras tills retur statusen för NX_HTTP_GET_DONE tas emot.</span><span class="sxs-lookup"><span data-stu-id="1aada-259">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

<span data-ttu-id="1aada-260">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-260">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-261">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-261">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-262">**packet_ptr** Mål för paket pekare som innehåller partiellt resurs innehåll.</span><span class="sxs-lookup"><span data-stu-id="1aada-262">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="1aada-263">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klienten ska hämta paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-263">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="1aada-264">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1aada-264">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1aada-265">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1aada-265">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1aada-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="1aada-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="1aada-267">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-267">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="1aada-268">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="1aada-268">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="1aada-269">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-269">**Return Values**</span></span>

- <span data-ttu-id="1aada-270">**NX_SUCCESS** (0X00) http-klient hämta paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-270">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
- <span data-ttu-id="1aada-271">**NX_HTTP_GET_DONE** (0XEC) http-klient hämta paket har slutförts</span><span class="sxs-lookup"><span data-stu-id="1aada-271">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
- <span data-ttu-id="1aada-272">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte i get-läge.</span><span class="sxs-lookup"><span data-stu-id="1aada-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="1aada-273">**NX_HTTP_BAD_PACKET_LENGTH** (0XED) ogiltig paket längd</span><span class="sxs-lookup"><span data-stu-id="1aada-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="1aada-274">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-275">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-275">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-276">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-276">**Allowed From**</span></span>

<span data-ttu-id="1aada-277">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-277">Threads</span></span>

<span data-ttu-id="1aada-278">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-278">**Example**</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="1aada-279">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="1aada-279">nx_http_client_put_start</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="1aada-280">Starta en HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-280">Start an HTTP PUT request</span></span> 

<span data-ttu-id="1aada-281">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-281">**Prototype**</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="1aada-282">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-282">**Description**</span></span>

<span data-ttu-id="1aada-283">Den här tjänsten försöker skicka en skicka begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="1aada-283">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="1aada-284">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_http_client_put_packet* rutinen för att faktiskt skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-284">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="1aada-285">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="1aada-285">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="1aada-286">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="1aada-286">This service is deprecated.</span></span> <span data-ttu-id="1aada-287">Utvecklare uppmanas att migrera till *nx_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="1aada-287">Developers are encouraged to migrate to *nx_http_client_put_start_extended()*.</span></span>

<span data-ttu-id="1aada-288">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-288">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-289">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-289">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-290">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-290">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="1aada-291">**resurs** Pekare till URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-291">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="1aada-292">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-292">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="1aada-293">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-293">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="1aada-294">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="1aada-294">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="1aada-295">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_http_client_put_packet* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="1aada-295">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="1aada-296">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klientens placering ska starta.</span><span class="sxs-lookup"><span data-stu-id="1aada-296">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="1aada-297">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1aada-297">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1aada-298">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1aada-298">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1aada-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="1aada-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="1aada-300">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-300">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="1aada-301">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="1aada-301">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="1aada-302">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-302">**Return Values**</span></span>

- <span data-ttu-id="1aada-303">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="1aada-303">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="1aada-304">**NX_HTTP_USERNAME_TOO_LONG**</span><span class="sxs-lookup"><span data-stu-id="1aada-304">**NX_HTTP_USERNAME_TOO_LONG**</span></span>
- <span data-ttu-id="1aada-305">**(0xF1) användar namnet är för stort för bufferten**</span><span class="sxs-lookup"><span data-stu-id="1aada-305">**(0xF1) Username too large for buffer**</span></span>
- <span data-ttu-id="1aada-306">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="1aada-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="1aada-307">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-307">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-308">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="1aada-308">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="1aada-309">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-309">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-310">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-310">**Allowed From**</span></span>

<span data-ttu-id="1aada-311">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-311">Threads</span></span>

<span data-ttu-id="1aada-312">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-312">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="1aada-313">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="1aada-313">nx_http_client_put_start_extended</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="1aada-314">Starta en HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-314">Start an HTTP PUT request</span></span>

<span data-ttu-id="1aada-315">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-315">**Prototype**</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="1aada-316">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-316">**Description**</span></span>

<span data-ttu-id="1aada-317">Den här tjänsten försöker skicka en skicka begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen.</span><span class="sxs-lookup"><span data-stu-id="1aada-317">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="1aada-318">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_http_client_put_packet* rutinen för att faktiskt skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-318">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="1aada-319">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="1aada-319">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="1aada-320">Den här tjänsten ersätter *nx_http_client_put_start ()*.</span><span class="sxs-lookup"><span data-stu-id="1aada-320">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="1aada-321">Den kräver att anroparen anger längden på resursen, användar namnet och lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="1aada-321">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="1aada-322">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-322">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-323">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-323">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-324">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-324">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="1aada-325">**resurs** Pekare till URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-325">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="1aada-326">**resource_length** Längd på URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-326">**resource_length** Length of URL string for resource to send to Server.</span></span>
- <span data-ttu-id="1aada-327">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-327">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="1aada-328">**username_length** Längden på det valfria användar namnet för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-328">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="1aada-329">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-329">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="1aada-330">**password_length** Det valfria lösen ordets längd för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-330">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="1aada-331">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="1aada-331">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="1aada-332">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_http_client_put_packet* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="1aada-332">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="1aada-333">**wait_option** Definierar hur länge tjänsten väntar på att HTTP-klientens placering ska starta.</span><span class="sxs-lookup"><span data-stu-id="1aada-333">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="1aada-334">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1aada-334">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1aada-335">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1aada-335">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1aada-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="1aada-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="1aada-337">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-337">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="1aada-338">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="1aada-338">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="1aada-339">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-339">**Return Values**</span></span>

- <span data-ttu-id="1aada-340">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="1aada-340">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="1aada-341">**NX_HTTP_USERNAME_TOO_LONG** (0XF1) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="1aada-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
- <span data-ttu-id="1aada-342">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="1aada-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="1aada-343">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-343">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-344">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="1aada-344">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="1aada-345">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-345">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-346">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-346">**Allowed From**</span></span>

<span data-ttu-id="1aada-347">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-347">Threads</span></span>

<span data-ttu-id="1aada-348">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-348">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="1aada-349">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="1aada-349">nx_http_client_put_packet</span></span>

### <a name="send-next-resource-data-packet"></a><span data-ttu-id="1aada-350">Skicka nästa resurs data paket</span><span class="sxs-lookup"><span data-stu-id="1aada-350">Send next resource data packet</span></span>

<span data-ttu-id="1aada-351">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-351">**Prototype**</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="1aada-352">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-352">**Description**</span></span>

<span data-ttu-id="1aada-353">Den här tjänsten försöker skicka nästa paket med resurs innehåll till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-353">This service attempts to send the next packet of resource content to the HTTP Server.</span></span> <span data-ttu-id="1aada-354">Observera att den här rutinen ska anropas upprepade gånger tills den kombinerade längden på de paket som skickas är lika med "total_bytes" som anges i föregående *nx_http_client_put_start ()-* anrop.</span><span class="sxs-lookup"><span data-stu-id="1aada-354">Note that this routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start()* call.</span></span>

<span data-ttu-id="1aada-355">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-355">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-356">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-356">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-357">**packet_ptr** Pekare till nästa innehåll i resursen som ska skickas till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-357">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="1aada-358">**wait_option** Definierar hur länge tjänsten ska vänta internt på att bearbeta HTTP-klientens paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-358">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="1aada-359">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1aada-359">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="1aada-360">**timeout-värde** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="1aada-360">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="1aada-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="1aada-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="1aada-362">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-362">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /> <span data-ttu-id="1aada-363">Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på HTTP-server svaret.</span><span class="sxs-lookup"><span data-stu-id="1aada-363">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="1aada-364">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-364">**Return Values**</span></span>

- <span data-ttu-id="1aada-365">**NX_SUCCESS** (0x00) skickade http-klient paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-365">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="1aada-366">**NX_HTTP_NOT_READY** (0XEA) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="1aada-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="1aada-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0XEE) mottagen Server felkod \* *-\*\*NX_HTTP_BAD_PACKET_LENGTH*\* (0xED) ogiltig paket längd</span><span class="sxs-lookup"><span data-stu-id="1aada-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="1aada-368">**NX_HTTP_AUTHENTICATION_ERROR** (0XEB) ogiltigt namn och/eller lösen ord</span><span class="sxs-lookup"><span data-stu-id="1aada-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
- <span data-ttu-id="1aada-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** -servern (0xEF) svarar innan den har slutförts</span><span class="sxs-lookup"><span data-stu-id="1aada-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
- <span data-ttu-id="1aada-370">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-370">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-371">NX_INVALID_PACKET-paketet (0x12) är för litet för TCP-huvud</span><span class="sxs-lookup"><span data-stu-id="1aada-371">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="1aada-372">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-372">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-373">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-373">**Allowed From**</span></span>

<span data-ttu-id="1aada-374">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-374">Threads</span></span>

<span data-ttu-id="1aada-375">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-375">**Example**</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="1aada-376">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="1aada-376">nx_http_client_set_connect_port</span></span>

### <a name="set-the-connection-port-to-the-server"></a><span data-ttu-id="1aada-377">Ange anslutnings porten till servern</span><span class="sxs-lookup"><span data-stu-id="1aada-377">Set the connection port to the Server</span></span>

<span data-ttu-id="1aada-378">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-378">**Prototype**</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

<span data-ttu-id="1aada-379">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-379">**Description**</span></span>

<span data-ttu-id="1aada-380">Den här tjänsten ändrar anslutnings porten vid anslutning till HTTP-servern till den angivna porten vid körning.</span><span class="sxs-lookup"><span data-stu-id="1aada-380">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="1aada-381">Annars är anslutnings porten standardvärdet 80.</span><span class="sxs-lookup"><span data-stu-id="1aada-381">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="1aada-382">Detta måste anropas före *nx_http_client_get_start*() och *nx_http_client_put_start*(), t. ex. När http-klienten ansluter till servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-382">This must be called before *nx_http_client_get_start*() and *nx_http_client_put_start*() e.g. when the HTTP Client connects with the Server.</span></span>

<span data-ttu-id="1aada-383">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-383">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-384">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="1aada-384">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="1aada-385">**port** Port för att ansluta till servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-385">**port** Port for connecting to the Server.</span></span>

<span data-ttu-id="1aada-386">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-386">**Return Values**</span></span>

- <span data-ttu-id="1aada-387">**NX_SUCCESS** (0X00) har ändrat anslutnings porten</span><span class="sxs-lookup"><span data-stu-id="1aada-387">**NX_SUCCESS** (0x00) Successfully changed the connect port</span></span>
- <span data-ttu-id="1aada-388">**NX_INVALID_PORT** -porten (0x46) överskrider max gränsen (0xffff) eller är noll.</span><span class="sxs-lookup"><span data-stu-id="1aada-388">**NX_INVALID_PORT** (0x46) Port exceeds the maximum (0xFFFF) or is zero.</span></span>
- <span data-ttu-id="1aada-389">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-389">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-390">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-390">**Allowed From**</span></span>

<span data-ttu-id="1aada-391">Trådar, initiering</span><span class="sxs-lookup"><span data-stu-id="1aada-391">Threads, Initialization</span></span>

<span data-ttu-id="1aada-392">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-392">**Example**</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="1aada-393">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="1aada-393">nx_http_server_cache_info_callback_set</span></span>

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a><span data-ttu-id="1aada-394">Ange återanropet för att hämta URL-högsta ålder och datum</span><span class="sxs-lookup"><span data-stu-id="1aada-394">Set the callback to retrieve URL max age and date</span></span>

<span data-ttu-id="1aada-395">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-395">**Prototype**</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

<span data-ttu-id="1aada-396">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-396">**Description**</span></span>

<span data-ttu-id="1aada-397">Den här tjänsten anger den callback-tjänst som anropas för att hämta den maximala ålder och senaste ändrings datum för den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="1aada-397">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

<span data-ttu-id="1aada-398">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-398">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-399">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-399">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-400">**cache_info_get** Pekare till motringning</span><span class="sxs-lookup"><span data-stu-id="1aada-400">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="1aada-401">**max_age** Pekare till högsta ålder för en resurs</span><span class="sxs-lookup"><span data-stu-id="1aada-401">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="1aada-402">**data** Pekare till senaste ändrings datum som returnerades.</span><span class="sxs-lookup"><span data-stu-id="1aada-402">**data** Pointer to last modified date returned.</span></span>

<span data-ttu-id="1aada-403">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-403">**Return Values**</span></span>

- <span data-ttu-id="1aada-404">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="1aada-404">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="1aada-405">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-405">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-406">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-406">**Allowed From**</span></span>

<span data-ttu-id="1aada-407">Initiering</span><span class="sxs-lookup"><span data-stu-id="1aada-407">Initialization</span></span>

<span data-ttu-id="1aada-408">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-408">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="1aada-409">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="1aada-409">nx_http_server_callback_data_send</span></span>

### <a name="send-data-from-callback-function"></a><span data-ttu-id="1aada-410">Skicka data från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="1aada-410">Send data from callback function</span></span>

<span data-ttu-id="1aada-411">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-411">**Prototype**</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

<span data-ttu-id="1aada-412">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-412">**Description**</span></span>

<span data-ttu-id="1aada-413">Den här tjänsten skickar data i det angivna paketet från programmets callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="1aada-413">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="1aada-414">Detta används vanligt vis för att skicka dynamiska data som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="1aada-414">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="1aada-415">Observera att om den här funktionen används ansvarar återanrops rutinen för att skicka hela svaret i rätt format.</span><span class="sxs-lookup"><span data-stu-id="1aada-415">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="1aada-416">Dessutom måste återanrops rutinen returnera status för NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="1aada-416">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="1aada-417">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-417">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-418">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-419">**data_ptr** Pekare till de data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="1aada-419">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="1aada-420">**data_length** Antal byte som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="1aada-420">**data_length** Number of bytes to send.</span></span>

<span data-ttu-id="1aada-421">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-421">**Return Values**</span></span>

- <span data-ttu-id="1aada-422">**NX_SUCCESS** (0X00) har skickat Server data</span><span class="sxs-lookup"><span data-stu-id="1aada-422">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="1aada-423">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-423">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-424">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-424">**Allowed From**</span></span>

<span data-ttu-id="1aada-425">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-425">Threads</span></span>

<span data-ttu-id="1aada-426">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-426">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="1aada-427">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="1aada-427">nx_http_server_callback_generate_response_header</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="1aada-428">Skapa ett svars huvud i en callback-funktion</span><span class="sxs-lookup"><span data-stu-id="1aada-428">Create a response header in a callback function</span></span>

<span data-ttu-id="1aada-429">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-429">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

<span data-ttu-id="1aada-430">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-430">**Description**</span></span>

<span data-ttu-id="1aada-431">Den här tjänsten anropar den interna funktionen _ *nx_http_server_generate_response_header* när HTTP-servern svarar på klienten get, skicka och ta bort begär Anden.</span><span class="sxs-lookup"><span data-stu-id="1aada-431">This service calls the internal function _ *nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="1aada-432">Den är avsedd att användas i funktioner för återanrop i HTTP-server när HTTP-serverprogrammet utformar sitt svar på klienten.</span><span class="sxs-lookup"><span data-stu-id="1aada-432">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="1aada-433">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="1aada-433">This service is deprecated.</span></span> <span data-ttu-id="1aada-434">Utvecklare uppmanas att migrera till *nxd_http_server_callback_generate_response_header_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="1aada-434">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

<span data-ttu-id="1aada-435">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-435">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-436">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-436">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-437">**packet_pptr** Pekar en paket pekare som har allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="1aada-437">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="1aada-438">**status_code** Indikerar resurs status.</span><span class="sxs-lookup"><span data-stu-id="1aada-438">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="1aada-439">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1aada-439">Examples:</span></span>
- <span data-ttu-id="1aada-440">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="1aada-440">**NX_HTTP_STATUS_OK**</span></span>
- <span data-ttu-id="1aada-441">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="1aada-441">**NX_HTTP_STATUS_MODIFIED**</span></span>
- <span data-ttu-id="1aada-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="1aada-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="1aada-443">**CONTENT_LENGTH** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="1aada-443">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="1aada-444">**content_type** Typ av HTTP, t. ex. "text/plain"</span><span class="sxs-lookup"><span data-stu-id="1aada-444">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="1aada-445">**additional_header** Pekare till ytterligare sidhuvud text</span><span class="sxs-lookup"><span data-stu-id="1aada-445">**additional_header** Pointer to additional header text</span></span>

<span data-ttu-id="1aada-446">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-446">**Return Values**</span></span>

- <span data-ttu-id="1aada-447">Ett HTML-huvud har skapats för **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="1aada-447">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="1aada-448">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-448">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-449">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-449">**Allowed From**</span></span>

<span data-ttu-id="1aada-450">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-450">Threads</span></span>

<span data-ttu-id="1aada-451">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-451">**Example**</span></span>

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="1aada-452">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="1aada-452">nx_http_server_callback_generate_response_header_extended</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="1aada-453">Skapa ett svars huvud i en callback-funktion</span><span class="sxs-lookup"><span data-stu-id="1aada-453">Create a response header in a callback function</span></span>

<span data-ttu-id="1aada-454">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-454">**Prototype**</span></span>

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

<span data-ttu-id="1aada-455">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-455">**Description**</span></span>

<span data-ttu-id="1aada-456">Den här tjänsten anropar den interna funktionen _ *nx_http_server_generate_response_header ()* när HTTP-servern svarar på klienten get-, Delete-och Delete-begäranden.</span><span class="sxs-lookup"><span data-stu-id="1aada-456">This service calls the internal function _ *nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="1aada-457">Den är avsedd att användas i funktioner för återanrop i HTTP-server när HTTP-serverprogrammet utformar sitt svar på klienten.</span><span class="sxs-lookup"><span data-stu-id="1aada-457">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="1aada-458">Den här tjänsten ersätter *nx_http_server_callback_generate_response_header ()*.</span><span class="sxs-lookup"><span data-stu-id="1aada-458">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="1aada-459">Den här versionen ger ytterligare längd information till callback-funktionen.</span><span class="sxs-lookup"><span data-stu-id="1aada-459">This version supplies additional length information to the callback function.</span></span>

<span data-ttu-id="1aada-460">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-460">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-461">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-461">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-462">**packet_pptr** Pekar en paket pekare som har allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="1aada-462">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="1aada-463">**status_code** Indikerar resurs status.</span><span class="sxs-lookup"><span data-stu-id="1aada-463">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="1aada-464">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1aada-464">Examples:</span></span>
  - <span data-ttu-id="1aada-465">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="1aada-465">**NX_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="1aada-466">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="1aada-466">**NX_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="1aada-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="1aada-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="1aada-468">**status_code** Längd på status kod</span><span class="sxs-lookup"><span data-stu-id="1aada-468">**status_code** Length of status code</span></span>
- <span data-ttu-id="1aada-469">**CONTENT_LENGTH** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="1aada-469">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="1aada-470">**content_type** Typ av HTTP, t. ex. "text/plain"</span><span class="sxs-lookup"><span data-stu-id="1aada-470">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="1aada-471">**content_type_length** Längd på HTTP-typ</span><span class="sxs-lookup"><span data-stu-id="1aada-471">**content_type_length** Length of HTTP type</span></span>
- <span data-ttu-id="1aada-472">**additional_header** Pekare till ytterligare sidhuvud text</span><span class="sxs-lookup"><span data-stu-id="1aada-472">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="1aada-473">**additional_header_length** Längd på ytterligare rubrik text</span><span class="sxs-lookup"><span data-stu-id="1aada-473">**additional_header_length** Length of additional header text</span></span>

<span data-ttu-id="1aada-474">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-474">**Return Values**</span></span>

- <span data-ttu-id="1aada-475">Ett huvud har skapats för **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="1aada-475">**NX_SUCCESS** (0x00) Successfully created header</span></span>
- <span data-ttu-id="1aada-476">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-476">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-477">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-477">**Allowed From**</span></span>

<span data-ttu-id="1aada-478">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-478">Threads</span></span>

<span data-ttu-id="1aada-479">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-479">**Example**</span></span>

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
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
                length, server_ptr ->
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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="1aada-480">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="1aada-480">nx_http_server_callback_packet_send</span></span>

### <a name="send-an-http-packet-from-callback-function"></a><span data-ttu-id="1aada-481">Skicka ett HTTP-paket från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="1aada-481">Send an HTTP packet from callback function</span></span>

<span data-ttu-id="1aada-482">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-482">**Prototype**</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

<span data-ttu-id="1aada-483">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-483">**Description**</span></span>

<span data-ttu-id="1aada-484">Den här tjänsten skickar ett fullständigt HTTP-servernamn från ett HTTP-motanrop.</span><span class="sxs-lookup"><span data-stu-id="1aada-484">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="1aada-485">HTTP-servern skickar paketet med NX_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="1aada-485">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="1aada-486">HTTP-huvudet och data måste läggas till i paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-486">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="1aada-487">Om retur statusen indikerar ett fel, måste HTTP-programmet släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-487">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="1aada-488">Återanropet ska returnera NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="1aada-488">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="1aada-489">Se *nx_http_server_callback_generate_response_header ()* för ett mer detaljerat exempel.</span><span class="sxs-lookup"><span data-stu-id="1aada-489">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

<span data-ttu-id="1aada-490">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-490">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-491">**server_ptr** Pekare till HTTP Server Control-Block</span><span class="sxs-lookup"><span data-stu-id="1aada-491">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="1aada-492">**packet_ptr** Pekare till det paket som ska skickas</span><span class="sxs-lookup"><span data-stu-id="1aada-492">**packet_ptr** Pointer to the packet to send</span></span>

<span data-ttu-id="1aada-493">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-493">**Return Values**</span></span>

- <span data-ttu-id="1aada-494">**NX_SUCCESS** (0X00) tog emot http-server paket</span><span class="sxs-lookup"><span data-stu-id="1aada-494">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="1aada-495">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-495">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-496">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-496">**Allowed From**</span></span>

<span data-ttu-id="1aada-497">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-497">Threads</span></span>

<span data-ttu-id="1aada-498">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-498">**Example**</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="1aada-499">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="1aada-499">nx_http_server_callback_response_send</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="1aada-500">Skicka svar från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="1aada-500">Send response from callback function</span></span>

<span data-ttu-id="1aada-501">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-501">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

<span data-ttu-id="1aada-502">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-502">**Description**</span></span>

<span data-ttu-id="1aada-503">Den här tjänsten skickar den levererade svars informationen från appens callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="1aada-503">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="1aada-504">Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="1aada-504">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="1aada-505">Observera att om den här funktionen används måste återanrops rutinen returnera status för NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="1aada-505">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="1aada-506">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="1aada-506">This service is deprecated.</span></span> <span data-ttu-id="1aada-507">Utvecklare uppmanas att migrera till *nx_http_server_callback_response_send_extended ().*</span><span class="sxs-lookup"><span data-stu-id="1aada-507">Developers are encouraged to migrate to *nx_http_server_callback_response_send_extended().*</span></span>

<span data-ttu-id="1aada-508">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-508">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-509">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-509">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-510">**sidhuvud** Pekar mot svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-510">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="1aada-511">**information** Pekar mot informations strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-511">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="1aada-512">**additional_info** Pekare till den ytterligare informations strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-512">**additional_info** Pointer to the additional information string.</span></span>

<span data-ttu-id="1aada-513">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-513">**Return Values**</span></span>

- <span data-ttu-id="1aada-514">**NX_SUCCESS** (0X00) har skickat http-serverns svar</span><span class="sxs-lookup"><span data-stu-id="1aada-514">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

<span data-ttu-id="1aada-515">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-515">**Allowed From**</span></span>

<span data-ttu-id="1aada-516">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-516">Threads</span></span>

<span data-ttu-id="1aada-517">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-517">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="1aada-518">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="1aada-518">nx_http_server_callback_response_send_extended</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="1aada-519">Skicka svar från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="1aada-519">Send response from callback function</span></span>

<span data-ttu-id="1aada-520">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-520">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

<span data-ttu-id="1aada-521">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-521">**Description**</span></span>

<span data-ttu-id="1aada-522">Den här tjänsten skickar den levererade svars informationen från appens callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="1aada-522">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="1aada-523">Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="1aada-523">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="1aada-524">Observera att om den här funktionen används måste återanrops rutinen returnera status för NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="1aada-524">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="1aada-525">Den här tjänsten ersätter *nx_http_server_callback_response_send ().*</span><span class="sxs-lookup"><span data-stu-id="1aada-525">This service replaces *nx_http_server_callback_response_send().*</span></span> <span data-ttu-id="1aada-526">Den här versionen tar lång information som indataargument.</span><span class="sxs-lookup"><span data-stu-id="1aada-526">This version takes length information as input argument.</span></span>

<span data-ttu-id="1aada-527">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-527">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-528">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-528">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-529">**sidhuvud** Pekar mot svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-529">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="1aada-530">**header_length** Längd på svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-530">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="1aada-531">**information** Pekar mot informations strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-531">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="1aada-532">**information_length** Längden på informations strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-532">**information_length** Length of the information string.</span></span>
- <span data-ttu-id="1aada-533">**additional_info** Pekare till den ytterligare informations strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-533">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="1aada-534">**additional_info_length** Den ytterligare informations strängens längd.</span><span class="sxs-lookup"><span data-stu-id="1aada-534">**additional_info_length** Length of the additional information string.</span></span>

<span data-ttu-id="1aada-535">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-535">**Return Values**</span></span>

- <span data-ttu-id="1aada-536">**NX_SUCCESS** (0x00) skickade Server svaret</span><span class="sxs-lookup"><span data-stu-id="1aada-536">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

<span data-ttu-id="1aada-537">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-537">**Allowed From**</span></span>

<span data-ttu-id="1aada-538">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-538">Threads</span></span>

<span data-ttu-id="1aada-539">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-539">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="1aada-540">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="1aada-540">nx_http_server_content_get</span></span>

### <a name="get-content-from-the-request"></a><span data-ttu-id="1aada-541">Hämta innehåll från begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-541">Get content from the request</span></span>

<span data-ttu-id="1aada-542">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-542">**Prototype**</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

<span data-ttu-id="1aada-543">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-543">**Description**</span></span>

<span data-ttu-id="1aada-544">Den här tjänsten försöker hämta den angivna mängden innehåll från begäran eller skicka HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-544">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="1aada-545">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="1aada-545">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="1aada-546">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="1aada-546">This service is deprecated.</span></span> <span data-ttu-id="1aada-547">Utvecklare uppmanas att migrera till nx_http_server_content_get_extended ().</span><span class="sxs-lookup"><span data-stu-id="1aada-547">Developers are encouraged to migrate to nx_http_server_content_get_extended().</span></span>

<span data-ttu-id="1aada-548">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-548">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-549">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-549">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-550">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-550">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="1aada-551">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="1aada-551">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="1aada-552">**byte_offset** Antal byte som ska förskjutas i innehålls ytan.</span><span class="sxs-lookup"><span data-stu-id="1aada-552">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="1aada-553">**destination_ptr** Pekar till mål avsnittet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="1aada-553">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="1aada-554">**destination_size** Maximalt antal byte som är tillgängliga i mål arean.</span><span class="sxs-lookup"><span data-stu-id="1aada-554">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="1aada-555">**actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.</span><span class="sxs-lookup"><span data-stu-id="1aada-555">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="1aada-556">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-556">**Return Values**</span></span>

- <span data-ttu-id="1aada-557">**NX_SUCCESS** (0X00) http-serverns innehåll Hämta</span><span class="sxs-lookup"><span data-stu-id="1aada-557">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="1aada-558">Internt fel för **NX_HTTP_ERROR** (0XE0) http-server</span><span class="sxs-lookup"><span data-stu-id="1aada-558">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="1aada-559">**NX_HTTP_DATA_END** (0XE7) slut på innehåll i begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-559">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="1aada-560">**NX_HTTP_TIMEOUT** (0xE1) timeout för http-server i Hämta nästa paket med innehåll</span><span class="sxs-lookup"><span data-stu-id="1aada-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="1aada-561">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-561">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-562">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-562">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-563">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-563">**Allowed From**</span></span>

<span data-ttu-id="1aada-564">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-564">Threads</span></span>

<span data-ttu-id="1aada-565">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-565">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="1aada-566">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="1aada-566">nx_http_server_content_get_extended</span></span>

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a><span data-ttu-id="1aada-567">Hämta innehåll från begäran/har stöd för längd för längd innehåll</span><span class="sxs-lookup"><span data-stu-id="1aada-567">Get content from the request/supports zero length Content Length</span></span>

<span data-ttu-id="1aada-568">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-568">**Prototype**</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

<span data-ttu-id="1aada-569">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-569">**Description**</span></span>

<span data-ttu-id="1aada-570">Den här tjänsten är nästan identisk med *nx_http_server_content_get ()*; det försöker hämta den angivna mängden innehåll från POST-eller klient förfrågan.</span><span class="sxs-lookup"><span data-stu-id="1aada-570">This service is almost identical to *nx_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="1aada-571">Den hanterar dock begär Anden med innehålls längd noll (' Empty Request ') som en giltig begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-571">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="1aada-572">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="1aada-572">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="1aada-573">Den här tjänsten ersätter *nx_http_server_content_get ().*</span><span class="sxs-lookup"><span data-stu-id="1aada-573">This service replaces *nx_http_server_content_get().*</span></span> <span data-ttu-id="1aada-574">Den här versionen kräver att anroparen tillhandahåller ytterligare längd information.</span><span class="sxs-lookup"><span data-stu-id="1aada-574">This version requires caller to supply additional length information.</span></span>

<span data-ttu-id="1aada-575">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-575">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-576">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-576">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-577">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-577">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="1aada-578">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="1aada-578">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="1aada-579">**byte_offset** Antal byte som ska förskjutas i innehålls ytan.</span><span class="sxs-lookup"><span data-stu-id="1aada-579">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="1aada-580">**destination_ptr** Pekar till mål avsnittet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="1aada-580">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="1aada-581">**destination_size** Maximalt antal byte som är tillgängliga i mål arean.</span><span class="sxs-lookup"><span data-stu-id="1aada-581">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="1aada-582">**actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.</span><span class="sxs-lookup"><span data-stu-id="1aada-582">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="1aada-583">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-583">**Return Values**</span></span>

- <span data-ttu-id="1aada-584">**NX_SUCCESS** (0X00) http-innehållet Hämta</span><span class="sxs-lookup"><span data-stu-id="1aada-584">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="1aada-585">Internt fel för **NX_HTTP_ERROR** (0XE0) http-server</span><span class="sxs-lookup"><span data-stu-id="1aada-585">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="1aada-586">**NX_HTTP_DATA_END** (0XE7) slut på innehåll i begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-586">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="1aada-587">**NX_HTTP_TIMEOUT** (0xE1) timeout för http-server i Hämta nästa paket</span><span class="sxs-lookup"><span data-stu-id="1aada-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="1aada-588">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-589">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-589">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-590">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-590">**Allowed From**</span></span>

<span data-ttu-id="1aada-591">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-591">Threads</span></span>

<span data-ttu-id="1aada-592">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-592">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="1aada-593">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="1aada-593">nx_http_server_content_length_get</span></span>

### <a name="get-length-of-content-in-the-request"></a><span data-ttu-id="1aada-594">Hämta längden på innehållet i begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-594">Get length of content in the request</span></span>

<span data-ttu-id="1aada-595">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-595">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
<span data-ttu-id="1aada-596">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-596">**Description**</span></span>

<span data-ttu-id="1aada-597">Den här tjänsten försöker hämta HTTP-innehållets längd i det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-597">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="1aada-598">Om det inte finns något HTTP-innehåll returnerar den här rutinen värdet noll.</span><span class="sxs-lookup"><span data-stu-id="1aada-598">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="1aada-599">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="1aada-599">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="1aada-600">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="1aada-600">This service is deprecated.</span></span> <span data-ttu-id="1aada-601">Utvecklare uppmanas att migrera till nx_http_server_content_length_get_extended ().</span><span class="sxs-lookup"><span data-stu-id="1aada-601">Developers are encouraged to migrate to nx_http_server_content_length_get_extended().</span></span>

<span data-ttu-id="1aada-602">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-602">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-603">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-603">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="1aada-604">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="1aada-604">Note that this packet must not be released by the request notify callback.</span></span>

<span data-ttu-id="1aada-605">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-605">**Return Values**</span></span>

- <span data-ttu-id="1aada-606">**innehålls längd** Vid fel returneras värdet noll</span><span class="sxs-lookup"><span data-stu-id="1aada-606">**content length** On error, a value of zero is returned</span></span>

<span data-ttu-id="1aada-607">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-607">**Allowed From**</span></span>

<span data-ttu-id="1aada-608">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-608">Threads</span></span>

<span data-ttu-id="1aada-609">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-609">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="1aada-610">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="1aada-610">nx_http_server_content_length_get_extended</span></span>

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a><span data-ttu-id="1aada-611">Hämta längden på innehållet i begäran/stöder innehålls längden noll värde</span><span class="sxs-lookup"><span data-stu-id="1aada-611">Get length of content in the request/supports Content Length of zero value</span></span>

<span data-ttu-id="1aada-612">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-612">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

<span data-ttu-id="1aada-613">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-613">**Description**</span></span>

<span data-ttu-id="1aada-614">Den här tjänsten liknar *nx_http_server_content_length_get ()*; försöker hämta längden för HTTP-innehållet i det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-614">This service is similar to *nx_http_server_content_length_get()*; attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="1aada-615">Returvärdet visar dock att status för slut för ande har slutförts, och det faktiska värdet för längd returneras i incontent_length.</span><span class="sxs-lookup"><span data-stu-id="1aada-615">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="1aada-616">Om det inte finns något HTTP-innehåll/innehålls längd = 0, returnerar den här rutinen fortfarande statusen slutförd och content_length inmatare pekar på en giltig längd (noll).</span><span class="sxs-lookup"><span data-stu-id="1aada-616">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="1aada-617">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="1aada-617">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="1aada-618">Den här tjänsten ersätter *nx_http_server_content_length_get*().</span><span class="sxs-lookup"><span data-stu-id="1aada-618">This service replaces *nx_http_server_content_length_get*().</span></span>

<span data-ttu-id="1aada-619">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-619">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-620">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-620">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="1aada-621">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="1aada-621">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="1aada-622">**CONTENT_LENGTH** Pekare till värde som hämtats från fältet innehålls längd</span><span class="sxs-lookup"><span data-stu-id="1aada-622">**content_length** Pointer to value retrieved from Content Length field</span></span>

<span data-ttu-id="1aada-623">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-623">**Return Values**</span></span>

- <span data-ttu-id="1aada-624">**NX_SUCCESS** (0X00) http-serverns innehåll Hämta</span><span class="sxs-lookup"><span data-stu-id="1aada-624">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="1aada-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0XEF) felaktigt http-huvudformat</span><span class="sxs-lookup"><span data-stu-id="1aada-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
- <span data-ttu-id="1aada-626">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-626">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-627">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-627">**Allowed From**</span></span>

<span data-ttu-id="1aada-628">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-628">Threads</span></span>

<span data-ttu-id="1aada-629">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-629">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="1aada-630">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="1aada-630">nx_http_server_create</span></span>

### <a name="create-an-http-server-instance"></a><span data-ttu-id="1aada-631">Skapa en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="1aada-631">Create an HTTP Server instance</span></span>

<span data-ttu-id="1aada-632">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-632">**Prototype**</span></span>

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

<span data-ttu-id="1aada-633">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-633">**Description**</span></span>

<span data-ttu-id="1aada-634">Den här tjänsten skapar en HTTP-serverinstans som körs i kontexten för en egen ThreadX-tråd.</span><span class="sxs-lookup"><span data-stu-id="1aada-634">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="1aada-635">De valfria rutinerna för *authentication_check* och *request_notify* programbegäran ger program kontroll över den grundläggande driften av HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-635">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="1aada-636">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-636">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-637">**http_server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-637">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="1aada-638">**http_server_name** Pekare till HTTP-serverns namn.</span><span class="sxs-lookup"><span data-stu-id="1aada-638">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="1aada-639">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-639">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="1aada-640">**media_ptr** Pekare till den tidigare skapade FileX Media-instansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-640">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="1aada-641">**stack_ptr** Pekar på ett stack-fält för HTTP-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="1aada-641">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="1aada-642">**stack_size** Pekare till HTTP-server trådens stack storlek.</span><span class="sxs-lookup"><span data-stu-id="1aada-642">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="1aada-643">**authentication_check** Funktions pekare till programmets verifierings kontroll rutin.</span><span class="sxs-lookup"><span data-stu-id="1aada-643">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="1aada-644">Den här rutinen anropas för varje HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-644">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="1aada-645">Om den här parametern är NULL utförs ingen autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-645">If this parameter is NULL no authentication will be performed.</span></span>
- <span data-ttu-id="1aada-646">**request_notify** Funktions pekare till program begär ande aviserings rutin.</span><span class="sxs-lookup"><span data-stu-id="1aada-646">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="1aada-647">Den här rutinen anropas före HTTP-serverns bearbetning av begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-647">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="1aada-648">Detta gör att resurs namnet kan omdirigeras eller fält i en resurs uppdateras innan HTTP-klientbegäran slutförs.</span><span class="sxs-lookup"><span data-stu-id="1aada-648">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

<span data-ttu-id="1aada-649">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-649">**Return Values**</span></span>

- <span data-ttu-id="1aada-650">**NX_SUCCESS** (0X00) http-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="1aada-650">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="1aada-651">NX_PTR_ERROR (0x07) ogiltig pekare för HTTP-server, IP, media, stack eller Packet-pool.</span><span class="sxs-lookup"><span data-stu-id="1aada-651">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="1aada-652">NX_HTTP_POOL_ERROR (0xE9) paket nytto lasten för poolen är inte tillräckligt stor för att rymma fullständig HTTP-begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-652">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

<span data-ttu-id="1aada-653">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-653">**Allowed From**</span></span>

<span data-ttu-id="1aada-654">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="1aada-654">Initialization, Threads</span></span>

<span data-ttu-id="1aada-655">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-655">**Example**</span></span>

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="1aada-656">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="1aada-656">nx_http_server_delete</span></span>

### <a name="delete-an-http-server-instance"></a><span data-ttu-id="1aada-657">Ta bort en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="1aada-657">Delete an HTTP Server instance</span></span>

<span data-ttu-id="1aada-658">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-658">**Prototype**</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="1aada-659">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-659">**Description**</span></span>

<span data-ttu-id="1aada-660">Den här tjänsten tar bort en tidigare skapad HTTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="1aada-660">This service deletes a previously created HTTP Server instance.</span></span>

<span data-ttu-id="1aada-661">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-661">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-662">**http_server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="1aada-662">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

<span data-ttu-id="1aada-663">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-663">**Return Values**</span></span>

- <span data-ttu-id="1aada-664">**NX_SUCCESS** (0X00) http-servern har tagits bort</span><span class="sxs-lookup"><span data-stu-id="1aada-664">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="1aada-665">NX_PTR_ERROR (0x07) ogiltig HTTP-server pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-665">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="1aada-666">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-666">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-667">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-667">**Allowed From**</span></span>

<span data-ttu-id="1aada-668">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-668">Threads</span></span>

<span data-ttu-id="1aada-669">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-669">**Example**</span></span>

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="1aada-670">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="1aada-670">nx_http_server_get_entity_content</span></span>

### <a name="retrieve-the-location-and-length-of-entity-data"></a><span data-ttu-id="1aada-671">Hämta plats och längd för enhets data</span><span class="sxs-lookup"><span data-stu-id="1aada-671">Retrieve the location and length of entity data</span></span>

<span data-ttu-id="1aada-672">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-672">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="1aada-673">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-673">**Description**</span></span>

<span data-ttu-id="1aada-674">Den här tjänsten bestämmer platsen för starten av data i den aktuella flerdelade entiteten i mottagna klient meddelanden och längden på data som inte inkluderar begränsnings strängen.</span><span class="sxs-lookup"><span data-stu-id="1aada-674">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="1aada-675">Internt HTTP-Server uppdaterar sina egna förskjutningar så att den här funktionen kan anropas igen på samma klient-datagram för meddelanden med flera entiteter.</span><span class="sxs-lookup"><span data-stu-id="1aada-675">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="1aada-676">Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-676">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="1aada-677">Observera att NX_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1aada-677">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="1aada-678">Se *nx_http_server_get_entity_header* för mer information.</span><span class="sxs-lookup"><span data-stu-id="1aada-678">See *nx_http_server_get_entity_header* for more details.</span></span>

<span data-ttu-id="1aada-679">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-679">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-680">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="1aada-680">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="1aada-681">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="1aada-681">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="1aada-682">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-682">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="1aada-683">**available_offset** Pekare för förskjutning av enhets data från paketets lägga-pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-683">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="1aada-684">**available_length** Pekare till längd på enhets data</span><span class="sxs-lookup"><span data-stu-id="1aada-684">**available_length** Pointer to length of entity data</span></span>

<span data-ttu-id="1aada-685">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-685">**Return Values**</span></span>

- <span data-ttu-id="1aada-686">**NX_SUCCESS** (0X00) har hämtat storlek och plats för enhetens innehåll</span><span class="sxs-lookup"><span data-stu-id="1aada-686">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="1aada-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) för HTTP-serverns interna flerdelade markörer finns redan</span><span class="sxs-lookup"><span data-stu-id="1aada-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="1aada-688">Internt fel för NX_HTTP_ERROR (0xE0) HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="1aada-688">NX_HTTP_ERROR (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="1aada-689">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-689">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-690">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-690">**Allowed From**</span></span>

<span data-ttu-id="1aada-691">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-691">Threads</span></span>

<span data-ttu-id="1aada-692">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-692">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="1aada-693">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="1aada-693">nx_http_server_get_entity_header</span></span>

### <a name="retrieve-the-contents-of-entity-header"></a><span data-ttu-id="1aada-694">Hämta innehållet i enhets huvudet</span><span class="sxs-lookup"><span data-stu-id="1aada-694">Retrieve the contents of entity header</span></span>

<span data-ttu-id="1aada-695">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-695">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

<span data-ttu-id="1aada-696">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-696">**Description**</span></span>

<span data-ttu-id="1aada-697">Den här tjänsten hämtar enhets rubriken till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="1aada-697">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="1aada-698">Internt HTTP-Server uppdaterar sin egen pekare för att hitta nästa flerdelade entitet i ett klient-datagram med flera entitets-rubriker.</span><span class="sxs-lookup"><span data-stu-id="1aada-698">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="1aada-699">Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-699">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="1aada-700">Observera att NX_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1aada-700">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="1aada-701">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-701">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-702">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="1aada-702">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="1aada-703">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="1aada-703">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="1aada-704">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-704">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="1aada-705">**entity_header_buffer** Pekare till plats för lagring av enhets huvud</span><span class="sxs-lookup"><span data-stu-id="1aada-705">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="1aada-706">**buffer_size** Storlek på indatabufferten</span><span class="sxs-lookup"><span data-stu-id="1aada-706">**buffer_size** Size of input buffer</span></span>

<span data-ttu-id="1aada-707">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-707">**Return Values**</span></span>

- <span data-ttu-id="1aada-708">**NX_SUCCESS** (0X00) har hämtat enhets huvud</span><span class="sxs-lookup"><span data-stu-id="1aada-708">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
- <span data-ttu-id="1aada-709">**NX_HTTP_NOT_FOUND (0xE6)** Fältet för enhets huvud hittades inte</span><span class="sxs-lookup"><span data-stu-id="1aada-709">**NX_HTTP_NOT_FOUND (0xE6)** Entity header field not found</span></span>
- <span data-ttu-id="1aada-710">**NX_HTTP_TIMEOUT (0xE1)** Tid för att ta emot nästa paket för klient meddelande med multipaket</span><span class="sxs-lookup"><span data-stu-id="1aada-710">**NX_HTTP_TIMEOUT (0xE1)** Time expired to receive next packet for multipacket client message</span></span> 
- <span data-ttu-id="1aada-711">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-711">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-712">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-712">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="1aada-713">Internt HTTP-fel NX_HTTP_ERROR (0xE0)</span><span class="sxs-lookup"><span data-stu-id="1aada-713">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>

<span data-ttu-id="1aada-714">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-714">**Allowed From**</span></span>

<span data-ttu-id="1aada-715">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-715">Threads</span></span>

<span data-ttu-id="1aada-716">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-716">**Example**</span></span>

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

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
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="1aada-717">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="1aada-717">nx_http_server_gmt_callback_set</span></span>

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a><span data-ttu-id="1aada-718">Ange återanropet för att få GMT-datum och-tid</span><span class="sxs-lookup"><span data-stu-id="1aada-718">Set the callback to obtain GMT date and time</span></span>

<span data-ttu-id="1aada-719">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-719">**Prototype**</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="1aada-720">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-720">**Description**</span></span>

<span data-ttu-id="1aada-721">Den här tjänsten anger återanropet för att hämta GMT-datum och-tid med en tidigare skapad HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="1aada-721">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="1aada-722">Den här tjänsten anropas med HTTP-servern för att skapa en rubrik i HTTP-server svar på klienten.</span><span class="sxs-lookup"><span data-stu-id="1aada-722">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

<span data-ttu-id="1aada-723">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-723">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-724">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="1aada-724">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="1aada-725">**gmt_get** Pekare till GMT-motanrop</span><span class="sxs-lookup"><span data-stu-id="1aada-725">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="1aada-726">**datum** Pekare till det datum som hämtades</span><span class="sxs-lookup"><span data-stu-id="1aada-726">**date** Pointer to the date retrieved</span></span>

<span data-ttu-id="1aada-727">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-727">**Return Values**</span></span>

- <span data-ttu-id="1aada-728">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="1aada-728">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="1aada-729">NX_PTR_ERROR (0x07) ogiltig paket-eller parameter pekare.</span><span class="sxs-lookup"><span data-stu-id="1aada-729">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

<span data-ttu-id="1aada-730">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-730">**Allowed From**</span></span>

<span data-ttu-id="1aada-731">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-731">Threads</span></span>

<span data-ttu-id="1aada-732">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-732">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="1aada-733">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="1aada-733">nx_http_server_invalid_userpassword_notify_set</span></span>

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a><span data-ttu-id="1aada-734">Ange motringning till för att hantera Ogiltig användare/lösen ord</span><span class="sxs-lookup"><span data-stu-id="1aada-734">Set the callback to to handle invalid user/password</span></span>

<span data-ttu-id="1aada-735">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-735">**Prototype**</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

<span data-ttu-id="1aada-736">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-736">**Description**</span></span>

<span data-ttu-id="1aada-737">Den här tjänsten anger återanropet som anropas när ett ogiltigt användar namn och lösen ord tas emot i en klient get-,-eller Delete-begäran, antingen av Digest eller grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-737">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="1aada-738">HTTP-servern måste ha skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="1aada-738">The HTTP server must be previously created.</span></span>

<span data-ttu-id="1aada-739">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-739">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-740">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="1aada-740">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="1aada-741">**invalid_username_password_callback** Pekare till Ogiltig användare/pass motringning</span><span class="sxs-lookup"><span data-stu-id="1aada-741">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="1aada-742">**resurs** Pekare till resursen som anges av klienten</span><span class="sxs-lookup"><span data-stu-id="1aada-742">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="1aada-743">**client_address** Klient adress</span><span class="sxs-lookup"><span data-stu-id="1aada-743">**client_address** Client address</span></span>
- <span data-ttu-id="1aada-744">**request_type** Anger typ av klient förfrågan.</span><span class="sxs-lookup"><span data-stu-id="1aada-744">**request_type** Indicates client request type.</span></span> <span data-ttu-id="1aada-745">Kanske:</span><span class="sxs-lookup"><span data-stu-id="1aada-745">May be:</span></span>
  - <span data-ttu-id="1aada-746">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="1aada-746">NX_HTTP_SERVER_GET_REQUEST</span></span>
  - <span data-ttu-id="1aada-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="1aada-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span></span>
  - <span data-ttu-id="1aada-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="1aada-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span></span>

<span data-ttu-id="1aada-749">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-749">**Return Values**</span></span>

- <span data-ttu-id="1aada-750">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="1aada-750">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="1aada-751">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-751">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-752">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-752">**Allowed From**</span></span>

<span data-ttu-id="1aada-753">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-753">Threads</span></span>

<span data-ttu-id="1aada-754">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-754">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="1aada-755">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="1aada-755">nx_http_server_mime_maps_additional_set</span></span>

### <a name="set-additional-mime-maps-for-html"></a><span data-ttu-id="1aada-756">Ange ytterligare MIME-mappningar för HTML</span><span class="sxs-lookup"><span data-stu-id="1aada-756">Set additional MIME maps for HTML</span></span> 

<span data-ttu-id="1aada-757">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-757">**Prototype**</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

<span data-ttu-id="1aada-758">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-758">**Description**</span></span>

<span data-ttu-id="1aada-759">Med den här tjänsten kan HTTP-programutvecklaren lägga till ytterligare MIME-typer från de standard-MIME-typer som anges av NetX HTTP-server (se *nx_http_server_get_type* för lista över definierade typer).</span><span class="sxs-lookup"><span data-stu-id="1aada-759">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="1aada-760">När en klientbegäran tas emot, t. ex. en GET-begäran, parsar HTTP-servern den begärda filtypen från HTTP-huvudet med en prioriterad uppsättning av ytterligare MIME-mappningar och om ingen matchning hittas söker den efter en matchning i standard-MIME-mappningen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="1aada-760">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="1aada-761">Om ingen matchning hittas är MIME-typen Standard text/plain.</span><span class="sxs-lookup"><span data-stu-id="1aada-761">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="1aada-762">Om begär ande aviserings funktionen har registrerats med HTTP-servern kan aviseringen meddela motringning anropa *nx_http_server_type_get* för att parsa filtypen.</span><span class="sxs-lookup"><span data-stu-id="1aada-762">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_get* to parse the file type.</span></span>

<span data-ttu-id="1aada-763">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-763">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-764">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="1aada-764">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="1aada-765">**mime_maps** Pekare till en MIME-kart mat ris</span><span class="sxs-lookup"><span data-stu-id="1aada-765">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="1aada-766">**mime_map_num** Antal MIME-mappningar i matrisen</span><span class="sxs-lookup"><span data-stu-id="1aada-766">**mime_map_num** Number of MIME maps in array</span></span>

<span data-ttu-id="1aada-767">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-767">**Return Values**</span></span>

- <span data-ttu-id="1aada-768">**NX_SUCCESS** (0X00) http-SERVERNS MIME-mappning har angetts</span><span class="sxs-lookup"><span data-stu-id="1aada-768">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="1aada-769">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-769">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-770">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-770">**Allowed From**</span></span>

<span data-ttu-id="1aada-771">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="1aada-771">Initialization, Threads</span></span>

<span data-ttu-id="1aada-772">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-772">**Example**</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="1aada-773">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="1aada-773">nx_http_server_packet_content_find</span></span>

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a><span data-ttu-id="1aada-774">Extrahera innehålls längd och ange pekare till början av data</span><span class="sxs-lookup"><span data-stu-id="1aada-774">Extract content length and set pointer to start of data</span></span>

<span data-ttu-id="1aada-775">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-775">**Prototype**</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

<span data-ttu-id="1aada-776">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-776">**Description**</span></span>

<span data-ttu-id="1aada-777">Den här tjänsten extraherar innehålls längden från HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="1aada-777">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="1aada-778">Den uppdaterar också det tillhandahållna paketet enligt följande: paketets lägga-pekare (start på platsen för den pakettyp som ska skrivas till) har angetts till HTTP-innehållet (data) precis skickade HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="1aada-778">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="1aada-779">Om början av innehållet inte hittas i det aktuella paketet väntar funktionen på nästa paket som ska tas emot med alternativet NX_HTTP_SERVER_TIMEOUT_RECEIVE vänta.</span><span class="sxs-lookup"><span data-stu-id="1aada-779">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="1aada-780">Observera att detta inte ska anropas innan du anropar *nx_http_server_get_entity_header ()* eftersom den ändrar lägga-pekaren förbi enhets huvudet.</span><span class="sxs-lookup"><span data-stu-id="1aada-780">Note this should not be called before calling *nx_http_server_get_entity_header()* because it modifies the prepend pointer past the entity header.</span></span>

<span data-ttu-id="1aada-781">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-781">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-782">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="1aada-782">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="1aada-783">**packet_ptr** Pekare till paket pekare för att returnera paketet med uppdaterad lägga-pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-783">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="1aada-784">**CONTENT_LENGTH** Pekare som extraheras content_length</span><span class="sxs-lookup"><span data-stu-id="1aada-784">**content_length** Pointer to extracted content_length</span></span>

<span data-ttu-id="1aada-785">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-785">**Return Values**</span></span>

- <span data-ttu-id="1aada-786">**NX_SUCCESS** (0X00) http-innehålls längd hittades och paketet har uppdaterats</span><span class="sxs-lookup"><span data-stu-id="1aada-786">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="1aada-787">**NX_HTTP_TIMEOUT** (0XE1) tid för att vänta på nästa paket</span><span class="sxs-lookup"><span data-stu-id="1aada-787">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="1aada-788">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-788">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-789">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-789">**Allowed From**</span></span>

<span data-ttu-id="1aada-790">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-790">Threads</span></span>

<span data-ttu-id="1aada-791">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-791">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="1aada-792">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="1aada-792">nx_http_server_packet_get</span></span>

### <a name="receive-the-next-http-packet"></a><span data-ttu-id="1aada-793">Ta emot nästa HTTP-paket</span><span class="sxs-lookup"><span data-stu-id="1aada-793">Receive the next HTTP packet</span></span>

<span data-ttu-id="1aada-794">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-794">**Prototype**</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

<span data-ttu-id="1aada-795">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-795">**Description**</span></span>

<span data-ttu-id="1aada-796">Den här tjänsten returnerar nästa paket som tas emot på HTTP-serverns socket.</span><span class="sxs-lookup"><span data-stu-id="1aada-796">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="1aada-797">Alternativet vänte för att ta emot ett paket är NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="1aada-797">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="1aada-798">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-798">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-799">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="1aada-799">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="1aada-800">**packet_ptr** Pekare till mottaget paket</span><span class="sxs-lookup"><span data-stu-id="1aada-800">**packet_ptr** Pointer to received packet</span></span>

<span data-ttu-id="1aada-801">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-801">**Return Values**</span></span>

- <span data-ttu-id="1aada-802">**NX_SUCCESS** (0X00) har tagit emot nästa http-paket</span><span class="sxs-lookup"><span data-stu-id="1aada-802">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="1aada-803">**NX_HTTP_TIMEOUT** (0XE1) tid för att vänta på nästa paket</span><span class="sxs-lookup"><span data-stu-id="1aada-803">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="1aada-804">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-804">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-805">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-805">**Allowed From**</span></span>

<span data-ttu-id="1aada-806">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-806">Threads</span></span>

<span data-ttu-id="1aada-807">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-807">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="1aada-808">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="1aada-808">nx_http_server_param_get</span></span>

### <a name="get-parameter-from-the-request"></a><span data-ttu-id="1aada-809">Hämta parameter från begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-809">Get parameter from the request</span></span>

<span data-ttu-id="1aada-810">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-810">**Prototype**</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

<span data-ttu-id="1aada-811">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-811">**Description**</span></span>

<span data-ttu-id="1aada-812">Den här tjänsten försöker hämta angiven HTTP URL-parameter i det angivna paketet för begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-812">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="1aada-813">Om den begärda HTTP-parametern inte finns, returnerar den här rutinen statusen NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="1aada-813">If the requested HTTP parameter is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="1aada-814">Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="1aada-814">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="1aada-815">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-815">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-816">**packet_ptr** Pekare till HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-816">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="1aada-817">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-817">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="1aada-818">**param_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i parameter listan.</span><span class="sxs-lookup"><span data-stu-id="1aada-818">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="1aada-819">**param_ptr** Mål arean för att kopiera parametern.</span><span class="sxs-lookup"><span data-stu-id="1aada-819">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="1aada-820">**max_param_size** Maximal storlek för parameter mål arean.</span><span class="sxs-lookup"><span data-stu-id="1aada-820">**max_param_size** Maximum size of the parameter destination area.</span></span>

<span data-ttu-id="1aada-821">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-821">**Return Values**</span></span>

- <span data-ttu-id="1aada-822">**NX_SUCCESS** (0X00) http-server parametern get har slutförts</span><span class="sxs-lookup"><span data-stu-id="1aada-822">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="1aada-823">Det gick inte att hitta den angivna parametern **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="1aada-823">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
- <span data-ttu-id="1aada-824">Parametern för **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) är inte korrekt avslutad</span><span class="sxs-lookup"><span data-stu-id="1aada-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
- <span data-ttu-id="1aada-825">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-825">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-826">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-827">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-827">**Allowed From**</span></span>

<span data-ttu-id="1aada-828">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-828">Threads</span></span>

<span data-ttu-id="1aada-829">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-829">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="1aada-830">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="1aada-830">nx_http_server_query_get</span></span>

### <a name="get-query-from-the-request"></a><span data-ttu-id="1aada-831">Hämta fråga från begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-831">Get query from the request</span></span>

<span data-ttu-id="1aada-832">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-832">**Prototype**</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

<span data-ttu-id="1aada-833">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-833">**Description**</span></span>

<span data-ttu-id="1aada-834">Den här tjänsten försöker hämta angiven HTTP URL-fråga i det angivna paketet för begäran.</span><span class="sxs-lookup"><span data-stu-id="1aada-834">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="1aada-835">Om begärd HTTP-fråga inte finns, returnerar den här rutinen statusen NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="1aada-835">If the requested HTTP query is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="1aada-836">Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="1aada-836">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="1aada-837">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-837">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-838">**packet_ptr** Pekare till HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="1aada-838">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="1aada-839">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="1aada-839">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="1aada-840">**query_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i listan över frågor.</span><span class="sxs-lookup"><span data-stu-id="1aada-840">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="1aada-841">**query_ptr** Mål områden för att kopiera frågan.</span><span class="sxs-lookup"><span data-stu-id="1aada-841">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="1aada-842">**max_query_size** Maximal storlek på mål arean för frågan.</span><span class="sxs-lookup"><span data-stu-id="1aada-842">**max_query_size** Maximum size of the query destination area.</span></span>

<span data-ttu-id="1aada-843">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-843">**Return Values**</span></span>

- <span data-ttu-id="1aada-844">**NX_SUCCESS** (0X00) lyckad http-server fråga Hämta</span><span class="sxs-lookup"><span data-stu-id="1aada-844">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="1aada-845">**NX_HTTP_FAILED** (0XE2) frågan är för liten.</span><span class="sxs-lookup"><span data-stu-id="1aada-845">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
- <span data-ttu-id="1aada-846">Det gick inte att hitta den angivna frågan för **NX_HTTP_NOT_FOUND** (0xE6)</span><span class="sxs-lookup"><span data-stu-id="1aada-846">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
- <span data-ttu-id="1aada-847">**NX_HTTP_NO_QUERY_PARSED** (0XF2) ingen fråga i klient förfrågan</span><span class="sxs-lookup"><span data-stu-id="1aada-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
- <span data-ttu-id="1aada-848">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-848">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-849">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-849">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-850">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-850">**Allowed From**</span></span>

<span data-ttu-id="1aada-851">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-851">Threads</span></span>

<span data-ttu-id="1aada-852">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-852">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
<span data-ttu-id="1aada-853">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="1aada-853">nx_http_server_start</span></span>

### <a name="start-the-http-server"></a><span data-ttu-id="1aada-854">Starta HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="1aada-854">Start the HTTP Server</span></span>

<span data-ttu-id="1aada-855">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-855">**Prototype**</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="1aada-856">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-856">**Description**</span></span>

<span data-ttu-id="1aada-857">Den här tjänsten startar den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-857">This service starts the previously create HTTP Server instance.</span></span>

<span data-ttu-id="1aada-858">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-858">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-859">**http_server_ptr** Pekare till HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-859">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="1aada-860">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-860">**Return Values**</span></span>

- <span data-ttu-id="1aada-861">**NX_SUCCESS** (0X00) http-servern har startats</span><span class="sxs-lookup"><span data-stu-id="1aada-861">**NX_SUCCESS** (0x00) Successful HTTP Server start</span></span>
- <span data-ttu-id="1aada-862">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-862">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-863">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-863">**Allowed From**</span></span>

<span data-ttu-id="1aada-864">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="1aada-864">Initialization, Threads</span></span>

<span data-ttu-id="1aada-865">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-865">**Example**</span></span>

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="1aada-866">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="1aada-866">nx_http_server_stop</span></span>

### <a name="stop-the-http-server"></a><span data-ttu-id="1aada-867">Stoppa HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="1aada-867">Stop the HTTP Server</span></span>

<span data-ttu-id="1aada-868">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-868">**Prototype**</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="1aada-869">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-869">**Description**</span></span>

<span data-ttu-id="1aada-870">Den här tjänsten stoppar den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-870">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="1aada-871">Den här rutinen ska anropas innan en HTTP-serverinstans tas bort.</span><span class="sxs-lookup"><span data-stu-id="1aada-871">This routine should be called prior to deleting an HTTP Server instance.</span></span>

<span data-ttu-id="1aada-872">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-872">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-873">**http_server_ptr** Pekare till HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="1aada-873">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="1aada-874">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-874">**Return Values**</span></span>

- <span data-ttu-id="1aada-875">**NX_SUCCESS** (0X00) http-servern stoppades</span><span class="sxs-lookup"><span data-stu-id="1aada-875">**NX_SUCCESS** (0x00) Successful HTTP Server stop</span></span>
- <span data-ttu-id="1aada-876">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-876">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-877">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="1aada-877">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="1aada-878">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-878">**Allowed From**</span></span>

<span data-ttu-id="1aada-879">Konversation</span><span class="sxs-lookup"><span data-stu-id="1aada-879">Threads</span></span>

<span data-ttu-id="1aada-880">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-880">**Example**</span></span>

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="1aada-881">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="1aada-881">nx_http_server_type_get</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="1aada-882">Extrahera filtypen från klientens HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-882">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="1aada-883">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-883">**Prototype**</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

<span data-ttu-id="1aada-884">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-884">**Description**</span></span>

<span data-ttu-id="1aada-885">Den här tjänsten extraherar typen av HTTP-begäran i bufferten *http_type_string* och dess längd i returvärdet från *indatabufferten, vanligt vis URL: en*.</span><span class="sxs-lookup"><span data-stu-id="1aada-885">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="1aada-886">Om det inte går att hitta någon MIME-mappning används standard typen text/plain.</span><span class="sxs-lookup"><span data-stu-id="1aada-886">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="1aada-887">Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning.</span><span class="sxs-lookup"><span data-stu-id="1aada-887">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="1aada-888">Standard-MIME-mappningarna i NetX HTTP-server är:</span><span class="sxs-lookup"><span data-stu-id="1aada-888">The default MIME maps in NetX HTTP Server are:</span></span>

- <span data-ttu-id="1aada-889">HTML-text/html</span><span class="sxs-lookup"><span data-stu-id="1aada-889">html text/html</span></span>
- <span data-ttu-id="1aada-890">htm-text/html</span><span class="sxs-lookup"><span data-stu-id="1aada-890">htm text/html</span></span>
- <span data-ttu-id="1aada-891">txt-text/plain</span><span class="sxs-lookup"><span data-stu-id="1aada-891">txt text/plain</span></span>
- <span data-ttu-id="1aada-892">GIF-bild/gif</span><span class="sxs-lookup"><span data-stu-id="1aada-892">gif image/gif</span></span>
- <span data-ttu-id="1aada-893">jpg-bild/JPEG</span><span class="sxs-lookup"><span data-stu-id="1aada-893">jpg image/jpeg</span></span>
- <span data-ttu-id="1aada-894">ico-bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="1aada-894">ico image/x-icon</span></span>

<span data-ttu-id="1aada-895">Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar.</span><span class="sxs-lookup"><span data-stu-id="1aada-895">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="1aada-896">Se *nx_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.</span><span class="sxs-lookup"><span data-stu-id="1aada-896">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="1aada-897">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="1aada-897">This service is deprecated.</span></span> <span data-ttu-id="1aada-898">Utvecklare uppmanas att migrera till *nx_http_server_type_get_extended ().*</span><span class="sxs-lookup"><span data-stu-id="1aada-898">Developers are encouraged to migrate to *nx_http_server_type_get_extended().*</span></span>

<span data-ttu-id="1aada-899">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-899">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-900">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="1aada-900">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="1aada-901">**namn** Pekare för att söka</span><span class="sxs-lookup"><span data-stu-id="1aada-901">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="1aada-902">**http_type_string** (pekare till extraherad HTML-typ)</span><span class="sxs-lookup"><span data-stu-id="1aada-902">**http_type_string** (Pointer to extracted HTML type)</span></span>

<span data-ttu-id="1aada-903">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-903">**Return Values**</span></span>

- <span data-ttu-id="1aada-904">**Sträng längd i byte** Ett värde som inte är noll är klart</span><span class="sxs-lookup"><span data-stu-id="1aada-904">**Length of string in bytes** Non zero value is success</span></span>
- <span data-ttu-id="1aada-905">**Noll indikerar fel**</span><span class="sxs-lookup"><span data-stu-id="1aada-905">**Zero indicates error**</span></span>

<span data-ttu-id="1aada-906">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-906">**Allowed From**</span></span>

<span data-ttu-id="1aada-907">Program</span><span class="sxs-lookup"><span data-stu-id="1aada-907">Application</span></span>

<span data-ttu-id="1aada-908">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-908">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="1aada-909">Ett mer detaljerat exempel finns i beskrivningen av</span><span class="sxs-lookup"><span data-stu-id="1aada-909">For a more detailed example, see the description for</span></span>

<span data-ttu-id="1aada-910">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="1aada-910">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="1aada-911">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="1aada-911">nx_http_server_type_get_extended</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="1aada-912">Extrahera filtypen från klientens HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="1aada-912">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="1aada-913">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-913">**Prototype**</span></span>

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

<span data-ttu-id="1aada-914">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-914">**Description**</span></span>

<span data-ttu-id="1aada-915">Den här tjänsten extraherar typen av HTTP-begäran i bufferten *http_type_string* och dess längd i returvärdet från *indatabufferten, vanligt vis URL: en*.</span><span class="sxs-lookup"><span data-stu-id="1aada-915">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="1aada-916">Om det inte går att hitta någon MIME-mappning används standard typen text/plain.</span><span class="sxs-lookup"><span data-stu-id="1aada-916">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="1aada-917">Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning.</span><span class="sxs-lookup"><span data-stu-id="1aada-917">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="1aada-918">Standard-MIME-mappningarna i NetX Duo HTTP-server är:</span><span class="sxs-lookup"><span data-stu-id="1aada-918">The default MIME maps in NetX Duo HTTP Server are:</span></span>

- <span data-ttu-id="1aada-919">HTML-text/html</span><span class="sxs-lookup"><span data-stu-id="1aada-919">html text/html</span></span>
- <span data-ttu-id="1aada-920">htm-text/html</span><span class="sxs-lookup"><span data-stu-id="1aada-920">htm text/html</span></span>
- <span data-ttu-id="1aada-921">txt-text/plain</span><span class="sxs-lookup"><span data-stu-id="1aada-921">txt text/plain</span></span>
- <span data-ttu-id="1aada-922">GIF-bild/gif</span><span class="sxs-lookup"><span data-stu-id="1aada-922">gif image/gif</span></span>
- <span data-ttu-id="1aada-923">jpg-bild/JPEG</span><span class="sxs-lookup"><span data-stu-id="1aada-923">jpg image/jpeg</span></span>
- <span data-ttu-id="1aada-924">ico-bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="1aada-924">ico image/x-icon</span></span>

<span data-ttu-id="1aada-925">Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar.</span><span class="sxs-lookup"><span data-stu-id="1aada-925">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="1aada-926">Se *nx_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.</span><span class="sxs-lookup"><span data-stu-id="1aada-926">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="1aada-927">Den här tjänsten ersätter *nx_http_server_type_get ().*</span><span class="sxs-lookup"><span data-stu-id="1aada-927">This service replaces *nx_http_server_type_get().*</span></span> <span data-ttu-id="1aada-928">Den här versionen tillhandahåller ytterligare längd information.</span><span class="sxs-lookup"><span data-stu-id="1aada-928">This version supplies additional length information.</span></span>

<span data-ttu-id="1aada-929">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-929">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-930">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="1aada-930">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="1aada-931">**namn** Pekare för att söka</span><span class="sxs-lookup"><span data-stu-id="1aada-931">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="1aada-932">**name_length** Längd på buffert att söka i</span><span class="sxs-lookup"><span data-stu-id="1aada-932">**name_length** Length of buffer to search</span></span>
- <span data-ttu-id="1aada-933">**http_type_string** (pekare till extraherad HTML-typ)</span><span class="sxs-lookup"><span data-stu-id="1aada-933">**http_type_string** (Pointer to extracted HTML type)</span></span>
- <span data-ttu-id="1aada-934">**http_type_string_max_size**</span><span class="sxs-lookup"><span data-stu-id="1aada-934">**http_type_string_max_size**</span></span>

<span data-ttu-id="1aada-935">Storlek på *http_type_string* -bufferten</span><span class="sxs-lookup"><span data-stu-id="1aada-935">Size of the *http_type_string* buffer</span></span>

<span data-ttu-id="1aada-936">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-936">**Return Values**</span></span>

- <span data-ttu-id="1aada-937">**Sträng längd i byte** Ett värde som inte är noll är klart</span><span class="sxs-lookup"><span data-stu-id="1aada-937">**Length of string in bytes** Non zero value is success</span></span><br /><span data-ttu-id="1aada-938">Noll indikerar fel</span><span class="sxs-lookup"><span data-stu-id="1aada-938">Zero indicates error</span></span>

<span data-ttu-id="1aada-939">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-939">**Allowed From**</span></span>

<span data-ttu-id="1aada-940">Program</span><span class="sxs-lookup"><span data-stu-id="1aada-940">Application</span></span>

<span data-ttu-id="1aada-941">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-941">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

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
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="1aada-942">Ett mer detaljerat exempel finns i beskrivningen av</span><span class="sxs-lookup"><span data-stu-id="1aada-942">For a more detailed example, see the description for</span></span>

<span data-ttu-id="1aada-943">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="1aada-943">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="1aada-944">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="1aada-944">nx_http_server_digest_authenticate_notify_set</span></span>

### <a name="set-digest-authenticate-callback-function"></a><span data-ttu-id="1aada-945">Ange funktionen Digest-autentisering</span><span class="sxs-lookup"><span data-stu-id="1aada-945">Set digest authenticate callback function</span></span>

<span data-ttu-id="1aada-946">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-946">**Prototype**</span></span>

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

<span data-ttu-id="1aada-947">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-947">**Description**</span></span>

<span data-ttu-id="1aada-948">Den här tjänsten anger återanropet som anropas när Digest-autentisering utförs.</span><span class="sxs-lookup"><span data-stu-id="1aada-948">This service sets the callback invoked when digest authenticate is performed.</span></span>

<span data-ttu-id="1aada-949">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-949">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-950">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="1aada-950">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="1aada-951">**digest_authenticate_callback** Pekare till sammanfattad autentisering av motringning</span><span class="sxs-lookup"><span data-stu-id="1aada-951">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

<span data-ttu-id="1aada-952">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-952">**Return Values**</span></span>

- <span data-ttu-id="1aada-953">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="1aada-953">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="1aada-954">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-954">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="1aada-955">NX_NOT_SUPPORTED (0x4B) Digest-autentisering är inte aktiverat</span><span class="sxs-lookup"><span data-stu-id="1aada-955">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

<span data-ttu-id="1aada-956">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-956">**Allowed From**</span></span>

<span data-ttu-id="1aada-957">Program</span><span class="sxs-lookup"><span data-stu-id="1aada-957">Application</span></span>

<span data-ttu-id="1aada-958">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-958">**Example**</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="1aada-959">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="1aada-959">nx_http_server_authentication_check_set</span></span>

### <a name="set-authentication-checking-callback-function"></a><span data-ttu-id="1aada-960">Ange återanrops funktion för autentisering</span><span class="sxs-lookup"><span data-stu-id="1aada-960">Set authentication checking callback function</span></span>

<span data-ttu-id="1aada-961">**Prototyp**</span><span class="sxs-lookup"><span data-stu-id="1aada-961">**Prototype**</span></span>

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

<span data-ttu-id="1aada-962">**Beskrivning**</span><span class="sxs-lookup"><span data-stu-id="1aada-962">**Description**</span></span>

<span data-ttu-id="1aada-963">Den här tjänsten anger återanrops funktionen för autentisering.</span><span class="sxs-lookup"><span data-stu-id="1aada-963">This service sets the callback function of authentication checking.</span></span>

<span data-ttu-id="1aada-964">**Indataparametrar**</span><span class="sxs-lookup"><span data-stu-id="1aada-964">**Input Parameters**</span></span>

- <span data-ttu-id="1aada-965">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="1aada-965">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="1aada-966">**authentication_check_extended** Pekare till programmets verifierings kontroll</span><span class="sxs-lookup"><span data-stu-id="1aada-966">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

<span data-ttu-id="1aada-967">**Retur värden**</span><span class="sxs-lookup"><span data-stu-id="1aada-967">**Return Values**</span></span>

- <span data-ttu-id="1aada-968">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="1aada-968">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="1aada-969">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="1aada-969">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="1aada-970">**Tillåten från**</span><span class="sxs-lookup"><span data-stu-id="1aada-970">**Allowed From**</span></span>

<span data-ttu-id="1aada-971">Program</span><span class="sxs-lookup"><span data-stu-id="1aada-971">Application</span></span>

<span data-ttu-id="1aada-972">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="1aada-972">**Example**</span></span>

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```