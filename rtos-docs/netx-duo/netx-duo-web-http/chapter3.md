---
title: Kapitel 3 – Beskrivning av HTTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Web HTTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bb2743f05c5b56331d1c0e948601ad23bf340d1
ms.sourcegitcommit: 95f4ae0842a486fec8f10d1480203695faa9592d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2021
ms.locfileid: "111875280"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="13f01-103">Kapitel 3 – Beskrivning av HTTP-tjänster</span><span class="sxs-lookup"><span data-stu-id="13f01-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="13f01-104">Det här kapitlet innehåller en beskrivning av alla NetX Web HTTP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="13f01-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-105">I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="13f01-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="13f01-106">HTTP- och HTTPS-klient-API</span><span class="sxs-lookup"><span data-stu-id="13f01-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="13f01-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="13f01-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="13f01-108">Öppna en socket i klartext till en HTTP-server för anpassade begäranden</span><span class="sxs-lookup"><span data-stu-id="13f01-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-109">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-110">Description</span></span>

<span data-ttu-id="13f01-111">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-112">Den här tjänsten öppnar en TCP-socket i klartext till en HTTP-server men skickar inga begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="13f01-113">Begäranden skapas med n *x_web_http_client_request_initialize() och* skickas med *hjälp av nx_web_http_client_request_send().*</span><span class="sxs-lookup"><span data-stu-id="13f01-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="13f01-114">Anpassade HTTP-huvuden kan läggas till i begäran med *hjälp av nx_web_http_client_request_header_add()*.</span><span class="sxs-lookup"><span data-stu-id="13f01-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="13f01-115">Användning av den här tjänsten gör det möjligt för ett program att lägga till val annat antal anpassade huvuden i begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="13f01-116">**Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.**</span><span class="sxs-lookup"><span data-stu-id="13f01-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-117">Metoderna nx_web_http_client_\*_start tillhandahålls för enkelhetens skull (t.ex. *nx_web_http_client_get_start*()) och hanterar genereringen av förfrågningar och socketanslutningen.</span><span class="sxs-lookup"><span data-stu-id="13f01-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="13f01-118">Du kan använda dessa tjänster *i stället för nx_web_http_client_connect()* och relaterade rutiner om du inte behöver anpassade HTTP-huvuden i dina begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-119">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-119">Input Parameters</span></span>

- <span data-ttu-id="13f01-120">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-121">**server_ip** IP-adress för fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="13f01-122">**server_port** Port på http-fjärrserver (t.ex. 80 för HTTP).</span><span class="sxs-lookup"><span data-stu-id="13f01-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="13f01-123">**wait_option** Definierar hur länge tjänsten ska vänta på underliggande nätverksåtgärder.</span><span class="sxs-lookup"><span data-stu-id="13f01-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="13f01-124">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-125">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-127">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-127">Return Values</span></span>

- <span data-ttu-id="13f01-128">**NX_SUCCESS** (0x00) Lyckad anslutning av TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="13f01-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="13f01-129">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-130">NX_WEB_HTTP_NOT_READY (0x3000A) En annan begäran pågår redan.</span><span class="sxs-lookup"><span data-stu-id="13f01-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-131">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-131">Allowed From</span></span>

<span data-ttu-id="13f01-132">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-133">Example</span></span>

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="13f01-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="13f01-134">nx_web_http_client_create</span></span>

<span data-ttu-id="13f01-135">Skapa en HTTP-klientinstans</span><span class="sxs-lookup"><span data-stu-id="13f01-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-136">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="13f01-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-137">Description</span></span>

<span data-ttu-id="13f01-138">Den här tjänsten skapar en HTTP-klientinstans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="13f01-139">Klientinstansen kan användas för HTTP eller HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="13f01-140">Se tjänsterna *nx_web_http_client_connect() och* *nx_web_http_client_secure_connect()* för mer information om hur du startar en HTTP- eller HTTPS-instans.</span><span class="sxs-lookup"><span data-stu-id="13f01-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="13f01-141">Se även API:et för \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** för enkla anrop av GET-, PUT- och POST-metoder.</span><span class="sxs-lookup"><span data-stu-id="13f01-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-142">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-142">Input Parameters</span></span>

- <span data-ttu-id="13f01-143">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-144">**client_name** Namnet på HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="13f01-145">**ip_ptr** Pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="13f01-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="13f01-146">**pool_ptr** Pekare till standardpaketpoolen.</span><span class="sxs-lookup"><span data-stu-id="13f01-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="13f01-147">Observera att paketen i den här poolen måste ha en nyttolast som är tillräckligt stor för att hantera hela svarshuvudet.</span><span class="sxs-lookup"><span data-stu-id="13f01-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="13f01-148">Detta definieras av *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* i *nx_web_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="13f01-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="13f01-149">**window_size** Storleken på klientens TCP-socket-mottagningsfönster.</span><span class="sxs-lookup"><span data-stu-id="13f01-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-150">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-150">Return Values</span></span>

- <span data-ttu-id="13f01-151">**NX_SUCCESS** (0x00) Lyckad HTTP-klient skapas</span><span class="sxs-lookup"><span data-stu-id="13f01-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="13f01-152">NX_PTR_ERROR (0x16) Ogiltig HTTP-, ip_ptr- eller paketpoolspekare</span><span class="sxs-lookup"><span data-stu-id="13f01-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="13f01-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Ogiltig nyttolaststorlek i paketpoolen</span><span class="sxs-lookup"><span data-stu-id="13f01-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-154">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-154">Allowed From</span></span>

<span data-ttu-id="13f01-155">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-156">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="13f01-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="13f01-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="13f01-158">Ta bort en HTTP-klientinstans</span><span class="sxs-lookup"><span data-stu-id="13f01-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-159">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-160">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-160">Description</span></span>

<span data-ttu-id="13f01-161">Den här tjänsten tar bort en http-klientinstans som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="13f01-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-162">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-162">Input Parameters</span></span>

- <span data-ttu-id="13f01-163">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-164">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-164">Return Values</span></span>

- <span data-ttu-id="13f01-165">**NX_SUCCESS** (0x00) Lyckad BORTTAGNING av HTTP-klient</span><span class="sxs-lookup"><span data-stu-id="13f01-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="13f01-166">NX_PTR_ERROR (0x16) Ogiltig HTTP-pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="13f01-167">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-168">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-168">Allowed From</span></span>

<span data-ttu-id="13f01-169">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-170">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="13f01-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="13f01-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="13f01-172">Starta en HTTP DELETE-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="13f01-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-174">Description</span></span>

<span data-ttu-id="13f01-175">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-176">Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-177">Om den här rutinen NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="13f01-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="13f01-178">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-179">Det här API:et är inaktuellt.</span><span class="sxs-lookup"><span data-stu-id="13f01-179">This API is deprecated.</span></span> <span data-ttu-id="13f01-180">Utvecklare uppmanas att använda *nx_web_http_client_delete_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="13f01-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-181">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-181">Input Parameters</span></span>

- <span data-ttu-id="13f01-182">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-183">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-184">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-185">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-186">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-187">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-188">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-189">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-190">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-191">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-192">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-193">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-195">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-195">Return Values</span></span>

- <span data-ttu-id="13f01-196">**NX_SUCCESS** (0x00) har skickat meddelandet HTTP-klientens DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="13f01-197">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-201">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-202">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-203">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-203">Allowed From</span></span>

<span data-ttu-id="13f01-204">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-205">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-205">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="13f01-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="13f01-207">Starta en HTTP DELETE-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="13f01-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-208">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-209">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-209">Description</span></span>

<span data-ttu-id="13f01-210">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-211">Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-212">Om den här rutinen NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="13f01-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="13f01-213">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-214">Strängarna för resursen, värden, användarnamnet och lösenordet måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-215">Den här tjänsten *ersätter nx_web_http_client_delete_start* ().</span><span class="sxs-lookup"><span data-stu-id="13f01-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="13f01-216">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-217">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-217">Input Parameters</span></span>

- <span data-ttu-id="13f01-218">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-219">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-220">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-221">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-222">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-223">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-224">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-225">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-226">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-227">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-228">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-229">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-230">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-231">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-232">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-233">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-235">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-235">Return Values</span></span>

- <span data-ttu-id="13f01-236">**NX_SUCCESS** (0x00) har skickat meddelandet HTTP-klientens DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="13f01-237">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-241">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-242">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-243">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-243">Allowed From</span></span>

<span data-ttu-id="13f01-244">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-245">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-245">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="13f01-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="13f01-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="13f01-247">Starta en krypterad HTTPS DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-248">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-249">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-249">Description</span></span>

<span data-ttu-id="13f01-250">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-251">Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-252">Om den här rutinen NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="13f01-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="13f01-253">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-254">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-254">This service is deprecated.</span></span> <span data-ttu-id="13f01-255">Utvecklare uppmanas att använda *nx_web_http_client_delete_secure_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-256">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-256">Input Parameters</span></span>

- <span data-ttu-id="13f01-257">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-258">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-259">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-260">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="13f01-261">resursen måste vara NULL-avslutad.</span><span class="sxs-lookup"><span data-stu-id="13f01-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="13f01-262">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-263">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-264">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-265">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-266">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-267">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-268">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-269">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-270">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-271">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-273">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-273">Return Values</span></span>

- <span data-ttu-id="13f01-274">**NX_SUCCESS** (0x00) har skickat meddelandet HTTP-klientens DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="13f01-275">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-279">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-280">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-281">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-281">Allowed From</span></span>

<span data-ttu-id="13f01-282">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-283">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-283">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="13f01-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="13f01-285">Starta en krypterad HTTPS DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-286">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-286">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-287">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-287">Description</span></span>

<span data-ttu-id="13f01-288">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-289">Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-290">Om den här rutinen NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="13f01-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="13f01-291">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-292">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-293">Den här tjänsten *ersätter nx_web_http_client_delete_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="13f01-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="13f01-294">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-295">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-295">Input Parameters</span></span>

- <span data-ttu-id="13f01-296">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-297">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-298">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-299">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="13f01-300">resursen måste vara NULL-avslutad.</span><span class="sxs-lookup"><span data-stu-id="13f01-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="13f01-301">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-302">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-303">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-304">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-305">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-306">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-307">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-308">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-309">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-310">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-311">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-312">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-313">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-314">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-316">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-316">Return Values</span></span>

- <span data-ttu-id="13f01-317">**NX_SUCCESS** (0x00) har skickat meddelandet HTTP-klientens DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="13f01-318">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-322">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-323">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="13f01-324">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-324">Allowed From</span></span>

<span data-ttu-id="13f01-325">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-326">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-326">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="13f01-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="13f01-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="13f01-328">Starta en HTTP GET-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="13f01-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-329">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-330">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-330">Description</span></span>

<span data-ttu-id="13f01-331">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-332">Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-333">Om den här rutinen NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="13f01-334">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-335">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-335">This service is deprecated.</span></span> <span data-ttu-id="13f01-336">Utvecklare uppmanas att använda *nx_web_http_client_get_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-337">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-337">Input Parameters</span></span>

- <span data-ttu-id="13f01-338">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-339">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-340">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-341">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-342">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-343">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-344">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-345">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-346">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-347">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-348">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-349">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-351">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-351">Return Values</span></span>

- <span data-ttu-id="13f01-352">**NX_SUCCESS** (0x00) Skickade HTTP-klientens GET-startmeddelande</span><span class="sxs-lookup"><span data-stu-id="13f01-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="13f01-353">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-357">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-358">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-359">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-359">Allowed From</span></span>

<span data-ttu-id="13f01-360">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-361">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-361">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="13f01-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="13f01-363">Starta en HTTP GET-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="13f01-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-364">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-365">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-365">Description</span></span>

<span data-ttu-id="13f01-366">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-367">Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-368">Om den här rutinen NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="13f01-369">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-370">Strängarna för resursen, värden, användarnamnet och lösenordet måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-371">Den här tjänsten *ersätter nx_web_http_client_get_start*().</span><span class="sxs-lookup"><span data-stu-id="13f01-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="13f01-372">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-373">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-373">Input Parameters</span></span>

- <span data-ttu-id="13f01-374">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-375">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-376">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-377">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-378">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-379">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-380">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-381">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-382">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-383">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-384">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-385">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-386">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-387">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-388">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-389">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-391">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-391">Return Values</span></span>

- <span data-ttu-id="13f01-392">**NX_SUCCESS** (0x00) Skickade HTTP-klientens GET-startmeddelande</span><span class="sxs-lookup"><span data-stu-id="13f01-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="13f01-393">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-397">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-398">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-399">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-399">Allowed From</span></span>

<span data-ttu-id="13f01-400">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-401">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-401">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="13f01-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="13f01-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="13f01-403">Starta en krypterad HTTPS GET-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-404">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-405">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-405">Description</span></span>

<span data-ttu-id="13f01-406">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-407">Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-408">Om den här rutinen NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="13f01-409">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-410">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-410">This service is deprecated.</span></span> <span data-ttu-id="13f01-411">Utvecklare uppmanas att använda *nx_web_http_client_get_secure_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-412">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-412">Input Parameters</span></span>

- <span data-ttu-id="13f01-413">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-414">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-415">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-416">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-417">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-418">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-419">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-420">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-421">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-422">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-423">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-424">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-425">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-426">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-428">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-428">Return Values</span></span>

- <span data-ttu-id="13f01-429">**NX_SUCCESS** (0x00) Skickade HTTP-klientens GET-startmeddelande</span><span class="sxs-lookup"><span data-stu-id="13f01-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="13f01-430">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-434">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-435">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-436">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-436">Allowed From</span></span>

<span data-ttu-id="13f01-437">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-438">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-438">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="13f01-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="13f01-440">Starta en krypterad HTTPS GET-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-441">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-441">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-442">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-442">Description</span></span>

<span data-ttu-id="13f01-443">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-444">Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-445">Om den här rutinen NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="13f01-446">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-447">Strängarna för resursen, värden, användarnamnet och lösenordet måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-448">Den här tjänsten *ersätter nx_web_http_client_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="13f01-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="13f01-449">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-450">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-450">Input Parameters</span></span>

- <span data-ttu-id="13f01-451">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-452">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-453">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-454">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-455">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-456">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-457">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-458">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-459">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-460">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-461">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-462">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-463">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-464">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-465">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-466">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-467">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-468">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-470">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-470">Return Values</span></span>

- <span data-ttu-id="13f01-471">**NX_SUCCESS** (0x00) Skickade HTTP-klientens GET-startmeddelande</span><span class="sxs-lookup"><span data-stu-id="13f01-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="13f01-472">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-476">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-477">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-478">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-478">Allowed From</span></span>

<span data-ttu-id="13f01-479">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-480">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-480">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="13f01-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="13f01-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="13f01-482">Starta en HTTP HEAD-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="13f01-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-483">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-484">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-484">Description</span></span>

<span data-ttu-id="13f01-485">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-486">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-487">Om den här rutinen NX_SUCCESS kan programmet sedan anropa *nx_web_http_client_response_body_get()* för att hämta svaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="13f01-488">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-489">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-489">This service is deprecated.</span></span> <span data-ttu-id="13f01-490">Utvecklare uppmanas att använda *nx_web_http_client_head_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="13f01-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-491">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-491">Input Parameters</span></span>

- <span data-ttu-id="13f01-492">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-493">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-494">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-495">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-496">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-497">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-498">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-499">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-500">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-501">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-502">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-503">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-505">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-505">Return Values</span></span>

- <span data-ttu-id="13f01-506">**NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="13f01-507">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-508">**HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-511">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-512">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-513">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-513">Allowed From</span></span>

<span data-ttu-id="13f01-514">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-515">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-515">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="13f01-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="13f01-517">Starta en HTTP HEAD-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="13f01-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-518">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-519">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-519">Description</span></span>

<span data-ttu-id="13f01-520">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-521">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-522">Om rutinen returnerar NX_SUCCESS kan programmet sedan anropa *nx_web_http_client_response_body_get()* för att hämta svaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="13f01-523">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-524">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-525">Den här tjänsten *ersätter nx_web_http_client_head_start*().</span><span class="sxs-lookup"><span data-stu-id="13f01-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="13f01-526">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-527">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-527">Input Parameters</span></span>

- <span data-ttu-id="13f01-528">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-529">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-530">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-531">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-532">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-533">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-534">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-535">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-536">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-537">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-538">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-539">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-540">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-541">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-542">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-543">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-545">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-545">Return Values</span></span>

- <span data-ttu-id="13f01-546">**NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="13f01-547">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-548">**HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-551">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-552">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-553">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-553">Allowed From</span></span>

<span data-ttu-id="13f01-554">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-555">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-555">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="13f01-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="13f01-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="13f01-557">Starta en krypterad HTTPS HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-558">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-559">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-559">Description</span></span>

<span data-ttu-id="13f01-560">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-561">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-562">Om rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar som motsvarar det begärda resursinnehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="13f01-563">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-564">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-564">This service is deprecated.</span></span> <span data-ttu-id="13f01-565">Utvecklare uppmanas att använda *nx_web_http_client_head_secure_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-566">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-566">Input Parameters</span></span>

- <span data-ttu-id="13f01-567">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-568">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-569">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-570">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-571">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-572">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-573">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-574">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-575">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-576">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-577">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-578">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-579">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-580">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-582">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-582">Return Values</span></span>

- <span data-ttu-id="13f01-583">**NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="13f01-584">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-585">**HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-588">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-589">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-590">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-590">Allowed From</span></span>

<span data-ttu-id="13f01-591">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-592">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-592">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="13f01-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="13f01-594">Starta en krypterad HTTPS HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-595">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-595">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-596">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-596">Description</span></span>

<span data-ttu-id="13f01-597">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-598">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="13f01-599">Om rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar som motsvarar det begärda resursinnehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="13f01-600">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="13f01-601">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-602">Den här tjänsten *ersätter nx_web_http_client_head_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="13f01-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="13f01-603">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-604">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-604">Input Parameters</span></span>

- <span data-ttu-id="13f01-605">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-606">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-607">**server_port** Port på fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-608">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-609">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-610">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-611">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-612">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-613">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-614">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-615">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-616">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-617">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-618">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-619">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-620">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-621">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-622">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-624">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-624">Return Values</span></span>

- <span data-ttu-id="13f01-625">**NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="13f01-626">**NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel</span><span class="sxs-lookup"><span data-stu-id="13f01-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="13f01-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="13f01-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="13f01-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="13f01-630">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-631">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-632">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-632">Allowed From</span></span>

<span data-ttu-id="13f01-633">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-634">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-634">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="13f01-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="13f01-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="13f01-636">Allokera ett HTTP(S)-paket</span><span class="sxs-lookup"><span data-stu-id="13f01-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-637">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-638">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-638">Description</span></span>

<span data-ttu-id="13f01-639">Den här tjänsten försöker allokera ett paket för klientens HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="13f01-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-640">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-640">Input Parameters</span></span>

- <span data-ttu-id="13f01-641">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-642">**packet_ptr** Pekare till allokerat paket.</span><span class="sxs-lookup"><span data-stu-id="13f01-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="13f01-643">**wait_option** Definierar väntetiden i tick om det inte finns några paket tillgängliga i paketpoolen.</span><span class="sxs-lookup"><span data-stu-id="13f01-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="13f01-644">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="13f01-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="13f01-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="13f01-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="13f01-647">**timeout i tick** (0x00000001 via 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="13f01-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-648">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-648">Return Values</span></span>

- <span data-ttu-id="13f01-649">**NX_SUCCESS** (0x00) Allokera ett lyckat paket</span><span class="sxs-lookup"><span data-stu-id="13f01-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="13f01-650">**NX_NO_PACKET** (0x01) Inget paket tillgängligt</span><span class="sxs-lookup"><span data-stu-id="13f01-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="13f01-651">**NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop *till tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="13f01-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="13f01-652">**NX_INVALID_PARAMETERS** (0x4D) Paketstorleken stöder inte protokoll.</span><span class="sxs-lookup"><span data-stu-id="13f01-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="13f01-653">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-654">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-655">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-655">Allowed From</span></span>

<span data-ttu-id="13f01-656">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-657">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="13f01-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="13f01-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="13f01-659">Starta en HTTP POST-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-660">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-661">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-661">Description</span></span>

<span data-ttu-id="13f01-662">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-663">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-664">Om den här rutinen lyckas ska programkoden göra efterföljande anrop *nx_web_http_client_put_packet* rutinen för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-665">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-666">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-666">This service is deprecated.</span></span> <span data-ttu-id="13f01-667">Utvecklare uppmanas att använda *nx_web_http_client_post_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-668">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-668">Input Parameters</span></span>

- <span data-ttu-id="13f01-669">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-670">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-671">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-672">**resurs** Pekare till URL-sträng som resursen ska skicka till servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="13f01-673">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-674">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-675">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-676">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-677">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-678">**total_bytes** Totalt antal byte av resurs som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-679">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-680">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-681">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-682">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-684">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-684">Return Values</span></span>

- <span data-ttu-id="13f01-685">**NX_SUCCESS** (0x00) Post-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="13f01-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-688">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-689">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-690">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-691">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-691">Allowed From</span></span>

<span data-ttu-id="13f01-692">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-693">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-693">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="13f01-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="13f01-695">Starta en HTTP POST-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-696">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-697">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-697">Description</span></span>

<span data-ttu-id="13f01-698">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-699">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-700">Om den här rutinen lyckas ska programkoden göra efterföljande anrop *nx_web_http_client_put_packet* rutinen för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-701">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-702">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-703">Den här tjänsten *ersätter nx_web_http_client_post_start* ().</span><span class="sxs-lookup"><span data-stu-id="13f01-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="13f01-704">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-705">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-705">Input Parameters</span></span>

- <span data-ttu-id="13f01-706">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-707">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-708">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-709">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-710">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-711">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-712">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-713">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-714">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-715">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-716">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-717">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-718">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-719">**total_bytes** Totalt antal byte av resurs som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-720">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-721">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-722">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-723">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-725">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-725">Return Values</span></span>

- <span data-ttu-id="13f01-726">**NX_SUCCESS** (0x00) Post-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="13f01-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-729">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-730">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-731">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-732">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-732">Allowed From</span></span>

<span data-ttu-id="13f01-733">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-734">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-734">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="13f01-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="13f01-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="13f01-736">Starta en krypterad HTTPS POST-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-737">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-737">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-738">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-738">Description</span></span>

<span data-ttu-id="13f01-739">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-740">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-741">Om den här rutinen lyckas ska programkoden göra efterföljande anrop *till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-742">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-743">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-743">This service is deprecated.</span></span> <span data-ttu-id="13f01-744">Utvecklare uppmanas att använda *nx_web_http_client_post_secure_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-745">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-745">Input Parameters</span></span>

- <span data-ttu-id="13f01-746">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-747">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-748">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-749">**resurs** Pekare till URL-sträng som resursen ska skicka till servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="13f01-750">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-751">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-752">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-753">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-754">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-755">**total_bytes** Totalt antal byte av resurs som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-756">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-757">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-758">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-759">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-760">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-761">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-763">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-763">Return Values</span></span>

- <span data-ttu-id="13f01-764">**NX_SUCCESS** (0x00) Post-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="13f01-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-767">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-768">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-769">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-770">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-770">Allowed From</span></span>

<span data-ttu-id="13f01-771">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-772">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-772">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="13f01-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="13f01-774">Starta en krypterad HTTPS POST-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-775">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-775">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-776">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-776">Description</span></span>

<span data-ttu-id="13f01-777">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-778">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-779">Om den här rutinen lyckas ska programkoden göra efterföljande anrop *till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-780">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-781">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-782">Den här tjänsten *ersätter nx_web_http_client_post_secure_start* ().</span><span class="sxs-lookup"><span data-stu-id="13f01-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="13f01-783">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-784">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-784">Input Parameters</span></span>

- <span data-ttu-id="13f01-785">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-786">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-787">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-788">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-789">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-790">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-791">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-792">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-793">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-794">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-795">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-796">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-797">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-798">**total_bytes** Totalt antal byte av resurs som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-799">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-800">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-801">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-802">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-803">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-804">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-806">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-806">Return Values</span></span>

- <span data-ttu-id="13f01-807">**NX_SUCCESS** (0x00) Post-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="13f01-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-809">**HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-810">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-811">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-812">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-813">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-813">Allowed From</span></span>

<span data-ttu-id="13f01-814">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-815">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-815">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="13f01-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="13f01-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="13f01-817">Starta en HTTP PUT-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-818">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-819">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-819">Description</span></span>

<span data-ttu-id="13f01-820">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-821">Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-822">Om den här rutinen lyckas bör programkoden göra efterföljande *anrop till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-823">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-824">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-824">This service is deprecated.</span></span> <span data-ttu-id="13f01-825">Utvecklare uppmanas att använda *nx_web_http_client_put_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-826">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-826">Input Parameters</span></span>

- <span data-ttu-id="13f01-827">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-828">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-829">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-830">**resurs** Pekare till URL-sträng som resursen ska skicka till servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="13f01-831">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-832">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-833">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-834">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-835">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-836">**total_bytes** Totalt antal byte för resursen som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-837">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-838">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-839">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-840">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-842">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-842">Return Values</span></span>

- <span data-ttu-id="13f01-843">**NX_SUCCESS** (0x00) Put-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="13f01-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-845">**HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-846">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-847">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-848">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-849">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-849">Allowed From</span></span>

<span data-ttu-id="13f01-850">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-851">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-851">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="13f01-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="13f01-853">Starta en HTTP PUT-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-854">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-855">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-855">Description</span></span>

<span data-ttu-id="13f01-856">Den här metoden är **för KLARTEXT** HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="13f01-857">Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-858">Om den här rutinen lyckas bör programkoden göra efterföljande *anrop till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-859">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-860">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-861">Den här tjänsten *ersätter nx_web_http_client_put_start* ().</span><span class="sxs-lookup"><span data-stu-id="13f01-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="13f01-862">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-863">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-863">Input Parameters</span></span>

- <span data-ttu-id="13f01-864">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-865">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-866">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-867">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-868">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-869">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-870">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-871">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-872">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-873">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-874">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-875">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-876">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-877">**total_bytes** Totalt antal byte för resursen som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-878">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-879">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-880">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-881">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-883">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-883">Return Values</span></span>

- <span data-ttu-id="13f01-884">**NX_SUCCESS** (0x00) Put-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="13f01-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-886">**HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-887">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-888">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-889">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-890">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-890">Allowed From</span></span>

<span data-ttu-id="13f01-891">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-892">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-892">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="13f01-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="13f01-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="13f01-894">Starta en krypterad HTTPS PUT-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-895">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-895">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-896">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-896">Description</span></span>

<span data-ttu-id="13f01-897">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-898">Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-899">Om den här rutinen lyckas bör programkoden göra efterföljande *anrop till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-900">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-901">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-901">This service is deprecated.</span></span> <span data-ttu-id="13f01-902">Utvecklare uppmanas att använda *nx_web_http_client_put_secure_start_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-903">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-903">Input Parameters</span></span>

- <span data-ttu-id="13f01-904">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-905">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-906">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-907">**resurs** Pekare till URL-sträng som resursen ska skicka till servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="13f01-908">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-909">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-910">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-911">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-912">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-913">**total_bytes** Totalt antal byte av resurs som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-914">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-915">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-916">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-917">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-918">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-919">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-921">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-921">Return Values</span></span>

- <span data-ttu-id="13f01-922">**NX_SUCCESS** (0x00) Put-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="13f01-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-925">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-926">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-927">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-928">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-928">Allowed From</span></span>

<span data-ttu-id="13f01-929">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-930">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-930">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="13f01-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="13f01-932">Starta en krypterad HTTPS PUT-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-933">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-933">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-934">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-934">Description</span></span>

<span data-ttu-id="13f01-935">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-936">Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="13f01-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="13f01-937">Om den här rutinen lyckas ska programkoden göra efterföljande anrop *till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="13f01-938">Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="13f01-939">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-940">Den här tjänsten *ersätter nx_web_http_client_put_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="13f01-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="13f01-941">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-942">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-942">Input Parameters</span></span>

- <span data-ttu-id="13f01-943">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-944">**ip_address** HTTP-serverns IP-adress.</span><span class="sxs-lookup"><span data-stu-id="13f01-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="13f01-945">**server_port** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="13f01-946">**resurs** Pekare till URL-sträng för begärd resurs.</span><span class="sxs-lookup"><span data-stu-id="13f01-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="13f01-947">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-948">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-949">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-950">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-951">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-952">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-953">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-954">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-955">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-956">**total_bytes** Totalt antal byte av resurs som skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="13f01-957">Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="13f01-958">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-959">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-960">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-961">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-962">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-964">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-964">Return Values</span></span>

- <span data-ttu-id="13f01-965">**NX_SUCCESS** (0x00) Put-begäran har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="13f01-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert</span><span class="sxs-lookup"><span data-stu-id="13f01-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="13f01-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-968">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-969">NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen</span><span class="sxs-lookup"><span data-stu-id="13f01-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="13f01-970">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-971">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-971">Allowed From</span></span>

<span data-ttu-id="13f01-972">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-973">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-973">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="13f01-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="13f01-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="13f01-975">Skicka nästa resursdatapaket</span><span class="sxs-lookup"><span data-stu-id="13f01-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-976">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-977">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-977">Description</span></span>

<span data-ttu-id="13f01-978">Den här tjänsten försöker skicka nästa paket med resursinnehåll till HTTP-servern för både PUT- och POST-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="13f01-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="13f01-979">Observera att den här rutinen bör anropas upprepade tills den kombinerade längden på de paket som skickas är lika med "total_bytes" som angavs i det tidigare *nx_web_http_client_put_start()* eller *nx_web_http_client_post_start()-anropet* (eller deras motsvarande säkra versioner).</span><span class="sxs-lookup"><span data-stu-id="13f01-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="13f01-980">Den här tjänsten söker också efter svar från servern om det uppstår problem med att upprätta HTTP-anslutningen (eller HTTPS).</span><span class="sxs-lookup"><span data-stu-id="13f01-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-981">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-981">Input Parameters</span></span>

- <span data-ttu-id="13f01-982">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-983">**packet_ptr** Pekare till nästa innehåll i resursen som skickas till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="13f01-984">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-985">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-986">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-988">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-988">Return Values</span></span>

- <span data-ttu-id="13f01-989">**NX_SUCCESS** (0x00) SKICKADE HTTP-klientpaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="13f01-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar</span><span class="sxs-lookup"><span data-stu-id="13f01-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="13f01-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Felkod för mottagen server\*\*</span><span class="sxs-lookup"><span data-stu-id="13f01-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="13f01-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Ogiltig paketlängd</span><span class="sxs-lookup"><span data-stu-id="13f01-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="13f01-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord</span><span class="sxs-lookup"><span data-stu-id="13f01-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="13f01-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Servern svarar innan PUT har slutförts</span><span class="sxs-lookup"><span data-stu-id="13f01-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="13f01-995">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-996">NX_INVALID_PACKET (0x12) Paket för litet för TCP-huvud</span><span class="sxs-lookup"><span data-stu-id="13f01-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="13f01-997">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-998">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-998">Allowed From</span></span>

<span data-ttu-id="13f01-999">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1000">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="13f01-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="13f01-1002">Ange segmenterad överföring för HTTP(S)-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1003">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-1004">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1004">Description</span></span>

<span data-ttu-id="13f01-1005">Den här tjänsten använder segmenterad överföringskodning för att skicka en anpassad HTTP(S)-begäran till den server som anges i *anropet nx_web_http_client_connect()* eller *nx_web_http_client_secure_connect()* som tidigare har upprättat socketanslutningen till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1006">Om programmet använder segmenterad överföringskodning för att skicka ett begärandedatapaket måste det anropa den här tjänsten efter *anropet nx_web_http_client_request_packet_allocate*() och *innan anropet nx_web_http_client_reqeust_packet_send* ().</span><span class="sxs-lookup"><span data-stu-id="13f01-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1007">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1007">Input Parameters</span></span>

- <span data-ttu-id="13f01-1008">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1009">**chunk_size** Storleken på segmentdata i oktett.</span><span class="sxs-lookup"><span data-stu-id="13f01-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="13f01-1010">**packet_ptr** Pekare för HTTP(S)-begärandedatapaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1011">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1011">Return Values</span></span>

- <span data-ttu-id="13f01-1012">**NX_SUCCESS** (0x00) Har angetts segmenterat.</span><span class="sxs-lookup"><span data-stu-id="13f01-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="13f01-1013">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1014">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1014">Allowed From</span></span>

<span data-ttu-id="13f01-1015">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1016">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="13f01-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="13f01-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="13f01-1018">Lägga till ett anpassat huvud i en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1019">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1020">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1020">Description</span></span>

<span data-ttu-id="13f01-1021">Den här tjänsten lägger till ett anpassat huvud (i form av ett fältnamn och värde) till en anpassad HTTP-begäran som skapats med n *x_web_http_client_request_initialize()*.</span><span class="sxs-lookup"><span data-stu-id="13f01-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="13f01-1022">Användning av den här tjänsten gör det möjligt för ett program att lägga till val annat antal anpassade huvuden i begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="13f01-1023">**Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.**</span><span class="sxs-lookup"><span data-stu-id="13f01-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1024">De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="13f01-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="13f01-1025">Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize()) för* att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1026">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1026">Input Parameters</span></span>

- <span data-ttu-id="13f01-1027">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1028">**field_name** Fältnamnssträng (t.ex. "Content-Type").</span><span class="sxs-lookup"><span data-stu-id="13f01-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="13f01-1029">**name_length** Längden på fältnamnssträngen i byte.</span><span class="sxs-lookup"><span data-stu-id="13f01-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="13f01-1030">**field_value** Fältvärdessträng (t.ex. "application/octet-stream").</span><span class="sxs-lookup"><span data-stu-id="13f01-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="13f01-1031">**value_length** Längden på värdesträngen i byte.</span><span class="sxs-lookup"><span data-stu-id="13f01-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="13f01-1032">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-1033">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1034">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1036">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1036">Return Values</span></span>

- <span data-ttu-id="13f01-1037">**NX_SUCCESS** (0x00) Lyckad tillägg av rubrik i begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="13f01-1038">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1039">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1039">Allowed From</span></span>

<span data-ttu-id="13f01-1040">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1041">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="13f01-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="13f01-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="13f01-1043">Initiera en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1044">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1045">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1045">Description</span></span>

<span data-ttu-id="13f01-1046">Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="13f01-1047">Till skillnad *från de enklare nx_web_http_client_get_start()* (tillsammans med metoderna för PUT, POST och de associerade säkra versionerna av dessa API) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send()* anropas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="13f01-1048">Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran med ***hjälp av nx_web_http_client_request_header_add()-tjänsten.***</span><span class="sxs-lookup"><span data-stu-id="13f01-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="13f01-1049">Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.</span><span class="sxs-lookup"><span data-stu-id="13f01-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1050">De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="13f01-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="13f01-1051">Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_send()) för* att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="13f01-1052">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-1052">This service is deprecated.</span></span> <span data-ttu-id="13f01-1053">Utvecklare uppmanas att använda *nx_web_http_client_request_initialize_extended()*.</span><span class="sxs-lookup"><span data-stu-id="13f01-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1054">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1054">Input Parameters</span></span>

- <span data-ttu-id="13f01-1055">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1056">**metod** Http-förfrågningsmetoden som ska användas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="13f01-1057">Alternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="13f01-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="13f01-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="13f01-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="13f01-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="13f01-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="13f01-1064">**resurs** Namnet på den resurs som överförs.</span><span class="sxs-lookup"><span data-stu-id="13f01-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="13f01-1065">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-1066">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-1067">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-1068">**input_size** Storlek på indata för PUT och POST.</span><span class="sxs-lookup"><span data-stu-id="13f01-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="13f01-1069">Skicka 0 för andra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="13f01-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="13f01-1070">**transfer_encoding_trunked** Reserverad parameter för stöd för framtida trunkerad överföring.</span><span class="sxs-lookup"><span data-stu-id="13f01-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="13f01-1071">**användarnamn** Användarnamn för skyddade resurser.</span><span class="sxs-lookup"><span data-stu-id="13f01-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="13f01-1072">**lösenord** Lösenord för skyddade resurser.</span><span class="sxs-lookup"><span data-stu-id="13f01-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="13f01-1073">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-1074">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1075">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1077">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1077">Return Values</span></span>

- <span data-ttu-id="13f01-1078">**NX_SUCCESS** (0x00) Lyckad initiering av begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="13f01-1079">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Viss nödvändig information saknades (t.ex. input_size put eller POST).</span><span class="sxs-lookup"><span data-stu-id="13f01-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1081">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1081">Allowed From</span></span>

<span data-ttu-id="13f01-1082">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1083">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1083">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="13f01-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="13f01-1085">Initiera en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1086">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1087">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1087">Description</span></span>

<span data-ttu-id="13f01-1088">Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klientinstansen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="13f01-1089">Till skillnad *från de enklare nx_web_http_client_get_start()* (tillsammans med metoderna för PUT, POST och de associerade säkra versionerna av dessa API) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send()* anropas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="13f01-1090">Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran med ***hjälp av nx_web_http_client_request_header_add()-tjänsten.***</span><span class="sxs-lookup"><span data-stu-id="13f01-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="13f01-1091">Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.</span><span class="sxs-lookup"><span data-stu-id="13f01-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1092">De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="13f01-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="13f01-1093">Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_send()) för* att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="13f01-1094">Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-1095">Den här tjänsten *ersätter nx_web_http_client_request_initialize*().</span><span class="sxs-lookup"><span data-stu-id="13f01-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="13f01-1096">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1097">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1097">Input Parameters</span></span>

- <span data-ttu-id="13f01-1098">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1099">**metod** Http-förfrågningsmetoden som ska användas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="13f01-1100">Alternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="13f01-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="13f01-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="13f01-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="13f01-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="13f01-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="13f01-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="13f01-1107">**resurs** Namnet på den resurs som överförs.</span><span class="sxs-lookup"><span data-stu-id="13f01-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="13f01-1108">**resource_length** Stränglängd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="13f01-1109">**värd** Null-avslutad sträng för serverns domännamn.</span><span class="sxs-lookup"><span data-stu-id="13f01-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="13f01-1110">Den här strängen överförs i fältet HTTP-värdrubrik.</span><span class="sxs-lookup"><span data-stu-id="13f01-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="13f01-1111">Värdsträngen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="13f01-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="13f01-1112">**host_length** Stränglängd för värden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="13f01-1113">**input_size** Storleken på indata för PUT och POST.</span><span class="sxs-lookup"><span data-stu-id="13f01-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="13f01-1114">Skicka 0 för andra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="13f01-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="13f01-1115">**transfer_encoding_trunked** Reserverad parameter för stöd för framtida trunkerad överföring.</span><span class="sxs-lookup"><span data-stu-id="13f01-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="13f01-1116">**användarnamn** Pekare till valfritt användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="13f01-1117">**username_length** Stränglängd för användarnamn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="13f01-1118">**lösenord** Pekare till valfritt lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="13f01-1119">**password_length** Stränglängd för lösenord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="13f01-1120">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-1121">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1122">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1124">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1124">Return Values</span></span>

- <span data-ttu-id="13f01-1125">**NX_SUCCESS** (0x00) Lyckad initiering av begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="13f01-1126">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Viss nödvändig information saknades (t.ex. input_size put eller POST).</span><span class="sxs-lookup"><span data-stu-id="13f01-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1128">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1128">Allowed From</span></span>

<span data-ttu-id="13f01-1129">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1130">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1130">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="13f01-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="13f01-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="13f01-1132">Skicka HTTP(S)-begärandedatapaket till fjärrservern</span><span class="sxs-lookup"><span data-stu-id="13f01-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1133">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1134">Description</span></span>

<span data-ttu-id="13f01-1135">Den här tjänsten skickar ett anpassat HTTP(S)-begärandedatapaket som skapats med *nx_web_http_client_request_packet_allocate* () till den server som anges i *anropet nx_web_http_client_connect()* eller *nx_web_http_client_secure_connect(*) som tidigare har upprättat socketanslutningen till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1136">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1136">Input Parameters</span></span>

- <span data-ttu-id="13f01-1137">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1138">**packet_ptr** Pekare för HTTP(S)-begärandedatapaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="13f01-1139">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-1140">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1141">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1143">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1143">Return Values</span></span>

- <span data-ttu-id="13f01-1144">**NX_SUCCESS** (0x00) Skicka datapaket med begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="13f01-1145">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1146">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1146">Allowed From</span></span>

<span data-ttu-id="13f01-1147">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1148">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="13f01-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="13f01-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="13f01-1150">Skicka en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1152">Description</span></span>

<span data-ttu-id="13f01-1153">Den här tjänsten skickar en anpassad HTTP-begäran som skapats med *nx_web_http_client_request_initialize()* till den server som anges i *nx_web_http_client_connect()* eller *nx_web_http_client_secure_connect()* som båda tidigare har upprättat socketanslutningen till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="13f01-1154">Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran med ***hjälp av nx_web_http_client_request_header_add()-tjänsten.***</span><span class="sxs-lookup"><span data-stu-id="13f01-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="13f01-1155">Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.</span><span class="sxs-lookup"><span data-stu-id="13f01-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1156">De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="13f01-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="13f01-1157">Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize()) för* att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1158">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1158">Input Parameters</span></span>

- <span data-ttu-id="13f01-1159">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1160">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-1161">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1162">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1164">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1164">Return Values</span></span>

- <span data-ttu-id="13f01-1165">**NX_SUCCESS** (0x00) Lyckades skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="13f01-1166">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1167">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1167">Allowed From</span></span>

<span data-ttu-id="13f01-1168">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1169">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="13f01-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="13f01-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="13f01-1171">Hämta nästa resursdatapaket</span><span class="sxs-lookup"><span data-stu-id="13f01-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1172">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1173">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1173">Description</span></span>

<span data-ttu-id="13f01-1174">Den här tjänsten hämtar nästa paket med innehåll i resursen som begärdes av det *tidigare nx_web_http_client_get_start() eller* *nx_web_http_client_get_secure_start()-anropet.*</span><span class="sxs-lookup"><span data-stu-id="13f01-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="13f01-1175">Efterföljande anrop till den här rutinen ska göras tills returstatusen för NX_WEB_HTTP_GET_DONE tas emot.</span><span class="sxs-lookup"><span data-stu-id="13f01-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1176">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1176">Input Parameters</span></span>

- <span data-ttu-id="13f01-1177">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1178">**packet_ptr** Mål för paket pekare som innehåller partiellt resursinnehåll.</span><span class="sxs-lookup"><span data-stu-id="13f01-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="13f01-1179">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-1180">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1181">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1183">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1183">Return Values</span></span>

- <span data-ttu-id="13f01-1184">**NX_SUCCESS** (0x00) Lyckad get av HTTP-klientpaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="13f01-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP-klienten hämta paket är klar</span><span class="sxs-lookup"><span data-stu-id="13f01-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="13f01-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten är inte i get-läge.</span><span class="sxs-lookup"><span data-stu-id="13f01-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="13f01-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Ogiltig paketlängd</span><span class="sxs-lookup"><span data-stu-id="13f01-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="13f01-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP-statuskod 100 Fortsätt</span><span class="sxs-lookup"><span data-stu-id="13f01-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="13f01-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP-statuskod 101 Växla protokoll</span><span class="sxs-lookup"><span data-stu-id="13f01-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="13f01-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP-statuskod 201 Skapad</span><span class="sxs-lookup"><span data-stu-id="13f01-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="13f01-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP-statuskod 202 Accepterad</span><span class="sxs-lookup"><span data-stu-id="13f01-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="13f01-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP-statuskod 203 – icke-auktoritativ information</span><span class="sxs-lookup"><span data-stu-id="13f01-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="13f01-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP-statuskod 204 Inget innehåll</span><span class="sxs-lookup"><span data-stu-id="13f01-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="13f01-1194">**HTTP-statuskod** NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT (0x30020) 205 Reset Content</span><span class="sxs-lookup"><span data-stu-id="13f01-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="13f01-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP-statuskod 206 Partiellt innehåll</span><span class="sxs-lookup"><span data-stu-id="13f01-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="13f01-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP-statuskod 300 Flera alternativ</span><span class="sxs-lookup"><span data-stu-id="13f01-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="13f01-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP-statuskod 301 Flyttad permanent</span><span class="sxs-lookup"><span data-stu-id="13f01-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="13f01-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP-statuskod 302 hittades</span><span class="sxs-lookup"><span data-stu-id="13f01-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="13f01-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP-statuskod 303 Se övrigt</span><span class="sxs-lookup"><span data-stu-id="13f01-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="13f01-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP-statuskod 304 Har inte ändrats</span><span class="sxs-lookup"><span data-stu-id="13f01-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="13f01-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP-statuskod 305 Använd proxy</span><span class="sxs-lookup"><span data-stu-id="13f01-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="13f01-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP-statuskod 307 tillfällig omdirigering</span><span class="sxs-lookup"><span data-stu-id="13f01-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="13f01-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP-statuskod 400 Felaktig begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="13f01-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP-statuskod 401 – Obehörig</span><span class="sxs-lookup"><span data-stu-id="13f01-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="13f01-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP-statuskod 402 Betalning krävs</span><span class="sxs-lookup"><span data-stu-id="13f01-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="13f01-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP-statuskod 403 Förbjuden</span><span class="sxs-lookup"><span data-stu-id="13f01-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="13f01-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP-statuskod 404 Hittades inte</span><span class="sxs-lookup"><span data-stu-id="13f01-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="13f01-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP-statuskod 405 Metoden tillåts inte</span><span class="sxs-lookup"><span data-stu-id="13f01-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="13f01-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP-statuskod 406 Inte acceptabel</span><span class="sxs-lookup"><span data-stu-id="13f01-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="13f01-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP-statuskod 407 Proxyautentisering krävs</span><span class="sxs-lookup"><span data-stu-id="13f01-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="13f01-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP-statuskod 408 Time-out för begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="13f01-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP-statuskod 409 Konflikt</span><span class="sxs-lookup"><span data-stu-id="13f01-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="13f01-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP-statuskod 410 Borta</span><span class="sxs-lookup"><span data-stu-id="13f01-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="13f01-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP-statuskod 411 Längd krävs</span><span class="sxs-lookup"><span data-stu-id="13f01-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="13f01-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP-statuskod 412 Förhandsvillkoret misslyckades</span><span class="sxs-lookup"><span data-stu-id="13f01-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="13f01-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP-statuskod 413 Begärandeentiteten är för stor</span><span class="sxs-lookup"><span data-stu-id="13f01-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="13f01-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP-statuskod 414 Begärande-URL är för stor</span><span class="sxs-lookup"><span data-stu-id="13f01-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="13f01-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP-statuskod 415 Medietyp som inte stöds</span><span class="sxs-lookup"><span data-stu-id="13f01-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="13f01-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP-statuskod 416 Det begärda intervallet är inte tillåtna</span><span class="sxs-lookup"><span data-stu-id="13f01-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="13f01-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP-statuskod 417 Förväntan misslyckades</span><span class="sxs-lookup"><span data-stu-id="13f01-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="13f01-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP-statuskod 500 Internt serverfel</span><span class="sxs-lookup"><span data-stu-id="13f01-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="13f01-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP-statuskod 501 Inte implementerad</span><span class="sxs-lookup"><span data-stu-id="13f01-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="13f01-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP-statuskod 502 Felaktig gateway</span><span class="sxs-lookup"><span data-stu-id="13f01-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="13f01-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP-statuskod 503 Tjänsten är inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="13f01-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="13f01-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP-statuskod 504 Gateway Time-out</span><span class="sxs-lookup"><span data-stu-id="13f01-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="13f01-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP-statuskod 505 HTTP-version stöds inte</span><span class="sxs-lookup"><span data-stu-id="13f01-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="13f01-1227">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1228">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1229">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1229">Allowed From</span></span>

<span data-ttu-id="13f01-1230">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1231">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="13f01-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="13f01-1233">Ställ in motringning för att anropa vid bearbetning av HTTP-huvuden</span><span class="sxs-lookup"><span data-stu-id="13f01-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1234">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="13f01-1235">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1235">Description</span></span>

<span data-ttu-id="13f01-1236">Den här tjänsten tilldelar ett återanrop som anropas när NetX Web HTTP Client bearbetar ett HTTP-huvud i ett inkommande svar från en fjärransluten HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="13f01-1237">Motringning anropas en gång för varje huvud i svaret när det bearbetas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="13f01-1238">Motringning gör att ett HTTP-klientprogram kan komma åt vart och ett av huvudena i HTTP-serversvaret för att vidta önskade åtgärder utöver den grundläggande bearbetning som NetX Web HTTP-klienten gör.</span><span class="sxs-lookup"><span data-stu-id="13f01-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1239">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1239">Input Parameters</span></span>

<span data-ttu-id="13f01-1240">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="13f01-1241">**callback_function** Återanrop anropas vid bearbetning av svarshuvud.</span><span class="sxs-lookup"><span data-stu-id="13f01-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="13f01-1242">Motringning anropas med fältnamnet och värdet som strängar (och deras längd).</span><span class="sxs-lookup"><span data-stu-id="13f01-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="13f01-1243">Till exempel skulle rubriken "Content-Length: 100" göra så att funktionen anropas med "Content-Length" för *field_name* och strängen "100" *för field_value*.</span><span class="sxs-lookup"><span data-stu-id="13f01-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1244">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1244">Return Values</span></span>

- <span data-ttu-id="13f01-1245">**NX_SUCCESS** (0x00) Lyckad tilldelning av återanrop.</span><span class="sxs-lookup"><span data-stu-id="13f01-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="13f01-1246">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1247">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1247">Allowed From</span></span>

<span data-ttu-id="13f01-1248">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1249">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1249">Example</span></span>

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="13f01-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="13f01-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="13f01-1251">Öppna en TLS-session till en HTTPS-server för anpassade begäranden</span><span class="sxs-lookup"><span data-stu-id="13f01-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1252">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1253">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1253">Description</span></span>

<span data-ttu-id="13f01-1254">Den här metoden är för **TLS-skyddad** HTTPS.</span><span class="sxs-lookup"><span data-stu-id="13f01-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="13f01-1255">Den här tjänsten öppnar en skyddad TLS-session till en HTTPS-server men skickar inga begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="13f01-1256">Begäranden skapas med n *x_web_http_client_request_initialize() och* skickas med *hjälp av nx_web_http_client_request_send().*</span><span class="sxs-lookup"><span data-stu-id="13f01-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="13f01-1257">Anpassade HTTP-huvuden kan läggas till i begäran med *hjälp av nx_web_http_client_request_header_add()*.</span><span class="sxs-lookup"><span data-stu-id="13f01-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="13f01-1258">Användning av den här tjänsten gör det möjligt för ett program att lägga till val annat antal anpassade huvuden i begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="13f01-1259">**Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.**</span><span class="sxs-lookup"><span data-stu-id="13f01-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1260">De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="13f01-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="13f01-1261">Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize()) för* att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1262">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1262">Input Parameters</span></span>

- <span data-ttu-id="13f01-1263">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1264">**server_ip** IP-adress för https-fjärrserver.</span><span class="sxs-lookup"><span data-stu-id="13f01-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="13f01-1265">**server_port** Port på https-fjärrserver (t.ex. 443 för HTTPS).</span><span class="sxs-lookup"><span data-stu-id="13f01-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="13f01-1266">**tls_setup** Återanrop som används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13f01-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="13f01-1267">Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="13f01-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="13f01-1268">**wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="13f01-1269">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1270">**timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.</span><span class="sxs-lookup"><span data-stu-id="13f01-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="13f01-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1272">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1272">Return Values</span></span>

- <span data-ttu-id="13f01-1273">**NX_SUCCESS** (0x00) Lyckad anslutning av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="13f01-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="13f01-1274">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1275">NX_WEB_HTTP_NOT_READY (0x3000A) En annan begäran pågår redan.</span><span class="sxs-lookup"><span data-stu-id="13f01-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1276">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1276">Allowed From</span></span>

<span data-ttu-id="13f01-1277">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1278">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1278">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="13f01-1279">HTTP och HTTPS Server API</span><span class="sxs-lookup"><span data-stu-id="13f01-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="13f01-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="13f01-1281">Ange återanrop för att hämta URL:ens maximala ålder och datum</span><span class="sxs-lookup"><span data-stu-id="13f01-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1282">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="13f01-1283">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1283">Description</span></span>

<span data-ttu-id="13f01-1284">Den här tjänsten anger återanropstjänsten som anropas för att hämta den angivna resursens högsta ålder och senaste ändringsdatum.</span><span class="sxs-lookup"><span data-stu-id="13f01-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1285">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1285">Input Parameters</span></span>

- <span data-ttu-id="13f01-1286">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1287">**cache_info_get** Pekare till motringning</span><span class="sxs-lookup"><span data-stu-id="13f01-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="13f01-1288">**max_age** Pekare till högsta ålder för en resurs</span><span class="sxs-lookup"><span data-stu-id="13f01-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="13f01-1289">**data** Pekare till senaste ändringsdatum som returnerades.</span><span class="sxs-lookup"><span data-stu-id="13f01-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1290">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1290">Return Values</span></span>

- <span data-ttu-id="13f01-1291">**NX_SUCCESS** (0x00) Har ställt in återanropet</span><span class="sxs-lookup"><span data-stu-id="13f01-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="13f01-1292">**NX_PTR_ERROR** (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1293">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1293">Allowed From</span></span>

<span data-ttu-id="13f01-1294">Initiering</span><span class="sxs-lookup"><span data-stu-id="13f01-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1295">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="13f01-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="13f01-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="13f01-1297">Funktionen Skicka data från motringning</span><span class="sxs-lookup"><span data-stu-id="13f01-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1298">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="13f01-1299">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1299">Description</span></span>

<span data-ttu-id="13f01-1300">Den här tjänsten skickar data i det angivna paketet från programmets återanropsrutin.</span><span class="sxs-lookup"><span data-stu-id="13f01-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="13f01-1301">Detta används vanligtvis för att skicka dynamiska data som är associerade med GET/POST-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="13f01-1302">Observera att om den här funktionen används ansvarar motringningrutinen för att skicka hela svaret i rätt format.</span><span class="sxs-lookup"><span data-stu-id="13f01-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="13f01-1303">Dessutom måste motringning rutinen returnera statusen för NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="13f01-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1304">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1304">Input Parameters</span></span>

- <span data-ttu-id="13f01-1305">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1306">**data_ptr** Pekare till de data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="13f01-1307">**data_length** Antal byte som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1308">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1308">Return Values</span></span>

- <span data-ttu-id="13f01-1309">**NX_SUCCESS** (0x00) Serverdata har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="13f01-1310">**NX_PTR_ERROR** (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1311">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1311">Allowed From</span></span>

<span data-ttu-id="13f01-1312">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1313">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1313">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="13f01-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="13f01-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="13f01-1315">Skapa ett svarshuvud i en återanropsfunktion</span><span class="sxs-lookup"><span data-stu-id="13f01-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1316">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="13f01-1317">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1317">Description</span></span>

<span data-ttu-id="13f01-1318">Den här tjänsten används i HTTP(S)-serverns återanropsrutin (definieras av programmet) för att generera ett HTTP-svarshuvud.</span><span class="sxs-lookup"><span data-stu-id="13f01-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="13f01-1319">Serveranropsrutinen anropas när HTTP-servern svarar på klientens GET-, PUT- och DELETE-begäranden som kräver ett HTTP-svar.</span><span class="sxs-lookup"><span data-stu-id="13f01-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="13f01-1320">Den här funktionen tar svarsinformationen från programmet och genererar lämpligt svarshuvud.</span><span class="sxs-lookup"><span data-stu-id="13f01-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="13f01-1321">Mer information om *rutinerna för återanrop av serverbegäran* finns i service nx_web_http_server_create().</span><span class="sxs-lookup"><span data-stu-id="13f01-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="13f01-1322">Det här API:et är inaktuellt.</span><span class="sxs-lookup"><span data-stu-id="13f01-1322">This API is deprecated.</span></span> <span data-ttu-id="13f01-1323">Utvecklare uppmanas att använda *nx_web_http_server_callback_generate_response_header_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1324">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1324">Input Parameters</span></span>

- <span data-ttu-id="13f01-1325">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1326">**packet_pptr** Pekare en paket pekare som allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="13f01-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="13f01-1327">**status_code** Ange status för resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="13f01-1328">Exempel:</span><span class="sxs-lookup"><span data-stu-id="13f01-1328">Examples:</span></span>
  - <span data-ttu-id="13f01-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="13f01-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="13f01-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="13f01-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="13f01-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="13f01-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="13f01-1332">**content_length** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="13f01-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="13f01-1333">**content_type** Typ av HTTP, t.ex. "text/oformaterad"</span><span class="sxs-lookup"><span data-stu-id="13f01-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="13f01-1334">**additional_header** Pekare till ytterligare rubriktext</span><span class="sxs-lookup"><span data-stu-id="13f01-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1335">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1335">Return Values</span></span>

- <span data-ttu-id="13f01-1336">**NX_SUCCESS** (0x00) HTML-rubrik har skapats</span><span class="sxs-lookup"><span data-stu-id="13f01-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="13f01-1337">**NX_PTR_ERROR** (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1338">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1338">Allowed From</span></span>

<span data-ttu-id="13f01-1339">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1340">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1340">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="13f01-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="13f01-1342">Skapa ett svarshuvud i en återanropsfunktion</span><span class="sxs-lookup"><span data-stu-id="13f01-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1343">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1343">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="13f01-1344">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1344">Description</span></span>

<span data-ttu-id="13f01-1345">Den här tjänsten används i HTTP(S)-serverns återanropsrutin (definieras av programmet) för att generera ett HTTP-svarshuvud.</span><span class="sxs-lookup"><span data-stu-id="13f01-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="13f01-1346">Serveranropsrutinen anropas när HTTP-servern svarar på klientens GET-, PUT- och DELETE-begäranden som kräver ett HTTP-svar.</span><span class="sxs-lookup"><span data-stu-id="13f01-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="13f01-1347">Den här funktionen tar svarsinformationen från programmet och genererar lämpligt svarshuvud.</span><span class="sxs-lookup"><span data-stu-id="13f01-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="13f01-1348">Mer information om *rutinerna för återanrop av serverbegäran* finns i service nx_web_http_server_create().</span><span class="sxs-lookup"><span data-stu-id="13f01-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1349">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1349">Input Parameters</span></span>

- <span data-ttu-id="13f01-1350">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1351">**packet_pptr** Pekare en paket pekare som allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="13f01-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="13f01-1352">**status_code** Ange status för resursen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="13f01-1353">Exempel:</span><span class="sxs-lookup"><span data-stu-id="13f01-1353">Examples:</span></span>
  - <span data-ttu-id="13f01-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="13f01-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="13f01-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="13f01-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="13f01-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="13f01-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="13f01-1357">**status_code_length** Stränglängd för statuskod</span><span class="sxs-lookup"><span data-stu-id="13f01-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="13f01-1358">**content_length** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="13f01-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="13f01-1359">**content_type** Typ av HTTP, t.ex. "text/oformaterad"</span><span class="sxs-lookup"><span data-stu-id="13f01-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="13f01-1360">**content_type_length** Stränglängd för innehållstyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="13f01-1361">**additional_header** Pekare till ytterligare rubriktext</span><span class="sxs-lookup"><span data-stu-id="13f01-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="13f01-1362">**additional_header_length** Längden på ytterligare rubriktext</span><span class="sxs-lookup"><span data-stu-id="13f01-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1363">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1363">Return Values</span></span>

- <span data-ttu-id="13f01-1364">**NX_SUCCESS** (0x00) HTML-rubrik har skapats</span><span class="sxs-lookup"><span data-stu-id="13f01-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="13f01-1365">**NX_PTR_ERROR** (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1366">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1366">Allowed From</span></span>

<span data-ttu-id="13f01-1367">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1368">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1368">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="13f01-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="13f01-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="13f01-1370">Skicka ett HTTP-paket från återanropsfunktionen</span><span class="sxs-lookup"><span data-stu-id="13f01-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1371">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-1372">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1372">Description</span></span>

<span data-ttu-id="13f01-1373">Den här tjänsten skickar ett fullständigt HTTP-serversvar från ett HTTP-återanrop.</span><span class="sxs-lookup"><span data-stu-id="13f01-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="13f01-1374">HTTP-servern skickar paketet med NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="13f01-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="13f01-1375">HTTP-huvudet och data måste läggas till i paketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="13f01-1376">Om returstatusen indikerar ett fel måste HTTP-programmet släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="13f01-1377">Motringning ska returnera NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="13f01-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="13f01-1378">I *nx_web_http_server_callback_generate_response_header() finns* ett mer detaljerat exempel.</span><span class="sxs-lookup"><span data-stu-id="13f01-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1379">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1379">Input Parameters</span></span>

- <span data-ttu-id="13f01-1380">**server_ptr** Pekare till HTTP-serverkontrollblock</span><span class="sxs-lookup"><span data-stu-id="13f01-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="13f01-1381">**packet_ptr** Pekare till det paket som ska skickas</span><span class="sxs-lookup"><span data-stu-id="13f01-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1382">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1382">Return Values</span></span>

- <span data-ttu-id="13f01-1383">**NX_SUCCESS** (0x00) SKICKADE HTTP-serverpaket</span><span class="sxs-lookup"><span data-stu-id="13f01-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="13f01-1384">**NX_PTR_ERROR** (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1385">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1385">Allowed From</span></span>

<span data-ttu-id="13f01-1386">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1387">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1387">Example</span></span>

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="13f01-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="13f01-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="13f01-1389">Skicka svar från återanropsfunktionen</span><span class="sxs-lookup"><span data-stu-id="13f01-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1390">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="13f01-1391">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1391">Description</span></span>

<span data-ttu-id="13f01-1392">Den här tjänsten skickar den angivna svarsinformationen från programmets återanropsrutin.</span><span class="sxs-lookup"><span data-stu-id="13f01-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="13f01-1393">Detta används vanligtvis för att skicka anpassade svar som är associerade med GET/POST-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="13f01-1394">Observera att om den här funktionen används måste återanropsrutinen returnera statusen för NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="13f01-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="13f01-1395">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-1395">This service is deprecated.</span></span> <span data-ttu-id="13f01-1396">Utvecklare uppmanas att använda *nx_web_http_server_callback_response_send_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1397">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1397">Input Parameters</span></span>

- <span data-ttu-id="13f01-1398">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1399">**sidhuvud** Pekare till svarshuvudsträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="13f01-1400">**information** Pekare till informationssträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="13f01-1401">**additional_info** Pekare till den ytterligare informationssträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1402">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1402">Return Values</span></span>

- <span data-ttu-id="13f01-1403">**NX_SUCCESS** (0x00) HTTP-serversvaret har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1404">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1404">Allowed From</span></span>

<span data-ttu-id="13f01-1405">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1406">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1406">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="13f01-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="13f01-1408">Skicka svar från återanropsfunktionen</span><span class="sxs-lookup"><span data-stu-id="13f01-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1409">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="13f01-1410">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1410">Description</span></span>

<span data-ttu-id="13f01-1411">Den här tjänsten skickar den angivna svarsinformationen från programmets återanropsrutin.</span><span class="sxs-lookup"><span data-stu-id="13f01-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="13f01-1412">Detta används vanligtvis för att skicka anpassade svar som är associerade med GET/POST-begäranden.</span><span class="sxs-lookup"><span data-stu-id="13f01-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="13f01-1413">Observera att om den här funktionen används måste återanropsrutinen returnera statusen för NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="13f01-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="13f01-1414">Strängarna i sidhuvud, information och additional_info måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="13f01-1415">Den här tjänsten *ersätter nx_web_http_server_callback_response_send*().</span><span class="sxs-lookup"><span data-stu-id="13f01-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="13f01-1416">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1417">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1417">Input Parameters</span></span>

- <span data-ttu-id="13f01-1418">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1419">**rubrik** Pekare till svarshuvudsträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="13f01-1420">**header_length** Längden på svarshuvudsträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="13f01-1421">**information** Pekare till informationssträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="13f01-1422">**Information_length** Längden på informationssträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="13f01-1423">**additional_info** Pekare till den ytterligare informationssträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="13f01-1424">**additional_info_length** Längden på den ytterligare informationssträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1425">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1425">Return Values</span></span>

- <span data-ttu-id="13f01-1426">**NX_SUCCESS** (0x00) HTTP-serversvaret har skickats</span><span class="sxs-lookup"><span data-stu-id="13f01-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1427">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1427">Allowed From</span></span>

<span data-ttu-id="13f01-1428">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1429">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1429">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="13f01-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="13f01-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="13f01-1431">Hämta innehåll från begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1432">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1433">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1433">Description</span></span>

<span data-ttu-id="13f01-1434">Den här tjänsten försöker hämta den angivna mängden innehåll från POST- eller PUT HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="13f01-1435">Den ska anropas från programmets begäran för att meddela återanrop som anges när HTTP-servern skapas (*nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="13f01-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1436">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1436">Input Parameters</span></span>

- <span data-ttu-id="13f01-1437">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1438">**packet_ptr** Pekare till HTTP-klientens begärandepaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="13f01-1439">Observera att det här paketet inte får släppas av begäran om att meddela återanrop.</span><span class="sxs-lookup"><span data-stu-id="13f01-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="13f01-1440">**byte_offset** Antal byte som ska förskjutas till innehållsområdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="13f01-1441">**destination_ptr** Pekare till målområdet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="13f01-1442">**destination_size** Maximalt antal byte som är tillgängliga i målområdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="13f01-1443">**actual_size** Pekare till målvariabeln som ställs in på den faktiska storleken på det kopierade innehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1444">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1444">Return Values</span></span>

- <span data-ttu-id="13f01-1445">**NX_SUCCESS** (0x00) Lyckat HTTP-serverinnehåll Hämta</span><span class="sxs-lookup"><span data-stu-id="13f01-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="13f01-1446">**NX_WEB_HTTP_ERROR** (0x30000) internt HTTP-serverfel</span><span class="sxs-lookup"><span data-stu-id="13f01-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="13f01-1447">**NX_WEB_HTTP_DATA_END** (0x30007) Slut på begärandeinnehåll</span><span class="sxs-lookup"><span data-stu-id="13f01-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="13f01-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP-server timeout för att hämta nästa paket med innehåll</span><span class="sxs-lookup"><span data-stu-id="13f01-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="13f01-1449">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1450">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1451">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1451">Allowed From</span></span>

<span data-ttu-id="13f01-1452">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1453">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="13f01-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="13f01-1455">Hämta innehåll från begäran/stöder innehållslängden noll längd</span><span class="sxs-lookup"><span data-stu-id="13f01-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1456">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1457">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1457">Description</span></span>

<span data-ttu-id="13f01-1458">Den här tjänsten är nästan identisk *med nx_web_http_server_content_get()*; Den försöker hämta den angivna mängden innehåll från POST- eller PUT HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="13f01-1459">Den hanterar dock begäranden med innehållslängden noll värde (tom begäran) som en giltig begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="13f01-1460">Den ska anropas från programmets begäran för att meddela återanrop som anges när HTTP-servern skapas (*nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="13f01-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="13f01-1461">Den här tjänsten *ersätter nx_web_http_server_content_get*().</span><span class="sxs-lookup"><span data-stu-id="13f01-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="13f01-1462">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1463">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1463">Input Parameters</span></span>

- <span data-ttu-id="13f01-1464">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1465">**packet_ptr** Pekare till HTTP-klientens begärandepaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="13f01-1466">Observera att det här paketet inte får släppas av begäran om att meddela återanrop.</span><span class="sxs-lookup"><span data-stu-id="13f01-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="13f01-1467">**byte_offset** Antal byte som ska förskjutas till innehållsområdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="13f01-1468">**destination_ptr** Pekare till målområdet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="13f01-1469">**destination_size** Maximalt antal byte som är tillgängliga i målområdet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="13f01-1470">**actual_size** Pekare till målvariabeln som ställs in på den faktiska storleken på det kopierade innehållet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1471">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1471">Return Values</span></span>

- <span data-ttu-id="13f01-1472">**NX_SUCCESS** (0x00) Http-innehåll hämta</span><span class="sxs-lookup"><span data-stu-id="13f01-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="13f01-1473">**NX_WEB_HTTP_ERROR** (0x30000) internt HTTP-serverfel</span><span class="sxs-lookup"><span data-stu-id="13f01-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="13f01-1474">**NX_WEB_HTTP_DATA_END** (0x30007) Slut på begärandeinnehåll</span><span class="sxs-lookup"><span data-stu-id="13f01-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="13f01-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP-server-timeout för att hämta nästa paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="13f01-1476">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1477">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1478">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1478">Allowed From</span></span>

<span data-ttu-id="13f01-1479">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1480">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="13f01-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="13f01-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="13f01-1482">Hämta längden på innehållet i begäran/stöder innehållslängd på noll värde</span><span class="sxs-lookup"><span data-stu-id="13f01-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1483">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="13f01-1484">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1484">Description</span></span>

<span data-ttu-id="13f01-1485">Den här tjänsten försöker hämta HTTP-innehållslängden i det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="13f01-1486">Returvärdet anger slutförandestatus och det faktiska längdvärdet returneras i indata pekaren content_length.</span><span class="sxs-lookup"><span data-stu-id="13f01-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="13f01-1487">Om det inte finns något HTTP-innehåll/innehållslängd = 0 returnerar den här rutinen fortfarande en slutförandestatus och content_length pekar på en giltig längd (noll).</span><span class="sxs-lookup"><span data-stu-id="13f01-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="13f01-1488">Den ska anropas från programmets begäran för att meddela återanrop som anges när HTTP-servern skapas (*nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="13f01-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1489">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1489">Input Parameters</span></span>

- <span data-ttu-id="13f01-1490">**packet_ptr** Pekare till HTTP-klientens begärandepaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="13f01-1491">Observera att det här paketet inte får släppas av begäran om att meddela återanrop.</span><span class="sxs-lookup"><span data-stu-id="13f01-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="13f01-1492">**content_length** Pekare till värde som hämtats från fältet Innehållslängd</span><span class="sxs-lookup"><span data-stu-id="13f01-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1493">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1493">Return Values</span></span>

- <span data-ttu-id="13f01-1494">**NX_SUCCESS** (0x00) Lyckad http-serverinnehållslängd get</span><span class="sxs-lookup"><span data-stu-id="13f01-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="13f01-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Felaktigt HTTP-huvudformat</span><span class="sxs-lookup"><span data-stu-id="13f01-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="13f01-1496">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1497">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1497">Allowed From</span></span>

<span data-ttu-id="13f01-1498">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1499">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="13f01-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="13f01-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="13f01-1501">Skapa en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="13f01-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1502">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1502">Prototype</span></span>

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="13f01-1503">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1503">Description</span></span>

<span data-ttu-id="13f01-1504">Den här tjänsten skapar en HTTP-serverinstans som körs i kontexten för en egen ThreadX-tråd.</span><span class="sxs-lookup"><span data-stu-id="13f01-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="13f01-1505">De *valfria authentication_check* *och request_notify* för programanrop ger programkontroll över de grundläggande åtgärderna för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="13f01-1506">Den här tjänsten används för att skapa HTTP-servrar i klartext och TLS-skyddade HTTPS-servrar.</span><span class="sxs-lookup"><span data-stu-id="13f01-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="13f01-1507">Information om hur du aktiverar HTTPS med TLS finns *i nx_web_http_server_secure_configure()*.</span><span class="sxs-lookup"><span data-stu-id="13f01-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1508">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1508">Input Parameters</span></span>

- <span data-ttu-id="13f01-1509">**http_server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1510">**http_server_name** Pekar på HTTP-serverns namn.</span><span class="sxs-lookup"><span data-stu-id="13f01-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="13f01-1511">**ip_ptr** Pekare till ip-instans som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="13f01-1512">**server_port** TCP-lyssningsport för serverinstans.</span><span class="sxs-lookup"><span data-stu-id="13f01-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="13f01-1513">**media_ptr** Pekare till tidigare skapade FileX-medieinstanser.</span><span class="sxs-lookup"><span data-stu-id="13f01-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="13f01-1514">**stack_ptr** Pekare till http-serverns trådstackområde.</span><span class="sxs-lookup"><span data-stu-id="13f01-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="13f01-1515">**stack_size** Pekare till http-serverns trådstackstorlek.</span><span class="sxs-lookup"><span data-stu-id="13f01-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="13f01-1516">**authentication_check** Funktions pekare till programmets autentiseringskontrollrutin.</span><span class="sxs-lookup"><span data-stu-id="13f01-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="13f01-1517">Om detta anges anropas den här rutinen för varje HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="13f01-1518">Om den här parametern är NULL utförs ingen autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="13f01-1519">Den här parametern är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-1519">This parameter is deprecated.</span></span> <span data-ttu-id="13f01-1520">Anropa *nx_web_http_server_authenticate_check_set*() i stället.</span><span class="sxs-lookup"><span data-stu-id="13f01-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="13f01-1521">**request_notify** Funktionspekare till programmets avvisningsrutin för begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="13f01-1522">Om detta anges anropas den här rutinen före HTTP-serverbearbetningen av begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="13f01-1523">På så sätt kan resursnamnet omdirigeras eller fält i en resurs uppdateras innan HTTP-klientbegäran slutförs.</span><span class="sxs-lookup"><span data-stu-id="13f01-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1524">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1524">Return Values</span></span>

- <span data-ttu-id="13f01-1525">**NX_SUCCESS** (0x00) Lyckad HTTP-server för att skapa.</span><span class="sxs-lookup"><span data-stu-id="13f01-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="13f01-1526">NX_PTR_ERROR (0x07) Ogiltig HTTP-server, IP-adress, media, stack eller paketpoolspekare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="13f01-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Paketnyttolasten för poolen är inte tillräckligt stor för att innehålla en fullständig HTTP-begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1528">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1528">Allowed From</span></span>

<span data-ttu-id="13f01-1529">Initiering, Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1530">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="13f01-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="13f01-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="13f01-1532">Ta bort en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="13f01-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1533">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-1534">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1534">Description</span></span>

<span data-ttu-id="13f01-1535">Den här tjänsten tar bort en http-serverinstans som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1536">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1536">Input Parameters</span></span>

- <span data-ttu-id="13f01-1537">**http_server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1538">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1538">Return Values</span></span>

- <span data-ttu-id="13f01-1539">**NX_SUCCESS** (0x00) Lyckad BORTTAGNING av HTTP-server</span><span class="sxs-lookup"><span data-stu-id="13f01-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="13f01-1540">NX_PTR_ERROR (0x07) Ogiltig HTTP-server-pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="13f01-1541">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1542">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1542">Allowed From</span></span>

<span data-ttu-id="13f01-1543">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1544">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="13f01-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="13f01-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="13f01-1546">Hämta plats och längd för entitetsdata</span><span class="sxs-lookup"><span data-stu-id="13f01-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1547">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="13f01-1548">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1548">Description</span></span>

<span data-ttu-id="13f01-1549">Den här tjänsten avgör platsen för datastarten i den aktuella multipart-entiteten i de mottagna klientmeddelandena och längden på data som inte inkluderar gränssträngen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="13f01-1550">Internt uppdaterar HTTP-servern sina egna förskjutningar så att den här funktionen kan anropas igen på samma klientdatagram för meddelanden med flera entiteter.</span><span class="sxs-lookup"><span data-stu-id="13f01-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="13f01-1551">Paketpekaren uppdateras till nästa paket där klientmeddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="13f01-1552">Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="13f01-1553">Observera också att programmet inte ska släppa paketet som det packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="13f01-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="13f01-1554">Detta görs internt av HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="13f01-1555">Se *nx_web_http_server_get_entity_header()* för mer information.</span><span class="sxs-lookup"><span data-stu-id="13f01-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1556">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1556">Input Parameters</span></span>

- <span data-ttu-id="13f01-1557">**server_ptr** Pekare till HTTP-server</span><span class="sxs-lookup"><span data-stu-id="13f01-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="13f01-1558">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="13f01-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="13f01-1559">Observera att programmet inte får släppa det här paketet</span><span class="sxs-lookup"><span data-stu-id="13f01-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="13f01-1560">**available_offset** Pekare till förskjutning av entitetsdata från pekaren för paketförberedelser</span><span class="sxs-lookup"><span data-stu-id="13f01-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="13f01-1561">**available_length** Pekare till längden på entitetsdata</span><span class="sxs-lookup"><span data-stu-id="13f01-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1562">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1562">Return Values</span></span>

- <span data-ttu-id="13f01-1563">**NX_SUCCESS** (0x00) Storleken och platsen för entitetsinnehåll har hämtats</span><span class="sxs-lookup"><span data-stu-id="13f01-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="13f01-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Innehåll för interna multipart-markörer för HTTP-servern finns redan</span><span class="sxs-lookup"><span data-stu-id="13f01-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="13f01-1565">NX_WEB_HTTP_ERROR (0x30000) internt HTTP-serverfel</span><span class="sxs-lookup"><span data-stu-id="13f01-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="13f01-1566">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1567">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1567">Allowed From</span></span>

<span data-ttu-id="13f01-1568">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1569">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1569">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="13f01-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="13f01-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="13f01-1571">Hämta innehållet i entitetsrubriken</span><span class="sxs-lookup"><span data-stu-id="13f01-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1572">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1573">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1573">Description</span></span>

<span data-ttu-id="13f01-1574">Den här tjänsten hämtar entitetsrubriken till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="13f01-1575">Internt uppdaterar HTTP Server sina egna pekare för att hitta nästa entitet med flera delar i ett klientdatagram med flera entitetsrubriker.</span><span class="sxs-lookup"><span data-stu-id="13f01-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="13f01-1576">Paketpekaren uppdateras till nästa paket där klientmeddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="13f01-1577">Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="13f01-1578">Observera också att programmet inte ska släppa det paket som det packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="13f01-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1579">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1579">Input Parameters</span></span>

- <span data-ttu-id="13f01-1580">**server_ptr** Pekare till HTTP-server</span><span class="sxs-lookup"><span data-stu-id="13f01-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="13f01-1581">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="13f01-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="13f01-1582">Observera att programmet inte får släppa det här paketet</span><span class="sxs-lookup"><span data-stu-id="13f01-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="13f01-1583">**entity_header_buffer** Pekare till plats för att lagra entitetsrubrik</span><span class="sxs-lookup"><span data-stu-id="13f01-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="13f01-1584">**buffer_size** Storleken på indatabufferten</span><span class="sxs-lookup"><span data-stu-id="13f01-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1585">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1585">Return Values</span></span>

- <span data-ttu-id="13f01-1586">**NX_SUCCESS** (0x00) Entitetsrubrik har hämtats</span><span class="sxs-lookup"><span data-stu-id="13f01-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="13f01-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Det går inte att hitta entitetsrubrikfältet</span><span class="sxs-lookup"><span data-stu-id="13f01-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="13f01-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiden har gått ut för att ta emot nästa paket för multipacket-klientmeddelande</span><span class="sxs-lookup"><span data-stu-id="13f01-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="13f01-1589">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1590">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="13f01-1591">NX_WEB_HTTP_ERROR (0x30000) Internt HTTP-fel</span><span class="sxs-lookup"><span data-stu-id="13f01-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1592">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1592">Allowed From</span></span>

<span data-ttu-id="13f01-1593">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1594">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1594">Example</span></span>

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="13f01-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="13f01-1596">Ställ in återanropet för att hämta GMT-datum och tid</span><span class="sxs-lookup"><span data-stu-id="13f01-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1597">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="13f01-1598">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1598">Description</span></span>

<span data-ttu-id="13f01-1599">Den här tjänsten ställer in återanrop för att hämta GMT-datum och -tid med en tidigare skapad HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="13f01-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="13f01-1600">Den här tjänsten anropas med HTTP-servern skapar ett huvud i HTTP-serversvar till klienten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1601">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1601">Input Parameters</span></span>

- <span data-ttu-id="13f01-1602">**server_ptr** Pekare till HTTP-server</span><span class="sxs-lookup"><span data-stu-id="13f01-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="13f01-1603">**gmt_get** Pekare till GMT-återanrop</span><span class="sxs-lookup"><span data-stu-id="13f01-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="13f01-1604">**datum** Pekare till det datum som hämtades</span><span class="sxs-lookup"><span data-stu-id="13f01-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1605">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1605">Return Values</span></span>

- <span data-ttu-id="13f01-1606">**NX_SUCCESS** (0x00) Ange återanropet</span><span class="sxs-lookup"><span data-stu-id="13f01-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="13f01-1607">NX_PTR_ERROR (0x07) Ogiltig paket- eller parameterpekare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1608">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1608">Allowed From</span></span>

<span data-ttu-id="13f01-1609">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1610">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1610">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="13f01-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="13f01-1612">Ange motringning för att hantera ogiltig användare/lösenord</span><span class="sxs-lookup"><span data-stu-id="13f01-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1613">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="13f01-1614">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1614">Description</span></span>

<span data-ttu-id="13f01-1615">Den här tjänsten anger återanropet som anropas när ett ogiltigt användarnamn och lösenord tas emot i en klientbegäran om att hämta, placera eller ta bort, antingen genom sammanfattad eller grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="13f01-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="13f01-1616">HTTP-servern måste ha skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1617">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1617">Input Parameters</span></span>

- <span data-ttu-id="13f01-1618">**server_ptr** Pekare till HTTP-server</span><span class="sxs-lookup"><span data-stu-id="13f01-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="13f01-1619">**invalid_username_password_callback** Pekare till ogiltig användare/skicka återanrop</span><span class="sxs-lookup"><span data-stu-id="13f01-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="13f01-1620">**resurs** Pekare till den resurs som anges av klienten</span><span class="sxs-lookup"><span data-stu-id="13f01-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="13f01-1621">**client_address** Klientadress</span><span class="sxs-lookup"><span data-stu-id="13f01-1621">**client_address** Client address</span></span>
- <span data-ttu-id="13f01-1622">**request_type** Anger typ av klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="13f01-1623">Kanske:</span><span class="sxs-lookup"><span data-stu-id="13f01-1623">May be:</span></span>
  - <span data-ttu-id="13f01-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="13f01-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="13f01-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="13f01-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="13f01-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="13f01-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1627">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1627">Return Values</span></span>

- <span data-ttu-id="13f01-1628">**NX_SUCCESS** (0x00) Ange återanropet</span><span class="sxs-lookup"><span data-stu-id="13f01-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="13f01-1629">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1630">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1630">Allowed From</span></span>

<span data-ttu-id="13f01-1631">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1632">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1632">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="13f01-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="13f01-1634">Ange ytterligare MIME-kartor för HTML</span><span class="sxs-lookup"><span data-stu-id="13f01-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1635">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="13f01-1636">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1636">Description</span></span>

<span data-ttu-id="13f01-1637">Med den här tjänsten kan HTTP-programutvecklaren lägga till ytterligare MIME-typer från de MIME-standardtyper som tillhandahålls av NetX Web HTTP Server.</span><span class="sxs-lookup"><span data-stu-id="13f01-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="13f01-1638">En *lista över definierade typer finns i nx_web_http_server_get_type().*</span><span class="sxs-lookup"><span data-stu-id="13f01-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="13f01-1639">När en klientbegäran tas emot, t.ex. en GET-begäran, parsar HTTP-servern den begärda filtypen från HTTP-huvudet med hjälp av den ytterligare MIME-mappningsuppsättningen och om ingen matchning hittas letar den efter en matchning i STANDARD-MIME-kartan för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="13f01-1640">Om ingen matchning hittas får MIME-typen som standard "text/oformaterad".</span><span class="sxs-lookup"><span data-stu-id="13f01-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="13f01-1641">Om funktionen request notify är registrerad på HTTP-servern kan begäran meddela motringning *anropa nx_web_http_server_type_get_extended()* för att parsa filtypen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1642">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1642">Input Parameters</span></span>

- <span data-ttu-id="13f01-1643">**server_ptr** Pekare till HTTP Server-instans</span><span class="sxs-lookup"><span data-stu-id="13f01-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="13f01-1644">**mime_maps** Pekare till en MIME-kartmatris</span><span class="sxs-lookup"><span data-stu-id="13f01-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="13f01-1645">**mime_map_num** Antal MIME-kartor i matris</span><span class="sxs-lookup"><span data-stu-id="13f01-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1646">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1646">Return Values</span></span>

- <span data-ttu-id="13f01-1647">**NX_SUCCESS** (0x00) LYCKAD MIME-kartuppsättning för HTTP-server</span><span class="sxs-lookup"><span data-stu-id="13f01-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="13f01-1648">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1649">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1649">Allowed From</span></span>

<span data-ttu-id="13f01-1650">Initiering, Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1651">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1651">Example</span></span>

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="13f01-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="13f01-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="13f01-1653">Allokera ett HTTP(S)-paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1654">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="13f01-1655">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1655">Description</span></span>

<span data-ttu-id="13f01-1656">Den här tjänsten försöker allokera ett paket för HTTP(S)-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="13f01-1657">Observera att om ett efterföljande NetX- eller HTTP Server-API som använder det här paketet som indata **misslyckas,** till exempel nx_packet_data_append eller \*\*nx_web_http_server_callback_packet_send, ansvarar programmet för att släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="13f01-1658">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1658">Input Parameters</span></span>

- <span data-ttu-id="13f01-1659">**server_ptr** Pekare till HTTP-serverkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="13f01-1660">**packet_ptr** Pekare till allokerat paket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="13f01-1661">**wait_option** Definierar väntetiden i tick om det inte finns några paket tillgängliga i paketpoolen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="13f01-1662">Väntealternativen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="13f01-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="13f01-1663">**NX_NO_WAIT** (0x00000000) Om du NX_NO_WAIT här alternativet returneras den anropande tråden omedelbart om begäran inte kan uppfyllas.</span><span class="sxs-lookup"><span data-stu-id="13f01-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="13f01-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="13f01-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="13f01-1665">**timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.</span><span class="sxs-lookup"><span data-stu-id="13f01-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1666">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1666">Return Values</span></span>

- <span data-ttu-id="13f01-1667">**NX_SUCCESS** (0x00) Allokera ett lyckat paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="13f01-1668">**NX_NO_PACKET** (0x01) Inget paket tillgängligt</span><span class="sxs-lookup"><span data-stu-id="13f01-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="13f01-1669">**NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop *till tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="13f01-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="13f01-1670">**NX_INVALID_PARAMETERS** paketstorlek (0x4D) stöder inte protokoll.</span><span class="sxs-lookup"><span data-stu-id="13f01-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="13f01-1671">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1672">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1673">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1673">Allowed From</span></span>

<span data-ttu-id="13f01-1674">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1675">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="13f01-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="13f01-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="13f01-1677">Extrahera innehållslängd och ange pekare till början av data</span><span class="sxs-lookup"><span data-stu-id="13f01-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1678">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="13f01-1679">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1679">Description</span></span>

<span data-ttu-id="13f01-1680">Den här tjänsten extraherar innehållslängden från HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="13f01-1681">Den uppdaterar också det angivna paketet på följande sätt: paketförberedaren (början på platsen för paketbufferten att skriva till) är inställd på HTTP-innehållet (data) som precis skickade HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="13f01-1682">Om början av innehållet inte finns i det aktuella paketet väntar funktionen tills nästa paket tas emot med hjälp av NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE väntealternativet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="13f01-1683">Observera att detta inte ska anropas innan *du anropar nx_web_http_server_get_entity_header()* eftersom det ändrar paketförberedar pekaren förbi entitetsrubriken.</span><span class="sxs-lookup"><span data-stu-id="13f01-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1684">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1684">Input Parameters</span></span>

- <span data-ttu-id="13f01-1685">**server_ptr** Pekare till HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="13f01-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="13f01-1686">**packet_ptr** Pekare till paket pekare för att returnera paketet med uppdaterad förberedelse pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="13f01-1687">**content_length** Pekare till extraherade content_length</span><span class="sxs-lookup"><span data-stu-id="13f01-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1688">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1688">Return Values</span></span>

- <span data-ttu-id="13f01-1689">**NX_SUCCESS** (0x00) HTTP-innehållslängd hittades och paketet har uppdaterats</span><span class="sxs-lookup"><span data-stu-id="13f01-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="13f01-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiden har gått ut och väntar på nästa paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="13f01-1691">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1692">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1692">Allowed From</span></span>

<span data-ttu-id="13f01-1693">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1694">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1694">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="13f01-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="13f01-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="13f01-1696">Ta emot nästa HTTP-paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1697">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-1698">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1698">Description</span></span>

<span data-ttu-id="13f01-1699">Den här tjänsten returnerar nästa paket som tas emot på HTTP-serversocketen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="13f01-1700">Väntealternativet för att ta emot ett paket NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="13f01-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="13f01-1701">Observera att om det lyckas ansvarar programmet för att släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1702">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1702">Input Parameters</span></span>

- <span data-ttu-id="13f01-1703">**server_ptr** Pekare till HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="13f01-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="13f01-1704">**packet_ptr** Pekare till mottaget paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1705">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1705">Return Values</span></span>

- <span data-ttu-id="13f01-1706">**NX_SUCCESS** (0x00) Tog emot nästa HTTP-paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="13f01-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiden har gått ut och väntar på nästa paket</span><span class="sxs-lookup"><span data-stu-id="13f01-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="13f01-1708">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1709">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1709">Allowed From</span></span>

<span data-ttu-id="13f01-1710">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1711">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="13f01-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="13f01-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="13f01-1713">Hämta parametern från begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1714">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1715">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1715">Description</span></span>

<span data-ttu-id="13f01-1716">Den här tjänsten försöker hämta den angivna HTTP-URL-parametern i det angivna begärandepaketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="13f01-1717">Om den begärda HTTP-parametern inte finns returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="13f01-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="13f01-1718">Den här rutinen ska anropas från programmets begäran meddela återanrop som anges när HTTP-servern skapas (*nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="13f01-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1719">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1719">Input Parameters</span></span>

- <span data-ttu-id="13f01-1720">**packet_ptr** Pekare till HTTP-klientbegärandepaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="13f01-1721">Observera att programmet inte får släppa det här paketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="13f01-1722">**param_number** Logiskt nummer för parametern med början vid noll, från vänster till höger i parameterlistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="13f01-1723">**param_ptr** Målområde för att kopiera parametern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="13f01-1724">**param_size** Returnera den totala parameterdatalängden (i byte).</span><span class="sxs-lookup"><span data-stu-id="13f01-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="13f01-1725">**max_param_size** Maximal storlek för parameterns målområde.</span><span class="sxs-lookup"><span data-stu-id="13f01-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1726">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1726">Return Values</span></span>

- <span data-ttu-id="13f01-1727">**NX_SUCCESS** (0x00) Lyckad HTTP-serverparameter get</span><span class="sxs-lookup"><span data-stu-id="13f01-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="13f01-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Det gick inte att hitta den angivna parametern</span><span class="sxs-lookup"><span data-stu-id="13f01-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="13f01-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Parametern för begäran avslutades inte korrekt</span><span class="sxs-lookup"><span data-stu-id="13f01-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="13f01-1730">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1731">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1732">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1732">Allowed From</span></span>

<span data-ttu-id="13f01-1733">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1734">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="13f01-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="13f01-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="13f01-1736">Hämta fråga från begäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1737">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1738">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1738">Description</span></span>

<span data-ttu-id="13f01-1739">Den här tjänsten försöker hämta den angivna HTTP-URL-frågan i det angivna begärandepaketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="13f01-1740">Om den begärda HTTP-frågan inte finns returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="13f01-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="13f01-1741">Den här rutinen ska anropas från programmets begäran meddela återanrop som anges när HTTP-servern skapas (*nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="13f01-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1742">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1742">Input Parameters</span></span>

- <span data-ttu-id="13f01-1743">**packet_ptr** Pekare till HTTP-klientbegärandepaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="13f01-1744">Observera att programmet inte får släppa det här paketet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="13f01-1745">**query_number** Logiskt nummer för parametern med början vid noll, från vänster till höger i frågelistan.</span><span class="sxs-lookup"><span data-stu-id="13f01-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="13f01-1746">**query_ptr** Målområde för att kopiera frågan.</span><span class="sxs-lookup"><span data-stu-id="13f01-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="13f01-1747">**query_size** Returnera frågedatastorlek (i byte).</span><span class="sxs-lookup"><span data-stu-id="13f01-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="13f01-1748">**max_query_size** Maximal storlek på frågemålet</span><span class="sxs-lookup"><span data-stu-id="13f01-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="13f01-1749">Området.</span><span class="sxs-lookup"><span data-stu-id="13f01-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1750">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1750">Return Values</span></span>

- <span data-ttu-id="13f01-1751">**NX_SUCCESS** (0x00) Lyckad HTTP-serverfråga hämta</span><span class="sxs-lookup"><span data-stu-id="13f01-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="13f01-1752">**NX_WEB_HTTP_FAILED** (0x30002) Frågestorlek för liten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="13f01-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Det gick inte att hitta den angivna frågan</span><span class="sxs-lookup"><span data-stu-id="13f01-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="13f01-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) Ingen fråga i Klientbegäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="13f01-1755">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1756">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1757">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1757">Allowed From</span></span>

<span data-ttu-id="13f01-1758">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1759">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="13f01-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="13f01-1761">Ange segmenterad överföring för HTTP(S)-svar</span><span class="sxs-lookup"><span data-stu-id="13f01-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1762">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-1763">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1763">Description</span></span>

<span data-ttu-id="13f01-1764">Den här tjänsten använder segmenterad överföringskodning för att skicka ett anpassat HTTP(S)-svarsdatapaket *som skapats med nx_web_http_server_response_packet_allocate*() till klienten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1765">Om programmet använder segmenterad överföringskodning för att skicka ett svarsdatapaket måste det anropa den här tjänsten efter *anropet nx_web_http_server_response_packet_allocate*() och innan *det anropar nx_web_http_server_callback_packet_send*().</span><span class="sxs-lookup"><span data-stu-id="13f01-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1766">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1766">Input Parameters</span></span>

- <span data-ttu-id="13f01-1767">**client_ptr** Pekare till HTTP-klientkontrollblock.</span><span class="sxs-lookup"><span data-stu-id="13f01-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="13f01-1768">**chunk_size** Storleken på segmentdata i oktett.</span><span class="sxs-lookup"><span data-stu-id="13f01-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="13f01-1769">**packet_ptr** Pekare för HTTP(S)-begärandedatapaket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1770">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1770">Return Values</span></span>

- <span data-ttu-id="13f01-1771">**NX_SUCCESS** (0x00) Lyckad uppsättning segmenterad.</span><span class="sxs-lookup"><span data-stu-id="13f01-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="13f01-1772">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1773">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1773">Allowed From</span></span>

<span data-ttu-id="13f01-1774">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1775">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="13f01-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="13f01-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="13f01-1777">Konfigurera en HTTP-server för att använda TLS för säker HTTPS</span><span class="sxs-lookup"><span data-stu-id="13f01-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1778">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1778">Prototype</span></span>

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1779">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1779">Description</span></span>

<span data-ttu-id="13f01-1780">Den här tjänsten konfigurerar en tidigare skapad NetX Web HTTP-serverinstans för att använda TLS för säker HTTPS-kommunikation.</span><span class="sxs-lookup"><span data-stu-id="13f01-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="13f01-1781">Parametrarna används för att konfigurera alla möjliga TLS-sessioner med identiskt tillstånd så att varje inkommande HTTPS-klient har konsekvent beteende.</span><span class="sxs-lookup"><span data-stu-id="13f01-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="13f01-1782">Antalet TLS-sessioner styrs med hjälp av NX_WEB_HTTP_SESSION_MAX.</span><span class="sxs-lookup"><span data-stu-id="13f01-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="13f01-1783">Den kryptografiska rutintabellen (chiffertabell) delas mellan alla TLS-sessioner eftersom den bara innehåller funktionspekare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="13f01-1784">Metadata och paket som åter sätts ihop med buffertar fördelas jämnt mellan alla TLS-sessioner.</span><span class="sxs-lookup"><span data-stu-id="13f01-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="13f01-1785">Om buffertstorleken inte är jämnt delbar med antalet sessioner kommer resten att vara oanvänd.</span><span class="sxs-lookup"><span data-stu-id="13f01-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="13f01-1786">Det skickade identitetscertifikatet används av alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="13f01-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="13f01-1787">Under TLS-åtgärden läses serveridentitetscertifikatet endast från, så kopior behövs inte för varje session.</span><span class="sxs-lookup"><span data-stu-id="13f01-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="13f01-1788">De betrodda certifikaten läggs till i varje TLS-session på HTTPS-servern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="13f01-1789">Dessa används för autentisering med klientcertifikat som aktiveras automatiskt när fjärranslutet certifikatutrymme anges.</span><span class="sxs-lookup"><span data-stu-id="13f01-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="13f01-1790">Fjärrcertifikatmatrisen och bufferten delas som standard mellan alla TLS-sessioner.</span><span class="sxs-lookup"><span data-stu-id="13f01-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="13f01-1791">Fjärrcertifikaten används för klientcertifikatautentisering som aktiveras automatiskt när antalet fjärrcertifikat inte är noll.</span><span class="sxs-lookup"><span data-stu-id="13f01-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="13f01-1792">På grund av att bufferten delas kan vissa sessioner blockeras under certifikatverifieringen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="13f01-1793">Om du vill inaktivera klientcertifikatautentisering skickar NX_NULL för remote_certificates-parametern och värdet 0 för remote_certs_num parametern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="13f01-1794">Returvärden innehåller eventuella TLS-felkoder som är resultatet av problem i konfigurationen av TLS-sessionerna.</span><span class="sxs-lookup"><span data-stu-id="13f01-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1795">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1795">Input Parameters</span></span>

- <span data-ttu-id="13f01-1796">**http_server_ptr** Pekare till HTTP Server-instans.</span><span class="sxs-lookup"><span data-stu-id="13f01-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="13f01-1797">**crypto_table** Pekare till TLS-chiffertabell.</span><span class="sxs-lookup"><span data-stu-id="13f01-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="13f01-1798">**metadata_buffer** Pekare till kryptografisk metadatabuffert.</span><span class="sxs-lookup"><span data-stu-id="13f01-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="13f01-1799">**metadata_size** Storlek på buffert för kryptografiska metadata.</span><span class="sxs-lookup"><span data-stu-id="13f01-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="13f01-1800">**packet_buffer** TLS-paket sätts ihop på ett åter sätt.</span><span class="sxs-lookup"><span data-stu-id="13f01-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="13f01-1801">**packet_buffer** Storleken på TLS-paketbufferten – ska vara lika med (<önskad TLS-buffertstorlek\* NX_WEB_HTTP_SESSION_MAX).</span><span class="sxs-lookup"><span data-stu-id="13f01-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="13f01-1802">**identity_certificate** TLS-serveridentitetscertifikat – används för alla HTTPS-serversessioner.</span><span class="sxs-lookup"><span data-stu-id="13f01-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="13f01-1803">**trusted_certificates** Pekare till matris NX_SECURE_X509_CERT objekt, som används för att verifiera inkommande klientcertifikat om klientcertifikatautentisering är aktiverat genom att skicka ett värde som *inte är noll för remote_certs_num-parametern.*</span><span class="sxs-lookup"><span data-stu-id="13f01-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="13f01-1804">**trusted_certs_num** Antal betrodda certifikat i *trusted_certificates* matrisen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="13f01-1805">**remote_certificates** Pekare till matris med NX_SECURE_X509_CERT objekt som används för inkommande klientcertifikat.</span><span class="sxs-lookup"><span data-stu-id="13f01-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="13f01-1806">**remote_certs_num** Antal fjärrcertifikat.</span><span class="sxs-lookup"><span data-stu-id="13f01-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="13f01-1807">Bör vara det maximala antalet förväntade certifikat från klienter.</span><span class="sxs-lookup"><span data-stu-id="13f01-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="13f01-1808">Autentisering med klientcertifikat aktiveras automatiskt när detta inte är noll.</span><span class="sxs-lookup"><span data-stu-id="13f01-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="13f01-1809">**remote_certificate_buffer** Buffert som ska innehålla inkommande fjärrcertifikat från klienter om autentisering med klientcertifikat är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="13f01-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="13f01-1810">remote_cert_buffer_size storleken på bufferten för fjärrcertifikat.</span><span class="sxs-lookup"><span data-stu-id="13f01-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="13f01-1811">Ska vara lika med (<maximal förväntad \* certifikatstorlek remote_certs_num).</span><span class="sxs-lookup"><span data-stu-id="13f01-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="13f01-1812">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1812">Return Values</span></span>

- <span data-ttu-id="13f01-1813">**NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="13f01-1814">**NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="13f01-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="13f01-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) En mottagen TLS-meddelandetyp är felaktig.</span><span class="sxs-lookup"><span data-stu-id="13f01-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="13f01-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="13f01-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="13f01-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Meddelandebearbetningen under TLS-handskakningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="13f01-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="13f01-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett inkommande meddelande misslyckades med en hash-MAC-kontroll.</span><span class="sxs-lookup"><span data-stu-id="13f01-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="13f01-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) Det gick inte att skicka underliggande TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="13f01-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="13f01-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Ett inkommande meddelande hade ett fält med ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="13f01-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="13f01-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) Ett inkommande ChangeCipherSpec-meddelande var felaktigt.</span><span class="sxs-lookup"><span data-stu-id="13f01-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="13f01-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) Ett inkommande TLS-certifikat kan inte användas för att identifiera TLS-fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="13f01-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="13f01-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Chiffer med offentlig nyckel som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="13f01-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="13f01-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Fjärrvärden har inte angett några chiffer som stöds av NetX Secure TLS-stacken.</span><span class="sxs-lookup"><span data-stu-id="13f01-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="13f01-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget TLS-meddelande hade en okänd TLS-version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="13f01-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="13f01-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Ett mottaget TLS-meddelande hade en känd TLS-version som inte stöds i rubriken.</span><span class="sxs-lookup"><span data-stu-id="13f01-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="13f01-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) En intern TLS-paketallokering misslyckades.</span><span class="sxs-lookup"><span data-stu-id="13f01-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="13f01-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Fjärrvärden angav ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="13f01-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="13f01-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Fjärrvärden skickade en avisering som anger ett fel och avslutar TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="13f01-1830">**NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1831">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1831">Allowed From</span></span>

<span data-ttu-id="13f01-1832">Initiering, Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1833">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1833">Example</span></span>

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a><span data-ttu-id="13f01-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="13f01-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="13f01-1835">Starta HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="13f01-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1836">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-1837">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1837">Description</span></span>

<span data-ttu-id="13f01-1838">Den här tjänsten startar en http- eller HTTPS-serverinstans som skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="13f01-1839">HTTPS-servrar delar samma API som HTTP.</span><span class="sxs-lookup"><span data-stu-id="13f01-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="13f01-1840">Information om hur du aktiverar HTTPS med TLS på en HTTP-server finns *i nx_web_http_server_secure_configure().*</span><span class="sxs-lookup"><span data-stu-id="13f01-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1841">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1841">Input Parameters</span></span>

- <span data-ttu-id="13f01-1842">**http_server_ptr** Pekare till HTTP Server-instans.</span><span class="sxs-lookup"><span data-stu-id="13f01-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1843">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1843">Return Values</span></span>

- <span data-ttu-id="13f01-1844">**NX_SUCCESS** (0x00) Lyckad HTTP-serverstart</span><span class="sxs-lookup"><span data-stu-id="13f01-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="13f01-1845">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1846">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1846">Allowed From</span></span>

<span data-ttu-id="13f01-1847">Initiering, Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1848">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="13f01-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="13f01-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="13f01-1850">Stoppa HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="13f01-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1851">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="13f01-1852">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1852">Description</span></span>

<span data-ttu-id="13f01-1853">Den här tjänsten stoppar den http-serverinstans som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="13f01-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="13f01-1854">Den här rutinen bör anropas innan du tar bort en HTTP Server-instans.</span><span class="sxs-lookup"><span data-stu-id="13f01-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1855">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1855">Input Parameters</span></span>

- <span data-ttu-id="13f01-1856">**http_server_ptr** Pekare till HTTP Server-instans.</span><span class="sxs-lookup"><span data-stu-id="13f01-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1857">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1857">Return Values</span></span>

- <span data-ttu-id="13f01-1858">**NX_SUCCESS** (0x00) Lyckat HTTP-serverstopp</span><span class="sxs-lookup"><span data-stu-id="13f01-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="13f01-1859">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1860">NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="13f01-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1861">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1861">Allowed From</span></span>

<span data-ttu-id="13f01-1862">Trådar</span><span class="sxs-lookup"><span data-stu-id="13f01-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1863">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="13f01-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="13f01-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="13f01-1865">Extrahera filtyp från HTTP-klientbegäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1866">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1867">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="13f01-1868">Den här tjänsten är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="13f01-1868">This service is deprecated.</span></span> <span data-ttu-id="13f01-1869">Användarna uppmanas att använda tjänsten *nx_web_http_server_type_get_extended().*</span><span class="sxs-lookup"><span data-stu-id="13f01-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="13f01-1870">Den här tjänsten extraherar HTTP-begärandetypen *i bufferten http_type_string* och dess längd *i string_size* från namnet på indatabufferten , vanligtvis URL:en. </span><span class="sxs-lookup"><span data-stu-id="13f01-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="13f01-1871">Om ingen MIME-karta hittas används som standard typen "text/oformaterad".</span><span class="sxs-lookup"><span data-stu-id="13f01-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="13f01-1872">Annars jämförs den extraherade typen med HTTP-serverns standard-MIME-mappning för en matchning.</span><span class="sxs-lookup"><span data-stu-id="13f01-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="13f01-1873">MIME-standardmappningar i NetX Web HTTP Server är:</span><span class="sxs-lookup"><span data-stu-id="13f01-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="13f01-1874">html-text/html</span><span class="sxs-lookup"><span data-stu-id="13f01-1874">html text/html</span></span>
- <span data-ttu-id="13f01-1875">htm text/html</span><span class="sxs-lookup"><span data-stu-id="13f01-1875">htm text/html</span></span>
- <span data-ttu-id="13f01-1876">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="13f01-1876">txt text/plain</span></span>
- <span data-ttu-id="13f01-1877">gif-bild/gif</span><span class="sxs-lookup"><span data-stu-id="13f01-1877">gif image/gif</span></span>
- <span data-ttu-id="13f01-1878">jpg-bild/jpeg</span><span class="sxs-lookup"><span data-stu-id="13f01-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="13f01-1879">ico-bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="13f01-1879">ico image/x-icon</span></span>

<span data-ttu-id="13f01-1880">Om det anges söker den även efter en användardefinierad uppsättning ytterligare MIME-kartor.</span><span class="sxs-lookup"><span data-stu-id="13f01-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="13f01-1881">Se *nx_web_http_server_mime_maps_addtional_set() för* mer information om användardefinierade kartor.</span><span class="sxs-lookup"><span data-stu-id="13f01-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1882">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1882">Input Parameters</span></span>

- <span data-ttu-id="13f01-1883">**http_server_ptr** Pekare till HTTP Server-instans</span><span class="sxs-lookup"><span data-stu-id="13f01-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="13f01-1884">**namn** Pekare till buffert för sökning</span><span class="sxs-lookup"><span data-stu-id="13f01-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="13f01-1885">**http_type_string** Pekare till extraherad HTML-typsträng</span><span class="sxs-lookup"><span data-stu-id="13f01-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="13f01-1886">**string_size** Pekare för att returnera stränglängden för extraherad HTML-typ.</span><span class="sxs-lookup"><span data-stu-id="13f01-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1887">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1887">Return Values</span></span>

- <span data-ttu-id="13f01-1888">**NX_SUCCESS** (0x00) Lyckad extrahering av typen</span><span class="sxs-lookup"><span data-stu-id="13f01-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="13f01-1889">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Standardvärdet "text/oformaterad" returneras.</span><span class="sxs-lookup"><span data-stu-id="13f01-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1891">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1891">Allowed From</span></span>

<span data-ttu-id="13f01-1892">Program</span><span class="sxs-lookup"><span data-stu-id="13f01-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1893">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1893">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="13f01-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="13f01-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="13f01-1895">Extrahera filtyp från HTTP-klientbegäran</span><span class="sxs-lookup"><span data-stu-id="13f01-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1896">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="13f01-1897">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1897">Description</span></span>

<span data-ttu-id="13f01-1898">Den här tjänsten extraherar HTTP-begärandetypen *i bufferten http_type_string* och dess längd *i string_size* från namnet på indatabufferten , vanligtvis URL:en. </span><span class="sxs-lookup"><span data-stu-id="13f01-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="13f01-1899">Om ingen MIME-karta hittas används som standard typen "text/oformaterad".</span><span class="sxs-lookup"><span data-stu-id="13f01-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="13f01-1900">Annars jämförs den extraherade typen med HTTP-serverns standard-MIME-mappning för en matchning.</span><span class="sxs-lookup"><span data-stu-id="13f01-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="13f01-1901">MIME-standardmappningar i NetX Web HTTP Server är:</span><span class="sxs-lookup"><span data-stu-id="13f01-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="13f01-1902">html-text/html</span><span class="sxs-lookup"><span data-stu-id="13f01-1902">html text/html</span></span>
- <span data-ttu-id="13f01-1903">htm text/html</span><span class="sxs-lookup"><span data-stu-id="13f01-1903">htm text/html</span></span>
- <span data-ttu-id="13f01-1904">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="13f01-1904">txt text/plain</span></span>
- <span data-ttu-id="13f01-1905">gif-bild/gif</span><span class="sxs-lookup"><span data-stu-id="13f01-1905">gif image/gif</span></span>
- <span data-ttu-id="13f01-1906">jpg-bild/jpeg</span><span class="sxs-lookup"><span data-stu-id="13f01-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="13f01-1907">ico-bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="13f01-1907">ico image/x-icon</span></span>

<span data-ttu-id="13f01-1908">Om det anges söker den även efter en användardefinierad uppsättning ytterligare MIME-kartor.</span><span class="sxs-lookup"><span data-stu-id="13f01-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="13f01-1909">Se *nx_web_http_server_mime_maps_addtional_set() för* mer information om användardefinierade kartor.</span><span class="sxs-lookup"><span data-stu-id="13f01-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="13f01-1910">Den här tjänsten *ersätter nx_web_http_server_type_get*().</span><span class="sxs-lookup"><span data-stu-id="13f01-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="13f01-1911">Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.</span><span class="sxs-lookup"><span data-stu-id="13f01-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1912">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1912">Input Parameters</span></span>

- <span data-ttu-id="13f01-1913">**http_server_ptr** Pekare till HTTP Server-instans</span><span class="sxs-lookup"><span data-stu-id="13f01-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="13f01-1914">**namn** Pekare till buffert för sökning</span><span class="sxs-lookup"><span data-stu-id="13f01-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="13f01-1915">**name_length** Namnlängd</span><span class="sxs-lookup"><span data-stu-id="13f01-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="13f01-1916">**http_type_string** Pekare till extraherad HTML-typsträng</span><span class="sxs-lookup"><span data-stu-id="13f01-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="13f01-1917">**http_type_string_max_size** Storlek på http_type_string buffertstorlek</span><span class="sxs-lookup"><span data-stu-id="13f01-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="13f01-1918">**string_size** Pekare för att returnera extraherad HTML-typsträng</span><span class="sxs-lookup"><span data-stu-id="13f01-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="13f01-1919">Längd.</span><span class="sxs-lookup"><span data-stu-id="13f01-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1920">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1920">Return Values</span></span>

- <span data-ttu-id="13f01-1921">**NX_SUCCESS** (0x00) Lyckad extrahering av typen</span><span class="sxs-lookup"><span data-stu-id="13f01-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="13f01-1922">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Standardvärdet "text/oformaterad" returneras.</span><span class="sxs-lookup"><span data-stu-id="13f01-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1924">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1924">Allowed From</span></span>

<span data-ttu-id="13f01-1925">Program</span><span class="sxs-lookup"><span data-stu-id="13f01-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1926">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1926">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="13f01-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="13f01-1928">Ange sammanfattad funktion för att autentisera motringning</span><span class="sxs-lookup"><span data-stu-id="13f01-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1929">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1929">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a><span data-ttu-id="13f01-1930">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1930">Description</span></span>

<span data-ttu-id="13f01-1931">Den här tjänsten anger återanropet som anropas när sammanfattad autentisering utförs.</span><span class="sxs-lookup"><span data-stu-id="13f01-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1932">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1932">Input Parameters</span></span>

- <span data-ttu-id="13f01-1933">**http_server_ptr** Pekare till HTTP Server-instans</span><span class="sxs-lookup"><span data-stu-id="13f01-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="13f01-1934">**digest_authenticate_callback** Pekare för att sammanfatta autentisera återanrop</span><span class="sxs-lookup"><span data-stu-id="13f01-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1935">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1935">Return Values</span></span>

- <span data-ttu-id="13f01-1936">**NX_SUCCESS** (0x00) Ange återanropet</span><span class="sxs-lookup"><span data-stu-id="13f01-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="13f01-1937">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="13f01-1938">NX_NOT_SUPPORTED (0x4B) Sammanfattad autentisering är inte aktiverat</span><span class="sxs-lookup"><span data-stu-id="13f01-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1939">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1939">Allowed From</span></span>

<span data-ttu-id="13f01-1940">Program</span><span class="sxs-lookup"><span data-stu-id="13f01-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1941">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1941">Example</span></span>

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="13f01-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="13f01-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="13f01-1943">Ange sammanfattad funktion för att autentisera motringning</span><span class="sxs-lookup"><span data-stu-id="13f01-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="13f01-1944">Prototyp</span><span class="sxs-lookup"><span data-stu-id="13f01-1944">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a><span data-ttu-id="13f01-1945">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13f01-1945">Description</span></span>

<span data-ttu-id="13f01-1946">Den här tjänsten anger återanropet som anropas när autentiseringskontrollen utförs.</span><span class="sxs-lookup"><span data-stu-id="13f01-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13f01-1947">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="13f01-1947">Input Parameters</span></span>

- <span data-ttu-id="13f01-1948">**http_server_ptr** Pekare till HTTP Server-instans</span><span class="sxs-lookup"><span data-stu-id="13f01-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="13f01-1949">**authenticate_check_externded** Pekare för att autentisera check motringning</span><span class="sxs-lookup"><span data-stu-id="13f01-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="13f01-1950">Returvärden</span><span class="sxs-lookup"><span data-stu-id="13f01-1950">Return Values</span></span>

- <span data-ttu-id="13f01-1951">**NX_SUCCESS** (0x00) Ange återanropet</span><span class="sxs-lookup"><span data-stu-id="13f01-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="13f01-1952">NX_PTR_ERROR (0x07) Ogiltig pekare</span><span class="sxs-lookup"><span data-stu-id="13f01-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13f01-1953">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="13f01-1953">Allowed From</span></span>

<span data-ttu-id="13f01-1954">Program</span><span class="sxs-lookup"><span data-stu-id="13f01-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="13f01-1955">Exempel</span><span class="sxs-lookup"><span data-stu-id="13f01-1955">Example</span></span>

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
