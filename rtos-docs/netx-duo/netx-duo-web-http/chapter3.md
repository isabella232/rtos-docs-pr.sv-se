---
title: Kapitel 3 – Beskrivning av HTTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX-webb-HTTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30168ad5a564b0f4c0a8c999046c5103385f4f90
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826985"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="a927b-103">Kapitel 3 – Beskrivning av HTTP-tjänster</span><span class="sxs-lookup"><span data-stu-id="a927b-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="a927b-104">Det här kapitlet innehåller en beskrivning av alla NetX-webb-HTTP-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="a927b-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="a927b-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="a927b-106">API för HTTP-och HTTPS-klient</span><span class="sxs-lookup"><span data-stu-id="a927b-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="a927b-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="a927b-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="a927b-108">Öppna en klartext-socket till en HTTP-server för anpassade begär Anden</span><span class="sxs-lookup"><span data-stu-id="a927b-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-109">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-110">Description</span></span>

<span data-ttu-id="a927b-111">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-112">Den här tjänsten öppnar en TCP-socket i klartext till en HTTP-server, men skickar inga förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="a927b-113">Begär Anden skapas med n *x_web_http_client_request_initialize ()* och skickas med *nx_web_http_client_request_send ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="a927b-114">Anpassade HTTP-huvuden kan läggas till i begäran med hjälp av *nx_web_http_client_request_header_add ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="a927b-115">Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="a927b-116">**Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.**</span><span class="sxs-lookup"><span data-stu-id="a927b-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-117">Nx_web_http_client_ \* _start metoder tillhandahålls för bekvämlighet (t. ex. *nx_web_http_client_get_start*()) och hanterar genereringen av förfrågningar och socketanslutningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="a927b-118">Du kan använda dessa tjänster i stället för *nx_web_http_client_connect ()* och de relaterade rutinerna om du inte behöver anpassade HTTP-huvuden i dina begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-119">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-119">Input Parameters</span></span>

- <span data-ttu-id="a927b-120">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-121">**server_ip** IP-adress för fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="a927b-122">**SERVER_PORT** Port på fjärr-HTTP-server (t. ex. 80 för HTTP).</span><span class="sxs-lookup"><span data-stu-id="a927b-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="a927b-123">**wait_option** Definierar hur länge tjänsten ska vänta på underliggande nätverks åtgärder.</span><span class="sxs-lookup"><span data-stu-id="a927b-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="a927b-124">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-125">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-126">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-127">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-127">Return Values</span></span>

- <span data-ttu-id="a927b-128">**NX_SUCCESS** (0x00) anslutning av TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="a927b-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="a927b-129">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-130">NX_WEB_HTTP_NOT_READY (0x3000A) en annan begäran pågår redan.</span><span class="sxs-lookup"><span data-stu-id="a927b-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-131">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-131">Allowed From</span></span>

<span data-ttu-id="a927b-132">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-133">Example</span></span>

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
    "https://192.168.1.150/test.txt ",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="a927b-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="a927b-134">nx_web_http_client_create</span></span>

<span data-ttu-id="a927b-135">Skapa en HTTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="a927b-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-136">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="a927b-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-137">Description</span></span>

<span data-ttu-id="a927b-138">Den här tjänsten skapar en HTTP-klient instans på den angivna IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="a927b-139">Klient instansen kan användas för antingen HTTP eller HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a927b-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="a927b-140">Se tjänsterna *nx_web_http_client_connect ()* och *nx_web_http_client_secure_connect ()* för mer information om hur du startar en HTTP-eller https-instans.</span><span class="sxs-lookup"><span data-stu-id="a927b-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="a927b-141">Se även API: et för \* nx_web_http_client_get_ \* \*, \*nx_web_http_client_put_ \* *, *nx_web_http_client_post_** för enkla anrop av get-, get-och post-metoder.</span><span class="sxs-lookup"><span data-stu-id="a927b-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-142">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-142">Input Parameters</span></span>

- <span data-ttu-id="a927b-143">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-144">**client_name** Namn på HTTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="a927b-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="a927b-145">**ip_ptr** Pekare till IP-instans.</span><span class="sxs-lookup"><span data-stu-id="a927b-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="a927b-146">**pool_ptr** Pekare till standard paketets pool.</span><span class="sxs-lookup"><span data-stu-id="a927b-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="a927b-147">Observera att paketen i den här poolen måste ha en nytto last som är tillräckligt stor för att hantera hela svars huvudet.</span><span class="sxs-lookup"><span data-stu-id="a927b-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="a927b-148">Detta definieras av *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* i *nx_web_http_client. h*.</span><span class="sxs-lookup"><span data-stu-id="a927b-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="a927b-149">**window_size** Storlek på klientens mottagnings fönster för TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="a927b-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-150">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-150">Return Values</span></span>

- <span data-ttu-id="a927b-151">**NX_SUCCESS** (0X00) http-klienten har skapats</span><span class="sxs-lookup"><span data-stu-id="a927b-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="a927b-152">NX_PTR_ERROR (0x16) ogiltig pekare för HTTP, ip_ptr eller Packet pool</span><span class="sxs-lookup"><span data-stu-id="a927b-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="a927b-153">NX_WEB_HTTP_POOL_ERROR (0x30009) ogiltig nytto Last storlek i Packet bassäng</span><span class="sxs-lookup"><span data-stu-id="a927b-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-154">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-154">Allowed From</span></span>

<span data-ttu-id="a927b-155">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a927b-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-156">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="a927b-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="a927b-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="a927b-158">Ta bort en HTTP-klient instans</span><span class="sxs-lookup"><span data-stu-id="a927b-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-159">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-160">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-160">Description</span></span>

<span data-ttu-id="a927b-161">Den här tjänsten tar bort en tidigare skapad HTTP-klient instans.</span><span class="sxs-lookup"><span data-stu-id="a927b-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-162">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-162">Input Parameters</span></span>

- <span data-ttu-id="a927b-163">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-164">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-164">Return Values</span></span>

- <span data-ttu-id="a927b-165">**NX_SUCCESS** (0X00) http-klientbegäran har tagits bort</span><span class="sxs-lookup"><span data-stu-id="a927b-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="a927b-166">NX_PTR_ERROR (0x16) ogiltig HTTP-pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="a927b-167">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-168">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-168">Allowed From</span></span>

<span data-ttu-id="a927b-169">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-170">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="a927b-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="a927b-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="a927b-172">Starta en HTTP DELETE-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="a927b-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-173">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-174">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-174">Description</span></span>

<span data-ttu-id="a927b-175">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-176">Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-177">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="a927b-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a927b-178">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-179">Detta API är föråldrat.</span><span class="sxs-lookup"><span data-stu-id="a927b-179">This API is deprecated.</span></span> <span data-ttu-id="a927b-180">Utvecklare uppmanas att använda *nx_web_http_client_delete_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-181">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-181">Input Parameters</span></span>

- <span data-ttu-id="a927b-182">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-183">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-184">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-185">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-186">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-187">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-188">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-189">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-190">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-191">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-192">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-193">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-194">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-195">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-195">Return Values</span></span>

- <span data-ttu-id="a927b-196">**NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan</span><span class="sxs-lookup"><span data-stu-id="a927b-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a927b-197">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-198">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-199">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-201">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-202">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-203">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-203">Allowed From</span></span>

<span data-ttu-id="a927b-204">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-205">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-205">Example</span></span>

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

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="a927b-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="a927b-207">Starta en HTTP DELETE-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="a927b-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-208">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-209">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-209">Description</span></span>

<span data-ttu-id="a927b-210">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-211">Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-212">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="a927b-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a927b-213">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-214">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-terminerade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-215">Den här tjänsten ersätter *nx_web_http_client_delete_start* ().</span><span class="sxs-lookup"><span data-stu-id="a927b-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="a927b-216">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-217">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-217">Input Parameters</span></span>

- <span data-ttu-id="a927b-218">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-219">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-220">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-221">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-222">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-223">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-224">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-225">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-226">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-227">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-228">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-229">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-230">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-231">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-232">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-233">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-234">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-235">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-235">Return Values</span></span>

- <span data-ttu-id="a927b-236">**NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan</span><span class="sxs-lookup"><span data-stu-id="a927b-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a927b-237">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-238">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-239">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-241">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-242">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-243">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-243">Allowed From</span></span>

<span data-ttu-id="a927b-244">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-245">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-245">Example</span></span>

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

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="a927b-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="a927b-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="a927b-247">Starta en krypterad HTTPS DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-248">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-249">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-249">Description</span></span>

<span data-ttu-id="a927b-250">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-251">Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-252">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="a927b-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a927b-253">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-254">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-254">This service is deprecated.</span></span> <span data-ttu-id="a927b-255">Utvecklare uppmanas att använda *nx_web_http_client_delete_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-256">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-256">Input Parameters</span></span>

- <span data-ttu-id="a927b-257">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-258">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-259">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-260">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="a927b-261">resursen måste vara NULL-terminerad.</span><span class="sxs-lookup"><span data-stu-id="a927b-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="a927b-262">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-263">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-264">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-265">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-266">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-267">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-268">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-269">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-270">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-271">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-272">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-273">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-273">Return Values</span></span>

- <span data-ttu-id="a927b-274">**NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan</span><span class="sxs-lookup"><span data-stu-id="a927b-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a927b-275">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-276">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-277">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-279">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-280">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-281">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-281">Allowed From</span></span>

<span data-ttu-id="a927b-282">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-283">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-283">Example</span></span>

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

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="a927b-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="a927b-285">Starta en krypterad HTTPS DELETE-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-286">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-286">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-287">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-287">Description</span></span>

<span data-ttu-id="a927b-288">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-289">Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-290">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.</span><span class="sxs-lookup"><span data-stu-id="a927b-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="a927b-291">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-292">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-293">Den här tjänsten ersätter *nx_web_http_client_delete_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a927b-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="a927b-294">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-295">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-295">Input Parameters</span></span>

- <span data-ttu-id="a927b-296">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-297">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-298">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-299">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="a927b-300">resursen måste vara NULL-terminerad.</span><span class="sxs-lookup"><span data-stu-id="a927b-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="a927b-301">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-302">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-303">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-304">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-305">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-306">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-307">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-308">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-309">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-310">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-311">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-312">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-313">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-314">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-315">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-316">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-316">Return Values</span></span>

- <span data-ttu-id="a927b-317">**NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan</span><span class="sxs-lookup"><span data-stu-id="a927b-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="a927b-318">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-319">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-320">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-322">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-323">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a927b-324">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-324">Allowed From</span></span>

<span data-ttu-id="a927b-325">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-326">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-326">Example</span></span>

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

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="a927b-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="a927b-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="a927b-328">Starta en HTTP GET-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="a927b-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-329">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-330">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-330">Description</span></span>

<span data-ttu-id="a927b-331">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-332">Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-333">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a927b-334">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-335">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-335">This service is deprecated.</span></span> <span data-ttu-id="a927b-336">Utvecklare uppmanas att använda *nx_web_http_client_get_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-337">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-337">Input Parameters</span></span>

- <span data-ttu-id="a927b-338">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-339">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-340">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-341">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-342">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-343">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-344">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-345">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-346">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-347">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-348">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-349">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-350">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-351">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-351">Return Values</span></span>

- <span data-ttu-id="a927b-352">**NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a927b-353">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-354">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-355">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-357">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-358">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-359">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-359">Allowed From</span></span>

<span data-ttu-id="a927b-360">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-361">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-361">Example</span></span>

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

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="a927b-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="a927b-363">Starta en HTTP GET-begäran i klartext</span><span class="sxs-lookup"><span data-stu-id="a927b-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-364">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-365">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-365">Description</span></span>

<span data-ttu-id="a927b-366">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-367">Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-368">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a927b-369">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-370">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-terminerade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-371">Den här tjänsten ersätter *nx_web_http_client_get_start*().</span><span class="sxs-lookup"><span data-stu-id="a927b-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="a927b-372">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-373">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-373">Input Parameters</span></span>

- <span data-ttu-id="a927b-374">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-375">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-376">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-377">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-378">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-379">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-380">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-381">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-382">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-383">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-384">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-385">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-386">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-387">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-388">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-389">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-390">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-391">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-391">Return Values</span></span>

- <span data-ttu-id="a927b-392">**NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a927b-393">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-394">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-395">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-397">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-398">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-399">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-399">Allowed From</span></span>

<span data-ttu-id="a927b-400">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-401">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-401">Example</span></span>

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

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="a927b-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="a927b-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="a927b-403">Starta en krypterad HTTPS GET-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-404">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-405">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-405">Description</span></span>

<span data-ttu-id="a927b-406">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-407">Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-408">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a927b-409">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-410">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-410">This service is deprecated.</span></span> <span data-ttu-id="a927b-411">Utvecklare uppmanas att använda *nx_web_http_client_get_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-412">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-412">Input Parameters</span></span>

- <span data-ttu-id="a927b-413">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-414">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-415">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-416">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-417">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-418">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-419">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-420">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-421">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-422">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-423">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-424">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-425">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-426">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-427">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-428">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-428">Return Values</span></span>

- <span data-ttu-id="a927b-429">**NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a927b-430">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-431">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-432">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-434">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-435">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-436">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-436">Allowed From</span></span>

<span data-ttu-id="a927b-437">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-438">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-438">Example</span></span>

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

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="a927b-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="a927b-440">Starta en krypterad HTTPS GET-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-441">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-441">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-442">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-442">Description</span></span>

<span data-ttu-id="a927b-443">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-444">Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-445">Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="a927b-446">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-447">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-terminerade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-448">Den här tjänsten ersätter *nx_web_http_client_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a927b-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="a927b-449">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-450">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-450">Input Parameters</span></span>

- <span data-ttu-id="a927b-451">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-452">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-453">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-454">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-455">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-456">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-457">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-458">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-459">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-460">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-461">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-462">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-463">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-464">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-465">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-466">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-467">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-468">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-469">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-470">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-470">Return Values</span></span>

- <span data-ttu-id="a927b-471">**NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="a927b-472">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-473">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-474">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-476">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-477">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-478">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-478">Allowed From</span></span>

<span data-ttu-id="a927b-479">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-480">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-480">Example</span></span>

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

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="a927b-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="a927b-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="a927b-482">Starta en HTTP HEAD-begäran med oformaterad text</span><span class="sxs-lookup"><span data-stu-id="a927b-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-483">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-484">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-484">Description</span></span>

<span data-ttu-id="a927b-485">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-486">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-487">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="a927b-488">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-489">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-489">This service is deprecated.</span></span> <span data-ttu-id="a927b-490">Utvecklare uppmanas att använda *nx_web_http_client_head_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-491">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-491">Input Parameters</span></span>

- <span data-ttu-id="a927b-492">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-493">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-494">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-495">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-496">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-497">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-498">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-499">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-500">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-501">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-502">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-503">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-504">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-505">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-505">Return Values</span></span>

- <span data-ttu-id="a927b-506">**NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a927b-507">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-508">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-509">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-511">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-512">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-513">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-513">Allowed From</span></span>

<span data-ttu-id="a927b-514">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-515">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-515">Example</span></span>

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

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="a927b-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="a927b-517">Starta en HTTP HEAD-begäran med oformaterad text</span><span class="sxs-lookup"><span data-stu-id="a927b-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-518">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-519">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-519">Description</span></span>

<span data-ttu-id="a927b-520">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-521">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-522">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="a927b-523">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-524">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-525">Den här tjänsten ersätter *nx_web_http_client_head_start*().</span><span class="sxs-lookup"><span data-stu-id="a927b-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="a927b-526">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-527">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-527">Input Parameters</span></span>

- <span data-ttu-id="a927b-528">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-529">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-530">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-531">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-532">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-533">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-534">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-535">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-536">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-537">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-538">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-539">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-540">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-541">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-542">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-543">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-544">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-545">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-545">Return Values</span></span>

- <span data-ttu-id="a927b-546">**NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a927b-547">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-548">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-549">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-551">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-552">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-553">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-553">Allowed From</span></span>

<span data-ttu-id="a927b-554">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-555">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-555">Example</span></span>

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

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="a927b-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="a927b-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="a927b-557">Starta en krypterad HTTPS HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-558">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-559">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-559">Description</span></span>

<span data-ttu-id="a927b-560">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-561">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-562">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="a927b-563">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-564">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-564">This service is deprecated.</span></span> <span data-ttu-id="a927b-565">Utvecklare uppmanas att använda *nx_web_http_client_head_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-566">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-566">Input Parameters</span></span>

- <span data-ttu-id="a927b-567">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-568">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-569">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-570">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-571">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-572">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-573">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-574">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-575">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-576">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-577">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-578">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-579">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-580">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-581">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-582">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-582">Return Values</span></span>

- <span data-ttu-id="a927b-583">**NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a927b-584">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-585">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-586">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-588">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-589">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-590">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-590">Allowed From</span></span>

<span data-ttu-id="a927b-591">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-592">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-592">Example</span></span>

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

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="a927b-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="a927b-594">Starta en krypterad HTTPS HEAD-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-595">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-595">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-596">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-596">Description</span></span>

<span data-ttu-id="a927b-597">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-598">Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="a927b-599">Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar som motsvarar det begärda resurs innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="a927b-600">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="a927b-601">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-602">Den här tjänsten ersätter *nx_web_http_client_head_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a927b-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="a927b-603">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-604">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-604">Input Parameters</span></span>

- <span data-ttu-id="a927b-605">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-606">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-607">**SERVER_PORT** Port på fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-608">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-609">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-610">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-611">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-612">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-613">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-614">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-615">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-616">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-617">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-618">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-619">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-620">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-621">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-622">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-623">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-624">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-624">Return Values</span></span>

- <span data-ttu-id="a927b-625">**NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats</span><span class="sxs-lookup"><span data-stu-id="a927b-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="a927b-626">**NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel</span><span class="sxs-lookup"><span data-stu-id="a927b-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="a927b-627">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-628">**NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="a927b-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a927b-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="a927b-630">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-631">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-632">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-632">Allowed From</span></span>

<span data-ttu-id="a927b-633">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-634">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-634">Example</span></span>

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

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="a927b-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a927b-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="a927b-636">Allokera ett HTTP (S)-paket</span><span class="sxs-lookup"><span data-stu-id="a927b-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-637">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-638">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-638">Description</span></span>

<span data-ttu-id="a927b-639">Den här tjänsten försöker allokera ett paket för klient-HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="a927b-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-640">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-640">Input Parameters</span></span>

- <span data-ttu-id="a927b-641">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-642">**packet_ptr** Pekare till allokerat paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="a927b-643">**wait_option** Definierar vänte tiden i Tick om det inte finns några tillgängliga paket i modempoolen.</span><span class="sxs-lookup"><span data-stu-id="a927b-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="a927b-644">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a927b-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="a927b-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a927b-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="a927b-647">**timeout i Tick** (0X00000001 till 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a927b-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-648">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-648">Return Values</span></span>

- <span data-ttu-id="a927b-649">**NX_SUCCESS** (0x00) paket tilldelningen lyckades</span><span class="sxs-lookup"><span data-stu-id="a927b-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="a927b-650">**NX_NO_PACKET** (0X01) inget tillgängligt paket</span><span class="sxs-lookup"><span data-stu-id="a927b-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="a927b-651">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="a927b-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="a927b-652">**NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.</span><span class="sxs-lookup"><span data-stu-id="a927b-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="a927b-653">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-654">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-655">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-655">Allowed From</span></span>

<span data-ttu-id="a927b-656">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-657">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="a927b-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="a927b-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="a927b-659">Starta en HTTP POST-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-660">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-661">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-661">Description</span></span>

<span data-ttu-id="a927b-662">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-663">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-664">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet* rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-665">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-666">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-666">This service is deprecated.</span></span> <span data-ttu-id="a927b-667">Utvecklare uppmanas att använda *nx_web_http_client_post_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-668">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-668">Input Parameters</span></span>

- <span data-ttu-id="a927b-669">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-670">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-671">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-672">**resurs** Pekare till URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a927b-673">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-674">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-675">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-676">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-677">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-678">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-679">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-680">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-681">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-682">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-683">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-684">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-684">Return Values</span></span>

- <span data-ttu-id="a927b-685">**NX_SUCCESS** (0X00) har skickat post-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a927b-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-687">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-688">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-689">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-690">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-691">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-691">Allowed From</span></span>

<span data-ttu-id="a927b-692">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-693">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-693">Example</span></span>

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

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="a927b-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="a927b-695">Starta en HTTP POST-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-696">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-697">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-697">Description</span></span>

<span data-ttu-id="a927b-698">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-699">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-700">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet* rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-701">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-702">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-703">Den här tjänsten ersätter *nx_web_http_client_post_start* ().</span><span class="sxs-lookup"><span data-stu-id="a927b-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="a927b-704">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-705">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-705">Input Parameters</span></span>

- <span data-ttu-id="a927b-706">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-707">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-708">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-709">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-710">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-711">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-712">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-713">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-714">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-715">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-716">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-717">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-718">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-719">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-720">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-721">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-722">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-723">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-724">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-725">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-725">Return Values</span></span>

- <span data-ttu-id="a927b-726">**NX_SUCCESS** (0X00) har skickat post-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a927b-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-728">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-729">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-730">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-731">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-732">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-732">Allowed From</span></span>

<span data-ttu-id="a927b-733">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-734">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-734">Example</span></span>

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

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="a927b-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="a927b-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="a927b-736">Starta en krypterad HTTPS POST-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-737">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-737">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-738">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-738">Description</span></span>

<span data-ttu-id="a927b-739">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-740">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-741">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-742">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-743">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-743">This service is deprecated.</span></span> <span data-ttu-id="a927b-744">Utvecklare uppmanas att använda *nx_web_http_client_post_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-745">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-745">Input Parameters</span></span>

- <span data-ttu-id="a927b-746">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-747">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-748">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-749">**resurs** Pekare till URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a927b-750">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-751">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-752">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-753">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-754">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-755">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-756">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-757">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-758">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-759">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-760">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-761">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-762">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-763">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-763">Return Values</span></span>

- <span data-ttu-id="a927b-764">**NX_SUCCESS** (0X00) har skickat post-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a927b-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-766">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-767">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-768">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-769">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-770">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-770">Allowed From</span></span>

<span data-ttu-id="a927b-771">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-772">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-772">Example</span></span>

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

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="a927b-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="a927b-774">Starta en krypterad HTTPS POST-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-775">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-775">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-776">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-776">Description</span></span>

<span data-ttu-id="a927b-777">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-778">Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-779">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-780">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-781">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-782">Den här tjänsten ersätter *nx_web_http_client_post_secure_start* ().</span><span class="sxs-lookup"><span data-stu-id="a927b-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="a927b-783">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-784">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-784">Input Parameters</span></span>

- <span data-ttu-id="a927b-785">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-786">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-787">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-788">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-789">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-790">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-791">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-792">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-793">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-794">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-795">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-796">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-797">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-798">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-799">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-800">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-801">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-802">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-803">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-804">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-805">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-806">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-806">Return Values</span></span>

- <span data-ttu-id="a927b-807">**NX_SUCCESS** (0X00) har skickat post-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="a927b-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-809">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-810">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-811">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-812">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-813">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-813">Allowed From</span></span>

<span data-ttu-id="a927b-814">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-815">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-815">Example</span></span>

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

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="a927b-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="a927b-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="a927b-817">Starta en HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-818">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-819">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-819">Description</span></span>

<span data-ttu-id="a927b-820">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-821">Tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-822">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-823">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-824">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-824">This service is deprecated.</span></span> <span data-ttu-id="a927b-825">Utvecklare uppmanas att använda *nx_web_http_client_put_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-826">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-826">Input Parameters</span></span>

- <span data-ttu-id="a927b-827">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-828">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-829">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-830">**resurs** Pekare till URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a927b-831">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-832">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-833">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-834">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-835">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-836">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-837">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-838">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-839">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-840">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-841">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-842">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-842">Return Values</span></span>

- <span data-ttu-id="a927b-843">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="a927b-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a927b-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-845">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-846">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-847">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-848">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-849">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-849">Allowed From</span></span>

<span data-ttu-id="a927b-850">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-851">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-851">Example</span></span>

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

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="a927b-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="a927b-853">Starta en HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-854">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-855">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-855">Description</span></span>

<span data-ttu-id="a927b-856">Den här metoden är för http med **oformaterad text** .</span><span class="sxs-lookup"><span data-stu-id="a927b-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="a927b-857">Tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-858">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-859">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-860">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-861">Den här tjänsten ersätter *nx_web_http_client_put_start* ().</span><span class="sxs-lookup"><span data-stu-id="a927b-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="a927b-862">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-863">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-863">Input Parameters</span></span>

- <span data-ttu-id="a927b-864">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-865">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-866">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-867">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-868">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-869">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-870">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-871">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-872">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-873">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-874">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-875">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-876">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-877">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-878">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-879">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-880">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-881">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-882">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-883">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-883">Return Values</span></span>

- <span data-ttu-id="a927b-884">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="a927b-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a927b-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-886">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-887">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-888">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-889">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-890">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-890">Allowed From</span></span>

<span data-ttu-id="a927b-891">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-892">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-892">Example</span></span>

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

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="a927b-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="a927b-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="a927b-894">Starta en krypterad HTTPS-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-895">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-895">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-896">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-896">Description</span></span>

<span data-ttu-id="a927b-897">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-898">Den här tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-899">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-900">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-901">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-901">This service is deprecated.</span></span> <span data-ttu-id="a927b-902">Utvecklare uppmanas att använda *nx_web_http_client_put_secure_start_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-903">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-903">Input Parameters</span></span>

- <span data-ttu-id="a927b-904">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-905">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-906">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-907">**resurs** Pekare till URL-sträng för resurs som ska skickas till servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="a927b-908">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-909">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-910">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-911">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-912">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-913">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-914">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-915">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-916">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-917">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-918">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-919">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-920">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-921">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-921">Return Values</span></span>

- <span data-ttu-id="a927b-922">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="a927b-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a927b-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-924">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-925">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-926">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-927">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-928">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-928">Allowed From</span></span>

<span data-ttu-id="a927b-929">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-930">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-930">Example</span></span>

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

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="a927b-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="a927b-932">Starta en krypterad HTTPS-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-933">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-933">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-934">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-934">Description</span></span>

<span data-ttu-id="a927b-935">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-936">Den här tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten.</span><span class="sxs-lookup"><span data-stu-id="a927b-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="a927b-937">Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="a927b-938">Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="a927b-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="a927b-939">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-940">Den här tjänsten ersätter *nx_web_http_client_put_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="a927b-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="a927b-941">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-942">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-942">Input Parameters</span></span>

- <span data-ttu-id="a927b-943">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-944">**ip_address** IP-adressen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="a927b-945">**SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="a927b-946">**resurs** Pekare till URL-sträng för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="a927b-947">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-948">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-949">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-950">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-951">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-952">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-953">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-954">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-955">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-956">**total_bytes** Totalt antal byte som skickas av resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="a927b-957">Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.</span><span class="sxs-lookup"><span data-stu-id="a927b-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="a927b-958">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-959">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-960">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-961">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-962">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-963">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-964">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-964">Return Values</span></span>

- <span data-ttu-id="a927b-965">**NX_SUCCESS** (0X00) har skickat begäran om att skicka</span><span class="sxs-lookup"><span data-stu-id="a927b-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="a927b-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="a927b-967">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-968">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-969">NX_SIZE_ERROR (0x09) ogiltig total resurs storlek</span><span class="sxs-lookup"><span data-stu-id="a927b-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="a927b-970">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-971">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-971">Allowed From</span></span>

<span data-ttu-id="a927b-972">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-973">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-973">Example</span></span>

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

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="a927b-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="a927b-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="a927b-975">Skicka nästa resurs data paket</span><span class="sxs-lookup"><span data-stu-id="a927b-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-976">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-977">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-977">Description</span></span>

<span data-ttu-id="a927b-978">Den här tjänsten försöker skicka nästa paket med resurs innehåll till HTTP-servern för både åtgärderna placera och publicera.</span><span class="sxs-lookup"><span data-stu-id="a927b-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="a927b-979">Observera att den här rutinen ska anropas upprepade gånger tills den kombinerade längden på de paket som skickas är lika med "total_bytes" som anges i föregående *nx_web_http_client_put_start ()* eller *nx_web_http_client_post_start ()* -anrop (eller motsvarande säkra versioner).</span><span class="sxs-lookup"><span data-stu-id="a927b-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="a927b-980">Tjänsten söker också efter ett svar från servern om det uppstod ett problem med att upprätta en HTTP-anslutning (eller HTTPS).</span><span class="sxs-lookup"><span data-stu-id="a927b-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-981">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-981">Input Parameters</span></span>

- <span data-ttu-id="a927b-982">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-983">**packet_ptr** Pekare till nästa innehåll i resursen som ska skickas till HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="a927b-984">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-985">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-986">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-987">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-988">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-988">Return Values</span></span>

- <span data-ttu-id="a927b-989">**NX_SUCCESS** (0x00) skickade http-klient paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="a927b-990">**NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar</span><span class="sxs-lookup"><span data-stu-id="a927b-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="a927b-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0X3000E) tog emot Server fel kod \* \*</span><span class="sxs-lookup"><span data-stu-id="a927b-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="a927b-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) ogiltig paket längd</span><span class="sxs-lookup"><span data-stu-id="a927b-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="a927b-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord</span><span class="sxs-lookup"><span data-stu-id="a927b-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="a927b-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** -servern (0x3000F) svarar innan den har slutförts</span><span class="sxs-lookup"><span data-stu-id="a927b-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="a927b-995">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-996">NX_INVALID_PACKET-paketet (0x12) är för litet för TCP-huvud</span><span class="sxs-lookup"><span data-stu-id="a927b-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="a927b-997">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-998">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-998">Allowed From</span></span>

<span data-ttu-id="a927b-999">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1000">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="a927b-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="a927b-1002">Ange segmenterad överföring för HTTP (S)-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1003">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-1004">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1004">Description</span></span>

<span data-ttu-id="a927b-1005">Den här tjänsten använder Chunked Transfer-kodning för att skicka en anpassad HTTP (S)-begäran till den server som anges i det *nx_web_http_client_connect ()* eller *nx_web_http_client_secure_connect ()* -anropet som tidigare har upprättat socket-anslutningen till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1006">Om programmet använder Chunked Transfer-kodning för att skicka ett data paket för begäran, måste det anropa tjänsten efter att ha anropat *nx_web_http_client_request_packet_allocate*() och innan anrop *nx_web_http_client_reqeust_packet_send* ().</span><span class="sxs-lookup"><span data-stu-id="a927b-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1007">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1007">Input Parameters</span></span>

- <span data-ttu-id="a927b-1008">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1009">**chunk_size** Storlek på segment data i oktetter.</span><span class="sxs-lookup"><span data-stu-id="a927b-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="a927b-1010">**packet_ptr** HTTP (a) begär data pakets pekare.</span><span class="sxs-lookup"><span data-stu-id="a927b-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1011">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1011">Return Values</span></span>

- <span data-ttu-id="a927b-1012">Ett segment har angetts för **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a927b-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="a927b-1013">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1014">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1014">Allowed From</span></span>

<span data-ttu-id="a927b-1015">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1016">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT, "https://192.168.1.150/test.txt ",
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

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="a927b-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="a927b-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="a927b-1018">Lägg till en anpassad rubrik i en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1019">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1020">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1020">Description</span></span>

<span data-ttu-id="a927b-1021">Den här tjänsten lägger till en anpassad rubrik (i form av ett fält namn och värde) till en anpassad HTTP-begäran som skapats med n *x_web_http_client_request_initialize ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="a927b-1022">Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="a927b-1023">**Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.**</span><span class="sxs-lookup"><span data-stu-id="a927b-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1024">Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="a927b-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a927b-1025">Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize ())* för att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1026">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1026">Input Parameters</span></span>

- <span data-ttu-id="a927b-1027">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1028">**field_name** Fält namn sträng (t. ex. "innehålls typ").</span><span class="sxs-lookup"><span data-stu-id="a927b-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="a927b-1029">**name_length** Längd på fält namn sträng i byte.</span><span class="sxs-lookup"><span data-stu-id="a927b-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="a927b-1030">**field_value** Fält värde sträng (t. ex. "Application/oktett-Stream").</span><span class="sxs-lookup"><span data-stu-id="a927b-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="a927b-1031">**value_length** Värde strängens längd i byte.</span><span class="sxs-lookup"><span data-stu-id="a927b-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="a927b-1032">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-1033">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1034">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-1035">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1036">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1036">Return Values</span></span>

- <span data-ttu-id="a927b-1037">**NX_SUCCESS** (0x00) addition av sidhuvud att begära.</span><span class="sxs-lookup"><span data-stu-id="a927b-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="a927b-1038">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1039">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1039">Allowed From</span></span>

<span data-ttu-id="a927b-1040">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1041">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
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
    until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="a927b-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="a927b-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="a927b-1043">Initiera en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1044">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1045">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1045">Description</span></span>

<span data-ttu-id="a927b-1046">Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klient instansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="a927b-1047">Till skillnad från de enklare *nx_web_http_client_get_start ()* (tillsammans med metoderna för att skicka, publicera och associerade säkra versioner av dessa API: er) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send ()* har anropats.</span><span class="sxs-lookup"><span data-stu-id="a927b-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="a927b-1048">Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran med hjälp av tjänsten ***nx_web_http_client_request_header_add ()*** .</span><span class="sxs-lookup"><span data-stu-id="a927b-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="a927b-1049">Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.</span><span class="sxs-lookup"><span data-stu-id="a927b-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1050">Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="a927b-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a927b-1051">Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_send ())* för att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="a927b-1052">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-1052">This service is deprecated.</span></span> <span data-ttu-id="a927b-1053">Utvecklare uppmanas att använda *nx_web_http_client_request_initialize_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1054">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1054">Input Parameters</span></span>

- <span data-ttu-id="a927b-1055">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1056">**metod** Den HTTP-metod för begäran som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a927b-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="a927b-1057">Alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="a927b-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="a927b-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="a927b-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="a927b-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="a927b-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="a927b-1064">**resurs** Namnet på den resurs som överförs.</span><span class="sxs-lookup"><span data-stu-id="a927b-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="a927b-1065">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-1066">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-1067">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-1068">**input_size** Storlek på indata för skicka och publicera.</span><span class="sxs-lookup"><span data-stu-id="a927b-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="a927b-1069">Pass 0 för andra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="a927b-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="a927b-1070">**transfer_encoding_trunked** Reserverad parameter för framtida Trunked transfer-stöd.</span><span class="sxs-lookup"><span data-stu-id="a927b-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="a927b-1071">**användar namn** Användar namn för skyddade resurser.</span><span class="sxs-lookup"><span data-stu-id="a927b-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="a927b-1072">**lösen ord** Lösen ord för skyddade resurser.</span><span class="sxs-lookup"><span data-stu-id="a927b-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="a927b-1073">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-1074">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1075">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-1076">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1077">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1077">Return Values</span></span>

- <span data-ttu-id="a927b-1078">**NX_SUCCESS** (0X00) slutförde initieringen av begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="a927b-1079">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) viss nödvändig information saknades (t. ex. input_size för placering eller POST).</span><span class="sxs-lookup"><span data-stu-id="a927b-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1081">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1081">Allowed From</span></span>

<span data-ttu-id="a927b-1082">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1083">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1083">Example</span></span>

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="a927b-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="a927b-1085">Initiera en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1086">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1087">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1087">Description</span></span>

<span data-ttu-id="a927b-1088">Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klient instansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="a927b-1089">Till skillnad från de enklare *nx_web_http_client_get_start ()* (tillsammans med metoderna för att skicka, publicera och associerade säkra versioner av dessa API: er) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send ()* har anropats.</span><span class="sxs-lookup"><span data-stu-id="a927b-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="a927b-1090">Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran med hjälp av tjänsten ***nx_web_http_client_request_header_add ()*** .</span><span class="sxs-lookup"><span data-stu-id="a927b-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="a927b-1091">Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.</span><span class="sxs-lookup"><span data-stu-id="a927b-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1092">Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="a927b-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a927b-1093">Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_send ())* för att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="a927b-1094">Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-1095">Den här tjänsten ersätter *nx_web_http_client_request_initialize*().</span><span class="sxs-lookup"><span data-stu-id="a927b-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="a927b-1096">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1097">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1097">Input Parameters</span></span>

- <span data-ttu-id="a927b-1098">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1099">**metod** Den HTTP-metod för begäran som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a927b-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="a927b-1100">Alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="a927b-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="a927b-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="a927b-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="a927b-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="a927b-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="a927b-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="a927b-1107">**resurs** Namnet på den resurs som överförs.</span><span class="sxs-lookup"><span data-stu-id="a927b-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="a927b-1108">**resource_length** Sträng längd för den begärda resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="a927b-1109">**värd** Null-avslutad sträng för serverns domän namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="a927b-1110">Den här strängen överförs i fältet HTTP-värd huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="a927b-1111">Värd strängen får inte vara NULL.</span><span class="sxs-lookup"><span data-stu-id="a927b-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="a927b-1112">**host_length** Värdens sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="a927b-1113">**input_size** Storlek på indata för skicka och publicera.</span><span class="sxs-lookup"><span data-stu-id="a927b-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="a927b-1114">Pass 0 för andra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="a927b-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="a927b-1115">**transfer_encoding_trunked** Reserverad parameter för framtida Trunked transfer-stöd.</span><span class="sxs-lookup"><span data-stu-id="a927b-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="a927b-1116">**användar namn** Pekare till valfritt användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="a927b-1117">**username_length** Sträng längd för användar namn för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="a927b-1118">**lösen ord** Pekare till valfritt lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="a927b-1119">**password_length** Sträng längden för lösen ord för autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="a927b-1120">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-1121">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1122">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-1123">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1124">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1124">Return Values</span></span>

- <span data-ttu-id="a927b-1125">**NX_SUCCESS** (0X00) slutförde initieringen av begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="a927b-1126">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) viss nödvändig information saknades (t. ex. input_size för placering eller POST).</span><span class="sxs-lookup"><span data-stu-id="a927b-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1128">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1128">Allowed From</span></span>

<span data-ttu-id="a927b-1129">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1130">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1130">Example</span></span>

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="a927b-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="a927b-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="a927b-1132">Skicka HTTP (S)-begäran om data paket till fjärrservern</span><span class="sxs-lookup"><span data-stu-id="a927b-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1133">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1134">Description</span></span>

<span data-ttu-id="a927b-1135">Den här tjänsten skickar ett anpassat HTTP (S)-begär ande data paket som skapats med *nx_web_http_client_request_packet_allocate* () till den server som anges i *nx_web_http_client_connect ()* eller *nx_web_http_client_secure_connect (*)-anropet som tidigare har upprättat socket-anslutningen till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1136">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1136">Input Parameters</span></span>

- <span data-ttu-id="a927b-1137">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1138">**packet_ptr** HTTP (a) begär data pakets pekare.</span><span class="sxs-lookup"><span data-stu-id="a927b-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="a927b-1139">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-1140">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1141">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-1142">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1143">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1143">Return Values</span></span>

- <span data-ttu-id="a927b-1144">**NX_SUCCESS** (0x00) skickade data paket för begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="a927b-1145">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1146">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1146">Allowed From</span></span>

<span data-ttu-id="a927b-1147">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1148">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ",
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

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="a927b-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="a927b-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="a927b-1150">Skicka en anpassad HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1152">Description</span></span>

<span data-ttu-id="a927b-1153">Den här tjänsten skickar en anpassad HTTP-begäran som skapats med *nx_web_http_client_request_initialize ()* till den server som anges i *nx_web_http_client_connect ()* eller *nx_web_http_client_secure_connect ()* som tidigare har upprättat socket-anslutningen till fjärrvärden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="a927b-1154">Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran med hjälp av tjänsten ***nx_web_http_client_request_header_add ()*** .</span><span class="sxs-lookup"><span data-stu-id="a927b-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="a927b-1155">Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.</span><span class="sxs-lookup"><span data-stu-id="a927b-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1156">Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="a927b-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a927b-1157">Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize ())* för att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1158">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1158">Input Parameters</span></span>

- <span data-ttu-id="a927b-1159">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1160">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-1161">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1162">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-1163">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1164">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1164">Return Values</span></span>

- <span data-ttu-id="a927b-1165">**NX_SUCCESS** (0X00) lyckades skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="a927b-1166">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1167">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1167">Allowed From</span></span>

<span data-ttu-id="a927b-1168">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1169">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="a927b-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="a927b-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="a927b-1171">Hämta nästa resurs data paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1172">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1173">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1173">Description</span></span>

<span data-ttu-id="a927b-1174">Den här tjänsten hämtar nästa innehålls paket av resursen som begärdes av föregående *nx_web_http_client_get_start ()* eller *nx_web_http_client_get_secure_start ()-* anropet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="a927b-1175">Efterföljande anrop till den här rutinen bör göras tills retur statusen för NX_WEB_HTTP_GET_DONE tas emot.</span><span class="sxs-lookup"><span data-stu-id="a927b-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1176">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1176">Input Parameters</span></span>

- <span data-ttu-id="a927b-1177">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1178">**packet_ptr** Mål för paket pekare som innehåller partiellt resurs innehåll.</span><span class="sxs-lookup"><span data-stu-id="a927b-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="a927b-1179">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-1180">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1181">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-1182">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1183">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1183">Return Values</span></span>

- <span data-ttu-id="a927b-1184">**NX_SUCCESS** (0X00) lyckades Hämta http-klient paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="a927b-1185">**NX_WEB_HTTP_GET_DONE** (0X3000C) http-klient hämta paket har slutförts</span><span class="sxs-lookup"><span data-stu-id="a927b-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="a927b-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) http-klienten är inte i get-läge.</span><span class="sxs-lookup"><span data-stu-id="a927b-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="a927b-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) ogiltig paket längd</span><span class="sxs-lookup"><span data-stu-id="a927b-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="a927b-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0X3001A) HTTP-statuskod 100 Fortsätt</span><span class="sxs-lookup"><span data-stu-id="a927b-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="a927b-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0X3001B) HTTP-statuskod 101 växlings protokoll</span><span class="sxs-lookup"><span data-stu-id="a927b-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="a927b-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0X3001C) HTTP-statuskod 201 skapades</span><span class="sxs-lookup"><span data-stu-id="a927b-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="a927b-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0X3001D) HTTP-statuskod 202 accepterades</span><span class="sxs-lookup"><span data-stu-id="a927b-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="a927b-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0X3001E) HTTP-statuskod 203 icke-auktoritativ information</span><span class="sxs-lookup"><span data-stu-id="a927b-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="a927b-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0X3001F) HTTP-statuskod 204 inget innehåll</span><span class="sxs-lookup"><span data-stu-id="a927b-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="a927b-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0X30020) HTTP-statuskod 205 Återställ innehåll</span><span class="sxs-lookup"><span data-stu-id="a927b-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="a927b-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0X30021) HTTP-statuskod 206 del av innehåll</span><span class="sxs-lookup"><span data-stu-id="a927b-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="a927b-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0X30022) HTTP-statuskod 300 flera alternativ</span><span class="sxs-lookup"><span data-stu-id="a927b-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="a927b-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0X30023) HTTP-statuskod 301 flyttades permanent</span><span class="sxs-lookup"><span data-stu-id="a927b-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="a927b-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0X30024) HTTP-statuskod 302 hittades</span><span class="sxs-lookup"><span data-stu-id="a927b-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="a927b-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0X30025) HTTP-statuskod 303 Se andra</span><span class="sxs-lookup"><span data-stu-id="a927b-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="a927b-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0X30026) HTTP-statuskod 304 har inte ändrats</span><span class="sxs-lookup"><span data-stu-id="a927b-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="a927b-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0X30027) HTTP-statuskod 305 Använd proxy</span><span class="sxs-lookup"><span data-stu-id="a927b-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="a927b-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0X30028) HTTP-statuskod 307 tillfällig omdirigering</span><span class="sxs-lookup"><span data-stu-id="a927b-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="a927b-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0X30029) HTTP-statuskod 400 Felaktig begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="a927b-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0X3002A) HTTP-statuskod 401 obehörig</span><span class="sxs-lookup"><span data-stu-id="a927b-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="a927b-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0X3002B) HTTP-statuskod 402 betalning krävs</span><span class="sxs-lookup"><span data-stu-id="a927b-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="a927b-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0X3002C) HTTP-statuskod 403 förbjuden</span><span class="sxs-lookup"><span data-stu-id="a927b-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="a927b-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0X3002D) HTTP-statuskod 404 hittades inte</span><span class="sxs-lookup"><span data-stu-id="a927b-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="a927b-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0X3002E) HTTP-statuskod 405 metoden är inte tillåten</span><span class="sxs-lookup"><span data-stu-id="a927b-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="a927b-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0X3002F) HTTP-statuskod 406 är inte acceptabel</span><span class="sxs-lookup"><span data-stu-id="a927b-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="a927b-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP-statuskod 407 proxy-autentisering krävs</span><span class="sxs-lookup"><span data-stu-id="a927b-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="a927b-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0X30031) HTTP-statuskod 408 begäran om timeout</span><span class="sxs-lookup"><span data-stu-id="a927b-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="a927b-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0X30032) http STATUS kod 409 konflikt</span><span class="sxs-lookup"><span data-stu-id="a927b-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="a927b-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0X30033) HTTP-statuskod 410 borta</span><span class="sxs-lookup"><span data-stu-id="a927b-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="a927b-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0X30034) HTTP-statuskod 411 längd krävs</span><span class="sxs-lookup"><span data-stu-id="a927b-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="a927b-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0X30035) HTTP-statuskod 412 förhands villkor misslyckades</span><span class="sxs-lookup"><span data-stu-id="a927b-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="a927b-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0X30036) HTTP-statuskod 413 den begärda enheten är för stor</span><span class="sxs-lookup"><span data-stu-id="a927b-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="a927b-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP-statuskod 414 förfrågnings-URL: en är för stor</span><span class="sxs-lookup"><span data-stu-id="a927b-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="a927b-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0X30038) HTTP-statuskod 415 medie typen stöds inte</span><span class="sxs-lookup"><span data-stu-id="a927b-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="a927b-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0X30039) HTTP-statuskod 416 begärt intervall uppfyller inte kraven</span><span class="sxs-lookup"><span data-stu-id="a927b-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="a927b-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0X3003A) HTTP-statuskod 417 förväntades inte</span><span class="sxs-lookup"><span data-stu-id="a927b-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="a927b-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0X3003B) http STATUS kod 500 internt Server fel</span><span class="sxs-lookup"><span data-stu-id="a927b-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="a927b-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0X3003C) HTTP-statuskod 501 inte implementerad</span><span class="sxs-lookup"><span data-stu-id="a927b-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="a927b-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0X3003D) HTTP-statuskod 502 Felaktig gateway</span><span class="sxs-lookup"><span data-stu-id="a927b-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="a927b-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0X3003E) HTTP-statuskod 503 tjänsten är inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="a927b-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="a927b-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0X3003F) http STATUS kod 504 Gateway-timeout</span><span class="sxs-lookup"><span data-stu-id="a927b-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="a927b-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0X30040) HTTP-statuskod 505 http-version stöds inte</span><span class="sxs-lookup"><span data-stu-id="a927b-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="a927b-1227">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1228">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1229">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1229">Allowed From</span></span>

<span data-ttu-id="a927b-1230">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1231">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="a927b-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="a927b-1233">Ange motringning för att anropa vid bearbetning av HTTP-huvuden</span><span class="sxs-lookup"><span data-stu-id="a927b-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1234">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="a927b-1235">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1235">Description</span></span>

<span data-ttu-id="a927b-1236">Den här tjänsten tilldelar ett återanrop som ska anropas när NetX webb-HTTP-klient bearbetar ett HTTP-huvud i ett inkommande svar från en fjärr-HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="a927b-1237">Återanropet anropas en gång för varje huvud i svaret som det bearbetas.</span><span class="sxs-lookup"><span data-stu-id="a927b-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="a927b-1238">Återanropet gör att ett HTTP-klientprogram kan komma åt vart och ett av huvudena i svaret på HTTP-servern för att vidta önskade åtgärder utöver den grundläggande bearbetning som NetX webb-HTTP-klient gör.</span><span class="sxs-lookup"><span data-stu-id="a927b-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1239">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1239">Input Parameters</span></span>

<span data-ttu-id="a927b-1240">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="a927b-1241">**callback_function** Motringning anropades under bearbetning av svars huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="a927b-1242">Återanropet anropas med fält namnet och värdet som strängar (och deras längd).</span><span class="sxs-lookup"><span data-stu-id="a927b-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="a927b-1243">Huvudet "Content-Length: 100" skulle till exempel orsaka att funktionen anropas med "Content-Length" för *field_name* och strängen "100" för *field_value*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1244">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1244">Return Values</span></span>

- <span data-ttu-id="a927b-1245">**NX_SUCCESS** (0x00) återanrops tilldelningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="a927b-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="a927b-1246">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1247">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1247">Allowed From</span></span>

<span data-ttu-id="a927b-1248">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1249">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1249">Example</span></span>

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

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="a927b-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="a927b-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="a927b-1251">Öppna en TLS-session till en HTTPS-server för anpassade begär Anden</span><span class="sxs-lookup"><span data-stu-id="a927b-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1252">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1253">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1253">Description</span></span>

<span data-ttu-id="a927b-1254">Den här metoden är för **TLS-säkrad** https.</span><span class="sxs-lookup"><span data-stu-id="a927b-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="a927b-1255">Den här tjänsten öppnar en säker TLS-session till en HTTPS-server men skickar inga förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="a927b-1256">Begär Anden skapas med n *x_web_http_client_request_initialize ()* och skickas med *nx_web_http_client_request_send ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="a927b-1257">Anpassade HTTP-huvuden kan läggas till i begäran med hjälp av *nx_web_http_client_request_header_add ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="a927b-1258">Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="a927b-1259">**Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.**</span><span class="sxs-lookup"><span data-stu-id="a927b-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1260">Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="a927b-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="a927b-1261">Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize ())* för att skapa och skicka HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1262">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1262">Input Parameters</span></span>

- <span data-ttu-id="a927b-1263">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1264">**server_ip** IP-adress för fjärr-HTTPS-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="a927b-1265">**SERVER_PORT** Port på fjärr-HTTPS-server (t. ex. 443 för HTTPS).</span><span class="sxs-lookup"><span data-stu-id="a927b-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="a927b-1266">**tls_setup** Motringning används för att konfigurera TLS-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a927b-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="a927b-1267">Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).</span><span class="sxs-lookup"><span data-stu-id="a927b-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="a927b-1268">**wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="a927b-1269">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1270">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="a927b-1271">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1272">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1272">Return Values</span></span>

- <span data-ttu-id="a927b-1273">**NX_SUCCESS** (0x00) anslutning av TLS-session.</span><span class="sxs-lookup"><span data-stu-id="a927b-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="a927b-1274">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1275">NX_WEB_HTTP_NOT_READY (0x3000A) en annan begäran pågår redan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1276">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1276">Allowed From</span></span>

<span data-ttu-id="a927b-1277">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1278">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1278">Example</span></span>

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
    "https://192.168.1.150/test.txt ",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="a927b-1279">API för HTTP och HTTPS-server</span><span class="sxs-lookup"><span data-stu-id="a927b-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="a927b-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="a927b-1281">Ange återanropet för att hämta URL-högsta ålder och datum</span><span class="sxs-lookup"><span data-stu-id="a927b-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1282">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="a927b-1283">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1283">Description</span></span>

<span data-ttu-id="a927b-1284">Den här tjänsten anger den callback-tjänst som anropas för att hämta den maximala ålder och senaste ändrings datum för den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1285">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1285">Input Parameters</span></span>

- <span data-ttu-id="a927b-1286">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1287">**cache_info_get** Pekare till motringning</span><span class="sxs-lookup"><span data-stu-id="a927b-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="a927b-1288">**max_age** Pekare till högsta ålder för en resurs</span><span class="sxs-lookup"><span data-stu-id="a927b-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="a927b-1289">**data** Pekare till senaste ändrings datum som returnerades.</span><span class="sxs-lookup"><span data-stu-id="a927b-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1290">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1290">Return Values</span></span>

- <span data-ttu-id="a927b-1291">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="a927b-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a927b-1292">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1293">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1293">Allowed From</span></span>

<span data-ttu-id="a927b-1294">Initiering</span><span class="sxs-lookup"><span data-stu-id="a927b-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1295">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="a927b-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="a927b-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="a927b-1297">Skicka data från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="a927b-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1298">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="a927b-1299">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1299">Description</span></span>

<span data-ttu-id="a927b-1300">Den här tjänsten skickar data i det angivna paketet från programmets callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="a927b-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="a927b-1301">Detta används vanligt vis för att skicka dynamiska data som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="a927b-1302">Observera att om den här funktionen används ansvarar återanrops rutinen för att skicka hela svaret i rätt format.</span><span class="sxs-lookup"><span data-stu-id="a927b-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="a927b-1303">Dessutom måste återanrops rutinen returnera status för NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a927b-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1304">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1304">Input Parameters</span></span>

- <span data-ttu-id="a927b-1305">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1306">**data_ptr** Pekare till de data som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="a927b-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="a927b-1307">**data_length** Antal byte som ska skickas.</span><span class="sxs-lookup"><span data-stu-id="a927b-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1308">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1308">Return Values</span></span>

- <span data-ttu-id="a927b-1309">**NX_SUCCESS** (0X00) har skickat Server data</span><span class="sxs-lookup"><span data-stu-id="a927b-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="a927b-1310">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1311">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1311">Allowed From</span></span>

<span data-ttu-id="a927b-1312">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1313">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1313">Example</span></span>

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

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="a927b-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="a927b-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="a927b-1315">Skapa ett svars huvud i en callback-funktion</span><span class="sxs-lookup"><span data-stu-id="a927b-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1316">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="a927b-1317">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1317">Description</span></span>

<span data-ttu-id="a927b-1318">Den här tjänsten används i HTTP (S)-återanrops rutinen för servern (definieras av programmet) för att generera ett HTTP-svarshuvuden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="a927b-1319">Återkallnings rutinen för servern anropas när HTTP-servern svarar på GET-, Delete-och DELETE-begäranden som kräver HTTP-svar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="a927b-1320">Den här funktionen tar svars information från programmet och genererar lämpligt svars huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="a927b-1321">Se tjänst *nx_web_http_server_create ()* om du vill ha mer information om återanrops rutinen för serverbegäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="a927b-1322">Detta API är föråldrat.</span><span class="sxs-lookup"><span data-stu-id="a927b-1322">This API is deprecated.</span></span> <span data-ttu-id="a927b-1323">Utvecklare uppmanas att använda *nx_web_http_server_callback_generate_response_header_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1324">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1324">Input Parameters</span></span>

- <span data-ttu-id="a927b-1325">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1326">**packet_pptr** Pekar en paket pekare som har allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="a927b-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="a927b-1327">**status_code** Indikerar resurs status.</span><span class="sxs-lookup"><span data-stu-id="a927b-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="a927b-1328">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a927b-1328">Examples:</span></span>
  - <span data-ttu-id="a927b-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="a927b-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="a927b-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="a927b-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="a927b-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a927b-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="a927b-1332">**CONTENT_LENGTH** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="a927b-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="a927b-1333">**content_type** Typ av HTTP, t. ex. "text/plain"</span><span class="sxs-lookup"><span data-stu-id="a927b-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="a927b-1334">**additional_header** Pekare till ytterligare sidhuvud text</span><span class="sxs-lookup"><span data-stu-id="a927b-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1335">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1335">Return Values</span></span>

- <span data-ttu-id="a927b-1336">Ett HTML-huvud har skapats för **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a927b-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="a927b-1337">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1338">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1338">Allowed From</span></span>

<span data-ttu-id="a927b-1339">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1340">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1340">Example</span></span>

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

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="a927b-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="a927b-1342">Skapa ett svars huvud i en callback-funktion</span><span class="sxs-lookup"><span data-stu-id="a927b-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1343">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1343">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-1344">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1344">Description</span></span>

<span data-ttu-id="a927b-1345">Den här tjänsten används i HTTP (S)-återanrops rutinen för servern (definieras av programmet) för att generera ett HTTP-svarshuvuden.</span><span class="sxs-lookup"><span data-stu-id="a927b-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="a927b-1346">Återkallnings rutinen för servern anropas när HTTP-servern svarar på GET-, Delete-och DELETE-begäranden som kräver HTTP-svar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="a927b-1347">Den här funktionen tar svars information från programmet och genererar lämpligt svars huvud.</span><span class="sxs-lookup"><span data-stu-id="a927b-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="a927b-1348">Se tjänst *nx_web_http_server_create ()* om du vill ha mer information om återanrops rutinen för serverbegäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1349">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1349">Input Parameters</span></span>

- <span data-ttu-id="a927b-1350">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1351">**packet_pptr** Pekar en paket pekare som har allokerats för meddelande</span><span class="sxs-lookup"><span data-stu-id="a927b-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="a927b-1352">**status_code** Indikerar resurs status.</span><span class="sxs-lookup"><span data-stu-id="a927b-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="a927b-1353">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a927b-1353">Examples:</span></span>
  - <span data-ttu-id="a927b-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="a927b-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="a927b-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="a927b-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="a927b-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a927b-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="a927b-1357">**status_code_length** Sträng längd för status kod</span><span class="sxs-lookup"><span data-stu-id="a927b-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="a927b-1358">**CONTENT_LENGTH** Storlek på innehåll i byte</span><span class="sxs-lookup"><span data-stu-id="a927b-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="a927b-1359">**content_type** Typ av HTTP, t. ex. "text/plain"</span><span class="sxs-lookup"><span data-stu-id="a927b-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="a927b-1360">**content_type_length** Innehålls typ sträng längd</span><span class="sxs-lookup"><span data-stu-id="a927b-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="a927b-1361">**additional_header** Pekare till ytterligare sidhuvud text</span><span class="sxs-lookup"><span data-stu-id="a927b-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="a927b-1362">**additional_header_length** Längd på ytterligare rubrik text</span><span class="sxs-lookup"><span data-stu-id="a927b-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1363">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1363">Return Values</span></span>

- <span data-ttu-id="a927b-1364">Ett HTML-huvud har skapats för **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="a927b-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="a927b-1365">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1366">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1366">Allowed From</span></span>

<span data-ttu-id="a927b-1367">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1368">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1368">Example</span></span>

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

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="a927b-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="a927b-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="a927b-1370">Skicka ett HTTP-paket från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="a927b-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1371">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-1372">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1372">Description</span></span>

<span data-ttu-id="a927b-1373">Den här tjänsten skickar ett fullständigt HTTP-servernamn från ett HTTP-motanrop.</span><span class="sxs-lookup"><span data-stu-id="a927b-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="a927b-1374">HTTP-servern skickar paketet med NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="a927b-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="a927b-1375">HTTP-huvudet och data måste läggas till i paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="a927b-1376">Om retur statusen indikerar ett fel, måste HTTP-programmet släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="a927b-1377">Återanropet ska returnera NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a927b-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a927b-1378">Se *nx_web_http_server_callback_generate_response_header ()* för ett mer detaljerat exempel.</span><span class="sxs-lookup"><span data-stu-id="a927b-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1379">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1379">Input Parameters</span></span>

- <span data-ttu-id="a927b-1380">**server_ptr** Pekare till HTTP Server Control-Block</span><span class="sxs-lookup"><span data-stu-id="a927b-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="a927b-1381">**packet_ptr** Pekare till det paket som ska skickas</span><span class="sxs-lookup"><span data-stu-id="a927b-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1382">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1382">Return Values</span></span>

- <span data-ttu-id="a927b-1383">**NX_SUCCESS** (0X00) tog emot http-server paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="a927b-1384">**NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1385">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1385">Allowed From</span></span>

<span data-ttu-id="a927b-1386">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1387">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1387">Example</span></span>

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

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="a927b-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="a927b-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="a927b-1389">Skicka svar från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="a927b-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1390">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="a927b-1391">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1391">Description</span></span>

<span data-ttu-id="a927b-1392">Den här tjänsten skickar den levererade svars informationen från appens callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="a927b-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="a927b-1393">Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="a927b-1394">Observera att om den här funktionen används måste återanrops rutinen returnera status för NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a927b-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a927b-1395">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-1395">This service is deprecated.</span></span> <span data-ttu-id="a927b-1396">Utvecklare uppmanas att använda *nx_web_http_server_callback_response_send_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1397">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1397">Input Parameters</span></span>

- <span data-ttu-id="a927b-1398">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1399">**sidhuvud** Pekar mot svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="a927b-1400">**information** Pekar mot informations strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="a927b-1401">**additional_info** Pekare till den ytterligare informations strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1402">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1402">Return Values</span></span>

- <span data-ttu-id="a927b-1403">**NX_SUCCESS** (0X00) har skickat http-serverns svar</span><span class="sxs-lookup"><span data-stu-id="a927b-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1404">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1404">Allowed From</span></span>

<span data-ttu-id="a927b-1405">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1406">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1406">Example</span></span>

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

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="a927b-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="a927b-1408">Skicka svar från callback-funktionen</span><span class="sxs-lookup"><span data-stu-id="a927b-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1409">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="a927b-1410">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1410">Description</span></span>

<span data-ttu-id="a927b-1411">Den här tjänsten skickar den levererade svars informationen från appens callback-rutin.</span><span class="sxs-lookup"><span data-stu-id="a927b-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="a927b-1412">Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="a927b-1413">Observera att om den här funktionen används måste återanrops rutinen returnera status för NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="a927b-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="a927b-1414">Strängarna för rubrik, information och additional_info måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="a927b-1415">Den här tjänsten ersätter *nx_web_http_server_callback_response_send*().</span><span class="sxs-lookup"><span data-stu-id="a927b-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="a927b-1416">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1417">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1417">Input Parameters</span></span>

- <span data-ttu-id="a927b-1418">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1419">**sidhuvud** Pekar mot svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="a927b-1420">**header_length** Längd på svars huvud strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="a927b-1421">**information** Pekar mot informations strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="a927b-1422">**Information_length** Längden på informations strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="a927b-1423">**additional_info** Pekare till den ytterligare informations strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="a927b-1424">**additional_info_length** Den ytterligare informations strängens längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1425">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1425">Return Values</span></span>

- <span data-ttu-id="a927b-1426">**NX_SUCCESS** (0X00) har skickat http-serverns svar</span><span class="sxs-lookup"><span data-stu-id="a927b-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1427">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1427">Allowed From</span></span>

<span data-ttu-id="a927b-1428">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1429">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1429">Example</span></span>

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

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="a927b-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="a927b-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="a927b-1431">Hämta innehåll från begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1432">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="a927b-1433">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1433">Description</span></span>

<span data-ttu-id="a927b-1434">Den här tjänsten försöker hämta den angivna mängden innehåll från begäran eller skicka HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="a927b-1435">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a927b-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1436">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1436">Input Parameters</span></span>

- <span data-ttu-id="a927b-1437">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1438">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a927b-1439">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="a927b-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a927b-1440">**byte_offset** Antal byte som ska förskjutas i innehålls ytan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="a927b-1441">**destination_ptr** Pekar till mål avsnittet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="a927b-1442">**destination_size** Maximalt antal byte som är tillgängliga i mål arean.</span><span class="sxs-lookup"><span data-stu-id="a927b-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="a927b-1443">**actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.</span><span class="sxs-lookup"><span data-stu-id="a927b-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1444">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1444">Return Values</span></span>

- <span data-ttu-id="a927b-1445">**NX_SUCCESS** (0X00) http-serverns innehåll Hämta</span><span class="sxs-lookup"><span data-stu-id="a927b-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="a927b-1446">Internt fel för **NX_WEB_HTTP_ERROR** (0X30000) http-server</span><span class="sxs-lookup"><span data-stu-id="a927b-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="a927b-1447">**NX_WEB_HTTP_DATA_END** (0X30007) slut på innehåll i begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="a927b-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) timeout för http-server i Hämta nästa paket med innehåll</span><span class="sxs-lookup"><span data-stu-id="a927b-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="a927b-1449">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1450">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1451">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1451">Allowed From</span></span>

<span data-ttu-id="a927b-1452">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1453">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="a927b-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="a927b-1455">Hämta innehåll från begäran/har stöd för längd för längd innehåll</span><span class="sxs-lookup"><span data-stu-id="a927b-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1456">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="a927b-1457">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1457">Description</span></span>

<span data-ttu-id="a927b-1458">Den här tjänsten är nästan identisk med *nx_web_http_server_content_get ()*; det försöker hämta den angivna mängden innehåll från POST-eller klient förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="a927b-1459">Den hanterar dock begär Anden med innehålls längd noll (' Empty Request ') som en giltig begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="a927b-1460">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a927b-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="a927b-1461">Den här tjänsten ersätter *nx_web_http_server_content_get*().</span><span class="sxs-lookup"><span data-stu-id="a927b-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="a927b-1462">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1463">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1463">Input Parameters</span></span>

- <span data-ttu-id="a927b-1464">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1465">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a927b-1466">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="a927b-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a927b-1467">**byte_offset** Antal byte som ska förskjutas i innehålls ytan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="a927b-1468">**destination_ptr** Pekar till mål avsnittet för innehållet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="a927b-1469">**destination_size** Maximalt antal byte som är tillgängliga i mål arean.</span><span class="sxs-lookup"><span data-stu-id="a927b-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="a927b-1470">**actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.</span><span class="sxs-lookup"><span data-stu-id="a927b-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1471">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1471">Return Values</span></span>

- <span data-ttu-id="a927b-1472">**NX_SUCCESS** (0X00) http-innehållet Hämta</span><span class="sxs-lookup"><span data-stu-id="a927b-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="a927b-1473">Internt fel för **NX_WEB_HTTP_ERROR** (0X30000) http-server</span><span class="sxs-lookup"><span data-stu-id="a927b-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="a927b-1474">**NX_WEB_HTTP_DATA_END** (0X30007) slut på innehåll i begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="a927b-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) timeout för http-server i Hämta nästa paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="a927b-1476">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1477">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1478">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1478">Allowed From</span></span>

<span data-ttu-id="a927b-1479">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1480">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="a927b-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="a927b-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="a927b-1482">Hämta längden på innehållet i begäran/stöder innehålls längden noll värde</span><span class="sxs-lookup"><span data-stu-id="a927b-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1483">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="a927b-1484">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1484">Description</span></span>

<span data-ttu-id="a927b-1485">Den här tjänsten försöker hämta HTTP-innehållets längd i det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="a927b-1486">Returvärdet visar att slut för ande status har slutförts och det faktiska värdet för längd returneras i indatamängden content_length.</span><span class="sxs-lookup"><span data-stu-id="a927b-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="a927b-1487">Om det inte finns något HTTP-innehåll/innehålls längd = 0, returnerar den här rutinen fortfarande statusen slutförd och content_length inmatare pekar på en giltig längd (noll).</span><span class="sxs-lookup"><span data-stu-id="a927b-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="a927b-1488">Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a927b-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1489">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1489">Input Parameters</span></span>

- <span data-ttu-id="a927b-1490">**packet_ptr** Pekar mot HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="a927b-1491">Observera att det här paketet inte får släppas av begäran om att meddela motringning.</span><span class="sxs-lookup"><span data-stu-id="a927b-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="a927b-1492">**CONTENT_LENGTH** Pekare till värde som hämtats från fältet innehålls längd</span><span class="sxs-lookup"><span data-stu-id="a927b-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1493">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1493">Return Values</span></span>

- <span data-ttu-id="a927b-1494">**NX_SUCCESS** (0X00) http-serverns innehålls längd Hämta</span><span class="sxs-lookup"><span data-stu-id="a927b-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="a927b-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0X3000F) felaktigt http-huvudformat</span><span class="sxs-lookup"><span data-stu-id="a927b-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="a927b-1496">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1497">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1497">Allowed From</span></span>

<span data-ttu-id="a927b-1498">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1499">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="a927b-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="a927b-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="a927b-1501">Skapa en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="a927b-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1502">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1502">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-1503">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1503">Description</span></span>

<span data-ttu-id="a927b-1504">Den här tjänsten skapar en HTTP-serverinstans som körs i kontexten för en egen ThreadX-tråd.</span><span class="sxs-lookup"><span data-stu-id="a927b-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="a927b-1505">De valfria rutinerna för *authentication_check* och *request_notify* programbegäran ger program kontroll över den grundläggande driften av HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="a927b-1506">Den här tjänsten används för att skapa både oformaterade HTTP-servrar och TLS-säkra HTTPS-servrar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="a927b-1507">Information om hur du aktiverar HTTPS med TLS finns i tjänst *nx_web_http_server_secure_configure ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1508">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1508">Input Parameters</span></span>

- <span data-ttu-id="a927b-1509">**http_server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1510">**http_server_name** Pekare till HTTP-serverns namn.</span><span class="sxs-lookup"><span data-stu-id="a927b-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="a927b-1511">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a927b-1512">**SERVER_PORT** TCP-lyssnings port för Server instans.</span><span class="sxs-lookup"><span data-stu-id="a927b-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="a927b-1513">**media_ptr** Pekare till den tidigare skapade FileX Media-instansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="a927b-1514">**stack_ptr** Pekar på ett stack-fält för HTTP-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="a927b-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="a927b-1515">**stack_size** Pekare till HTTP-server trådens stack storlek.</span><span class="sxs-lookup"><span data-stu-id="a927b-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="a927b-1516">**authentication_check** Funktions pekare till programmets verifierings kontroll rutin.</span><span class="sxs-lookup"><span data-stu-id="a927b-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="a927b-1517">Den här rutinen anropas för varje HTTP-klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="a927b-1518">Om den här parametern är NULL utförs ingen autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="a927b-1519">Den här parametern är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-1519">This parameter is deprecated.</span></span> <span data-ttu-id="a927b-1520">Anropa *nx_web_http_server_authenticate_check_set*() i stället.</span><span class="sxs-lookup"><span data-stu-id="a927b-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="a927b-1521">**request_notify** Funktions pekare till program begär ande aviserings rutin.</span><span class="sxs-lookup"><span data-stu-id="a927b-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="a927b-1522">Den här rutinen anropas före HTTP-serverns bearbetning av begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="a927b-1523">Detta gör att resurs namnet kan omdirigeras eller fält i en resurs uppdateras innan HTTP-klientbegäran slutförs.</span><span class="sxs-lookup"><span data-stu-id="a927b-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1524">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1524">Return Values</span></span>

- <span data-ttu-id="a927b-1525">**NX_SUCCESS** (0X00) http-servern har skapats.</span><span class="sxs-lookup"><span data-stu-id="a927b-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="a927b-1526">NX_PTR_ERROR (0x07) ogiltig pekare för HTTP-server, IP, media, stack eller Packet-pool.</span><span class="sxs-lookup"><span data-stu-id="a927b-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="a927b-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) paket nytto lasten för poolen är inte tillräckligt stor för att rymma fullständig HTTP-begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1528">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1528">Allowed From</span></span>

<span data-ttu-id="a927b-1529">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a927b-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1530">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="a927b-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="a927b-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="a927b-1532">Ta bort en HTTP-serverinstans</span><span class="sxs-lookup"><span data-stu-id="a927b-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1533">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-1534">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1534">Description</span></span>

<span data-ttu-id="a927b-1535">Den här tjänsten tar bort en tidigare skapad HTTP-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="a927b-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1536">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1536">Input Parameters</span></span>

- <span data-ttu-id="a927b-1537">**http_server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1538">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1538">Return Values</span></span>

- <span data-ttu-id="a927b-1539">**NX_SUCCESS** (0X00) http-servern har tagits bort</span><span class="sxs-lookup"><span data-stu-id="a927b-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="a927b-1540">NX_PTR_ERROR (0x07) ogiltig HTTP-server pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="a927b-1541">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1542">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1542">Allowed From</span></span>

<span data-ttu-id="a927b-1543">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1544">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="a927b-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="a927b-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="a927b-1546">Hämta plats och längd för enhets data</span><span class="sxs-lookup"><span data-stu-id="a927b-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1547">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="a927b-1548">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1548">Description</span></span>

<span data-ttu-id="a927b-1549">Den här tjänsten bestämmer platsen för starten av data i den aktuella flerdelade entiteten i mottagna klient meddelanden och längden på data som inte inkluderar begränsnings strängen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="a927b-1550">Internt uppdaterar HTTP-servern sina egna förskjutningar så att den här funktionen kan anropas igen på samma klient-datagram för meddelanden med flera entiteter.</span><span class="sxs-lookup"><span data-stu-id="a927b-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="a927b-1551">Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="a927b-1552">Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="a927b-1553">Observera också att programmet inte bör släppa paketet som packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="a927b-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="a927b-1554">Detta görs internt av HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="a927b-1555">Se *nx_web_http_server_get_entity_header ()* för mer information.</span><span class="sxs-lookup"><span data-stu-id="a927b-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1556">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1556">Input Parameters</span></span>

- <span data-ttu-id="a927b-1557">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="a927b-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a927b-1558">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="a927b-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="a927b-1559">Observera att programmet inte ska frigöra det här paketet</span><span class="sxs-lookup"><span data-stu-id="a927b-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="a927b-1560">**available_offset** Pekare för förskjutning av enhets data från paketets lägga-pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="a927b-1561">**available_length** Pekare till längd på enhets data</span><span class="sxs-lookup"><span data-stu-id="a927b-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1562">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1562">Return Values</span></span>

- <span data-ttu-id="a927b-1563">**NX_SUCCESS** (0X00) har hämtat storlek och plats för enhetens innehåll</span><span class="sxs-lookup"><span data-stu-id="a927b-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="a927b-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) för HTTP-serverns interna flerdelade markörer finns redan</span><span class="sxs-lookup"><span data-stu-id="a927b-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="a927b-1565">Internt fel för NX_WEB_HTTP_ERROR (0x30000) HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="a927b-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="a927b-1566">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1567">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1567">Allowed From</span></span>

<span data-ttu-id="a927b-1568">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1569">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1569">Example</span></span>

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

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="a927b-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="a927b-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="a927b-1571">Hämta innehållet i enhets huvudet</span><span class="sxs-lookup"><span data-stu-id="a927b-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1572">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="a927b-1573">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1573">Description</span></span>

<span data-ttu-id="a927b-1574">Den här tjänsten hämtar enhets rubriken till den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="a927b-1575">Internt HTTP-Server uppdaterar sin egen pekare för att hitta nästa flerdelade entitet i ett klient-datagram med flera entitets-rubriker.</span><span class="sxs-lookup"><span data-stu-id="a927b-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="a927b-1576">Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="a927b-1577">Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="a927b-1578">Observera också att programmet inte bör släppa paketet som packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="a927b-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1579">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1579">Input Parameters</span></span>

- <span data-ttu-id="a927b-1580">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="a927b-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a927b-1581">**packet_pptr** Pekare till platsen för paket pekaren.</span><span class="sxs-lookup"><span data-stu-id="a927b-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="a927b-1582">Observera att programmet inte ska frigöra det här paketet</span><span class="sxs-lookup"><span data-stu-id="a927b-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="a927b-1583">**entity_header_buffer** Pekare till plats för lagring av enhets huvud</span><span class="sxs-lookup"><span data-stu-id="a927b-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="a927b-1584">**buffer_size** Storlek på indatabufferten</span><span class="sxs-lookup"><span data-stu-id="a927b-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1585">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1585">Return Values</span></span>

- <span data-ttu-id="a927b-1586">**NX_SUCCESS** (0X00) har hämtat enhets huvudet</span><span class="sxs-lookup"><span data-stu-id="a927b-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="a927b-1587">Det gick inte att hitta **NX_WEB_HTTP_NOT_FOUND** (0X30006) entitets huvud fält</span><span class="sxs-lookup"><span data-stu-id="a927b-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="a927b-1588">**NX_WEB_HTTP_TIMEOUT** (0X30001) tid för att ta emot nästa paket för klient meddelande med multipaket</span><span class="sxs-lookup"><span data-stu-id="a927b-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="a927b-1589">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1590">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="a927b-1591">Internt HTTP-fel NX_WEB_HTTP_ERROR (0x30000)</span><span class="sxs-lookup"><span data-stu-id="a927b-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1592">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1592">Allowed From</span></span>

<span data-ttu-id="a927b-1593">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1594">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1594">Example</span></span>

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

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="a927b-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="a927b-1596">Ange återanropet för att få GMT-datum och-tid</span><span class="sxs-lookup"><span data-stu-id="a927b-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1597">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="a927b-1598">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1598">Description</span></span>

<span data-ttu-id="a927b-1599">Den här tjänsten anger återanropet för att hämta GMT-datum och-tid med en tidigare skapad HTTP-server.</span><span class="sxs-lookup"><span data-stu-id="a927b-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="a927b-1600">Den här tjänsten anropas med HTTP-servern för att skapa en rubrik i HTTP-server svar på klienten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1601">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1601">Input Parameters</span></span>

- <span data-ttu-id="a927b-1602">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="a927b-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a927b-1603">**gmt_get** Pekare till GMT-motanrop</span><span class="sxs-lookup"><span data-stu-id="a927b-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="a927b-1604">**datum** Pekare till det datum som hämtades</span><span class="sxs-lookup"><span data-stu-id="a927b-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1605">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1605">Return Values</span></span>

- <span data-ttu-id="a927b-1606">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="a927b-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a927b-1607">NX_PTR_ERROR (0x07) ogiltig paket-eller parameter pekare.</span><span class="sxs-lookup"><span data-stu-id="a927b-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1608">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1608">Allowed From</span></span>

<span data-ttu-id="a927b-1609">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1610">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1610">Example</span></span>

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

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="a927b-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="a927b-1612">Ange återanropet för att hantera Ogiltig användare/lösen ord</span><span class="sxs-lookup"><span data-stu-id="a927b-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1613">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="a927b-1614">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1614">Description</span></span>

<span data-ttu-id="a927b-1615">Den här tjänsten anger återanropet som anropas när ett ogiltigt användar namn och lösen ord tas emot i en klient get-,-eller Delete-begäran, antingen av Digest eller grundläggande autentisering.</span><span class="sxs-lookup"><span data-stu-id="a927b-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="a927b-1616">HTTP-servern måste ha skapats tidigare.</span><span class="sxs-lookup"><span data-stu-id="a927b-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1617">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1617">Input Parameters</span></span>

- <span data-ttu-id="a927b-1618">**server_ptr** Pekare till HTTP-Server</span><span class="sxs-lookup"><span data-stu-id="a927b-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="a927b-1619">**invalid_username_password_callback** Pekare till Ogiltig användare/pass motringning</span><span class="sxs-lookup"><span data-stu-id="a927b-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="a927b-1620">**resurs** Pekare till resursen som anges av klienten</span><span class="sxs-lookup"><span data-stu-id="a927b-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="a927b-1621">**client_address** Klient adress</span><span class="sxs-lookup"><span data-stu-id="a927b-1621">**client_address** Client address</span></span>
- <span data-ttu-id="a927b-1622">**request_type** Anger typ av klient förfrågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="a927b-1623">Kanske:</span><span class="sxs-lookup"><span data-stu-id="a927b-1623">May be:</span></span>
  - <span data-ttu-id="a927b-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="a927b-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="a927b-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="a927b-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="a927b-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="a927b-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1627">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1627">Return Values</span></span>

- <span data-ttu-id="a927b-1628">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="a927b-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a927b-1629">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1630">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1630">Allowed From</span></span>

<span data-ttu-id="a927b-1631">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1632">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1632">Example</span></span>

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

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="a927b-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="a927b-1634">Ange ytterligare MIME-mappningar för HTML</span><span class="sxs-lookup"><span data-stu-id="a927b-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1635">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="a927b-1636">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1636">Description</span></span>

<span data-ttu-id="a927b-1637">Med den här tjänsten kan HTTP-programutvecklaren lägga till ytterligare MIME-typer från de standard-MIME-typer som anges av NetX-webb-HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="a927b-1638">Se *nx_web_http_server_get_type ()* för lista över definierade typer.</span><span class="sxs-lookup"><span data-stu-id="a927b-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="a927b-1639">När en klientbegäran tas emot, t. ex. en GET-begäran, parsar HTTP-servern den begärda filtypen från HTTP-huvudet med en prioriterad uppsättning av ytterligare MIME-mappningar och om ingen matchning hittas söker den efter en matchning i standard-MIME-mappningen för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="a927b-1640">Om ingen matchning hittas är MIME-typen Standard text/plain.</span><span class="sxs-lookup"><span data-stu-id="a927b-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="a927b-1641">Om begär ande aviserings funktionen har registrerats med HTTP-servern kan aviseringen meddela motringning anropa *nx_web_http_server_type_get_extended ()* för att parsa filtypen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1642">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1642">Input Parameters</span></span>

- <span data-ttu-id="a927b-1643">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="a927b-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a927b-1644">**mime_maps** Pekare till en MIME-kart mat ris</span><span class="sxs-lookup"><span data-stu-id="a927b-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="a927b-1645">**mime_map_num** Antal MIME-mappningar i matrisen</span><span class="sxs-lookup"><span data-stu-id="a927b-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1646">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1646">Return Values</span></span>

- <span data-ttu-id="a927b-1647">**NX_SUCCESS** (0X00) http-SERVERNS MIME-mappning har angetts</span><span class="sxs-lookup"><span data-stu-id="a927b-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="a927b-1648">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1649">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1649">Allowed From</span></span>

<span data-ttu-id="a927b-1650">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a927b-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1651">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1651">Example</span></span>

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

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="a927b-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a927b-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="a927b-1653">Allokera ett HTTP (S)-paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1654">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a927b-1655">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1655">Description</span></span>

<span data-ttu-id="a927b-1656">Den här tjänsten försöker allokera ett paket för HTTP (S)-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="a927b-1657">Observera att om ett efterföljande NetX-eller HTTP-server-API som använder det här paketet **Miss lyckas**, t. ex. nx_packet_data_append eller \* \* nx_web_http_server_callback_packet_send, är programmet ansvarigt för att släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="a927b-1658">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1658">Input Parameters</span></span>

- <span data-ttu-id="a927b-1659">**server_ptr** Pekare till HTTP Server Control-Block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="a927b-1660">**packet_ptr** Pekare till allokerat paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="a927b-1661">**wait_option** Definierar vänte tiden i Tick om det inte finns några tillgängliga paket i modempoolen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="a927b-1662">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a927b-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a927b-1663">**NX_NO_WAIT** (0X00000000) väljer NX_NO_WAIT gör att anrops tråden returneras omedelbart om begäran inte kan uppfyllas.</span><span class="sxs-lookup"><span data-stu-id="a927b-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="a927b-1664">**NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="a927b-1665">**timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.</span><span class="sxs-lookup"><span data-stu-id="a927b-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1666">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1666">Return Values</span></span>

- <span data-ttu-id="a927b-1667">**NX_SUCCESS** (0x00) paket tilldelningen lyckades</span><span class="sxs-lookup"><span data-stu-id="a927b-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="a927b-1668">**NX_NO_PACKET** (0X01) inget tillgängligt paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="a927b-1669">**NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="a927b-1670">**NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="a927b-1671">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1672">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1673">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1673">Allowed From</span></span>

<span data-ttu-id="a927b-1674">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1675">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="a927b-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="a927b-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="a927b-1677">Extrahera innehålls längd och ange pekare till början av data</span><span class="sxs-lookup"><span data-stu-id="a927b-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1678">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="a927b-1679">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1679">Description</span></span>

<span data-ttu-id="a927b-1680">Den här tjänsten extraherar innehålls längden från HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="a927b-1681">Den uppdaterar också det tillhandahållna paketet enligt följande: paketets lägga-pekare (start på platsen för den pakettyp som ska skrivas till) har angetts till HTTP-innehållet (data) precis skickade HTTP-huvudet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="a927b-1682">Om början av innehållet inte hittas i det aktuella paketet väntar funktionen på nästa paket som ska tas emot med alternativet NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE vänta.</span><span class="sxs-lookup"><span data-stu-id="a927b-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="a927b-1683">Observera att detta inte ska anropas innan du anropar *nx_web_http_server_get_entity_header ()* eftersom den ändrar paketets lägga-pekare förbi enhets huvudet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1684">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1684">Input Parameters</span></span>

- <span data-ttu-id="a927b-1685">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="a927b-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="a927b-1686">**packet_ptr** Pekare till paket pekare för att returnera paketet med uppdaterad lägga-pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="a927b-1687">**CONTENT_LENGTH** Pekare som extraheras content_length</span><span class="sxs-lookup"><span data-stu-id="a927b-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1688">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1688">Return Values</span></span>

- <span data-ttu-id="a927b-1689">**NX_SUCCESS** (0X00) http-innehålls längd hittades och paketet har uppdaterats</span><span class="sxs-lookup"><span data-stu-id="a927b-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="a927b-1690">**NX_WEB_HTTP_TIMEOUT** (0X30001) tid för att vänta på nästa paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="a927b-1691">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1692">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1692">Allowed From</span></span>

<span data-ttu-id="a927b-1693">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1694">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1694">Example</span></span>

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

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="a927b-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="a927b-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="a927b-1696">Ta emot nästa HTTP-paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1697">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-1698">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1698">Description</span></span>

<span data-ttu-id="a927b-1699">Den här tjänsten returnerar nästa paket som tas emot på HTTP-serverns socket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="a927b-1700">Alternativet vänte för att ta emot ett paket är NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="a927b-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="a927b-1701">Observera att om programmet har ansvar för att släppa paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1702">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1702">Input Parameters</span></span>

- <span data-ttu-id="a927b-1703">**server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="a927b-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="a927b-1704">**packet_ptr** Pekare till mottaget paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1705">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1705">Return Values</span></span>

- <span data-ttu-id="a927b-1706">**NX_SUCCESS** (0X00) har tagit emot nästa http-paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="a927b-1707">**NX_WEB_HTTP_TIMEOUT** (0X30001) tid för att vänta på nästa paket</span><span class="sxs-lookup"><span data-stu-id="a927b-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="a927b-1708">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1709">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1709">Allowed From</span></span>

<span data-ttu-id="a927b-1710">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1711">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="a927b-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="a927b-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="a927b-1713">Hämta parameter från begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1714">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="a927b-1715">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1715">Description</span></span>

<span data-ttu-id="a927b-1716">Den här tjänsten försöker hämta angiven HTTP URL-parameter i det angivna paketet för begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="a927b-1717">Om den begärda HTTP-parametern inte finns, returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="a927b-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="a927b-1718">Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a927b-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1719">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1719">Input Parameters</span></span>

- <span data-ttu-id="a927b-1720">**packet_ptr** Pekare till HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="a927b-1721">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a927b-1722">**param_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i parameter listan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="a927b-1723">**param_ptr** Mål arean för att kopiera parametern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="a927b-1724">**param_size** Returnera total parameter data längd (i byte).</span><span class="sxs-lookup"><span data-stu-id="a927b-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="a927b-1725">**max_param_size** Maximal storlek för parameter mål arean.</span><span class="sxs-lookup"><span data-stu-id="a927b-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1726">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1726">Return Values</span></span>

- <span data-ttu-id="a927b-1727">**NX_SUCCESS** (0X00) http-server parametern get har slutförts</span><span class="sxs-lookup"><span data-stu-id="a927b-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="a927b-1728">Det gick inte att hitta den angivna parametern **NX_WEB_HTTP_NOT_FOUND** (0x30006)</span><span class="sxs-lookup"><span data-stu-id="a927b-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="a927b-1729">Parametern för **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) är inte korrekt avslutad</span><span class="sxs-lookup"><span data-stu-id="a927b-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="a927b-1730">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1731">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1732">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1732">Allowed From</span></span>

<span data-ttu-id="a927b-1733">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1734">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="a927b-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="a927b-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="a927b-1736">Hämta fråga från begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1737">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="a927b-1738">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1738">Description</span></span>

<span data-ttu-id="a927b-1739">Den här tjänsten försöker hämta angiven HTTP URL-fråga i det angivna paketet för begäran.</span><span class="sxs-lookup"><span data-stu-id="a927b-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="a927b-1740">Om begärd HTTP-fråga inte finns, returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="a927b-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="a927b-1741">Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).</span><span class="sxs-lookup"><span data-stu-id="a927b-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1742">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1742">Input Parameters</span></span>

- <span data-ttu-id="a927b-1743">**packet_ptr** Pekare till HTTP-klientens begär ande paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="a927b-1744">Observera att programmet inte ska frigöra det här paketet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="a927b-1745">**query_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i listan över frågor.</span><span class="sxs-lookup"><span data-stu-id="a927b-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="a927b-1746">**query_ptr** Mål områden för att kopiera frågan.</span><span class="sxs-lookup"><span data-stu-id="a927b-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="a927b-1747">**query_size** Returnera frågans data storlek (i byte).</span><span class="sxs-lookup"><span data-stu-id="a927b-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="a927b-1748">**max_query_size** Maximal storlek på målet</span><span class="sxs-lookup"><span data-stu-id="a927b-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="a927b-1749">Skriv.</span><span class="sxs-lookup"><span data-stu-id="a927b-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1750">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1750">Return Values</span></span>

- <span data-ttu-id="a927b-1751">**NX_SUCCESS** (0X00) lyckad http-server fråga Hämta</span><span class="sxs-lookup"><span data-stu-id="a927b-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="a927b-1752">**NX_WEB_HTTP_FAILED** (0X30002) frågan är för liten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="a927b-1753">Det gick inte att hitta den angivna frågan för **NX_WEB_HTTP_NOT_FOUND** (0x30006)</span><span class="sxs-lookup"><span data-stu-id="a927b-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="a927b-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0X30013) ingen fråga i klient förfrågan</span><span class="sxs-lookup"><span data-stu-id="a927b-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="a927b-1755">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1756">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1757">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1757">Allowed From</span></span>

<span data-ttu-id="a927b-1758">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1759">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="a927b-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="a927b-1761">Ange segmenterad överföring för HTTP (S)-svar</span><span class="sxs-lookup"><span data-stu-id="a927b-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1762">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-1763">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1763">Description</span></span>

<span data-ttu-id="a927b-1764">Den här tjänsten använder Chunked Transfer-kodning för att skicka ett anpassat HTTP (S)-svars data paket som skapats med *nx_web_http_server_response_packet_allocate*() till klienten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1765">Om programmet använder Chunked Transfer-kodning för att skicka ett svars data paket, måste det anropa den här tjänsten när du anropar *nx_web_http_server_response_packet_allocate*() och innan du anropar *nx_web_http_server_callback_packet_send*().</span><span class="sxs-lookup"><span data-stu-id="a927b-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1766">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1766">Input Parameters</span></span>

- <span data-ttu-id="a927b-1767">**client_ptr** Pekare till HTTP-klientens kontroll block.</span><span class="sxs-lookup"><span data-stu-id="a927b-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="a927b-1768">**chunk_size** Storlek på segment data i oktetter.</span><span class="sxs-lookup"><span data-stu-id="a927b-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="a927b-1769">**packet_ptr** HTTP (a) begär data pakets pekare.</span><span class="sxs-lookup"><span data-stu-id="a927b-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1770">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1770">Return Values</span></span>

- <span data-ttu-id="a927b-1771">Den **NX_SUCCESS** (0x00) har en segment.</span><span class="sxs-lookup"><span data-stu-id="a927b-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="a927b-1772">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1773">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1773">Allowed From</span></span>

<span data-ttu-id="a927b-1774">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1775">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="a927b-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="a927b-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="a927b-1777">Konfigurera en HTTP-server för att använda TLS för säker HTTPS</span><span class="sxs-lookup"><span data-stu-id="a927b-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1778">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1778">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-1779">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1779">Description</span></span>

<span data-ttu-id="a927b-1780">Den här tjänsten konfigurerar en tidigare skapad NetX-webbinstans för HTTP-server för att använda TLS för säker HTTPS-kommunikation.</span><span class="sxs-lookup"><span data-stu-id="a927b-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="a927b-1781">Parametrarna används för att konfigurera alla möjliga TLS-sessioner med identiskt tillstånd så att varje inkommande HTTPS-klient upplever konsekvent beteende.</span><span class="sxs-lookup"><span data-stu-id="a927b-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="a927b-1782">Antalet TLS-sessioner styrs med hjälp av makro NX_WEB_HTTP_SESSION_MAX.</span><span class="sxs-lookup"><span data-stu-id="a927b-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="a927b-1783">Den kryptografiska rutin tabellen (ciphersuite-tabellen) delas mellan alla TLS-sessioner eftersom den bara innehåller funktions pekare.</span><span class="sxs-lookup"><span data-stu-id="a927b-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="a927b-1784">Buffertarna för metadata och paket ommontering är var och en uppdelad jämnt mellan alla TLS-sessioner.</span><span class="sxs-lookup"><span data-stu-id="a927b-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="a927b-1785">Om buffertstorleken inte är jämnt delbar med antalet sessioner används resten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="a927b-1786">Det skickade identitets certifikatet används av alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="a927b-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="a927b-1787">Under TLS-åtgärd läses Server identitets certifikatet bara från så att kopior inte behövs för varje session.</span><span class="sxs-lookup"><span data-stu-id="a927b-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="a927b-1788">De betrodda certifikaten läggs till i varje TLS-session i HTTPS-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="a927b-1789">Dessa används för autentisering av klient certifikat som aktive ras automatiskt när Fjärrcertifikatet har angetts.</span><span class="sxs-lookup"><span data-stu-id="a927b-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="a927b-1790">Fjärrcertifikatets matris och buffert delas som standard mellan alla TLS-sessioner.</span><span class="sxs-lookup"><span data-stu-id="a927b-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="a927b-1791">Fjärrcertifikaten används för autentisering av klient certifikat som aktive ras automatiskt när antalet fjärrcertifikat är noll.</span><span class="sxs-lookup"><span data-stu-id="a927b-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="a927b-1792">På grund av att bufferten som delas är en del sessioner kan blockeras under certifikat valideringen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="a927b-1793">Om du vill inaktivera autentisering av klient certifikat, pass NX_NULL för remote_certificates-parametern och värdet 0 för remote_certs_num-parametern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="a927b-1794">Retur värden tar med alla TLS-felkoder som uppstår på grund av problem med konfigurationen av TLS-sessionerna.</span><span class="sxs-lookup"><span data-stu-id="a927b-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1795">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1795">Input Parameters</span></span>

- <span data-ttu-id="a927b-1796">**http_server_ptr** Pekare till HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="a927b-1797">**crypto_table** Pekare till TLS ciphersuite-tabell.</span><span class="sxs-lookup"><span data-stu-id="a927b-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="a927b-1798">**metadata_buffer** Pekare till buffert för kryptografisk metadata.</span><span class="sxs-lookup"><span data-stu-id="a927b-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="a927b-1799">**metadata_size** Storlek på buffert för kryptografisk metadata.</span><span class="sxs-lookup"><span data-stu-id="a927b-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="a927b-1800">**packet_buffer** Omassembly-buffert för TLS-paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="a927b-1801">**packet_buffer** Storleken på TLS-paketets buffert – bör vara lika med (<önskad TLS-buffertstorlek \* NX_WEB_HTTP_SESSION_MAX).</span><span class="sxs-lookup"><span data-stu-id="a927b-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="a927b-1802">**identity_certificate** TLS-serverns identitets certifikat – kommer att användas för alla HTTPS-serversessioner.</span><span class="sxs-lookup"><span data-stu-id="a927b-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="a927b-1803">**trusted_certificates** Pekar mot matrisen med NX_SECURE_X509_CERT objekt som används för att verifiera inkommande klient certifikat om autentisering av klient certifikat är aktiverat genom att skicka ett värde som inte är noll för parametern *remote_certs_num* .</span><span class="sxs-lookup"><span data-stu-id="a927b-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="a927b-1804">**trusted_certs_num** Antal betrodda certifikat i *trusted_certificates* matrisen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="a927b-1805">**remote_certificates** Pekare till matrisen med NX_SECURE_X509_CERT objekt som används för inkommande klient certifikat.</span><span class="sxs-lookup"><span data-stu-id="a927b-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="a927b-1806">**remote_certs_num** Antal fjärrcertifikat.</span><span class="sxs-lookup"><span data-stu-id="a927b-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="a927b-1807">Ska vara det maximala antalet certifikat som förväntas från klienter.</span><span class="sxs-lookup"><span data-stu-id="a927b-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="a927b-1808">Autentisering av klient certifikat aktive ras automatiskt när detta inte är noll.</span><span class="sxs-lookup"><span data-stu-id="a927b-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="a927b-1809">**remote_certificate_buffer** Buffert som innehåller inkommande fjärrcertifikat från klienter om autentisering av klient certifikat är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="a927b-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="a927b-1810">remote_cert_buffer_size storleken på bufferten för fjärrcertifikat.</span><span class="sxs-lookup"><span data-stu-id="a927b-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="a927b-1811">Måste vara lika med (<maximala förväntad certifikat storlek \* remote_certs_num).</span><span class="sxs-lookup"><span data-stu-id="a927b-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="a927b-1812">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1812">Return Values</span></span>

- <span data-ttu-id="a927b-1813">**NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="a927b-1814">**NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.</span><span class="sxs-lookup"><span data-stu-id="a927b-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="a927b-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) en mottagen TLS-meddelande typ är felaktig.</span><span class="sxs-lookup"><span data-stu-id="a927b-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="a927b-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) ett chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="a927b-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="a927b-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Det gick inte att bearbeta meddelande bearbetningen under TLS-handskakningen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="a927b-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett inkommande meddelande misslyckades med en hash Mac-kontroll.</span><span class="sxs-lookup"><span data-stu-id="a927b-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="a927b-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) Det gick inte att skicka en underliggande TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="a927b-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) ett inkommande meddelande hade ett ogiltigt längd fält.</span><span class="sxs-lookup"><span data-stu-id="a927b-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="a927b-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0X10B) ett inkommande ChangeCipherSpec-meddelande var felaktigt.</span><span class="sxs-lookup"><span data-stu-id="a927b-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="a927b-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0X10C) ett inkommande TLS-certifikat kan inte användas för att identifiera fjärr-TLS-servern.</span><span class="sxs-lookup"><span data-stu-id="a927b-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="a927b-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0X10D) den offentliga nyckel chiffer som tillhandahålls av fjärrvärden stöds inte.</span><span class="sxs-lookup"><span data-stu-id="a927b-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="a927b-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) fjärrvärden har angett Inga krypteringssviter som stöds av netx Secure TLS-stacken.</span><span class="sxs-lookup"><span data-stu-id="a927b-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="a927b-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett MOTTAGet TLS-meddelande hade en okänd TLS-version i huvudet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="a927b-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) ett MOTTAGet TLS-meddelande hade en känd men TLS-version som inte stöds i huvudet.</span><span class="sxs-lookup"><span data-stu-id="a927b-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="a927b-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att tilldela en intern TLS-paket.</span><span class="sxs-lookup"><span data-stu-id="a927b-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="a927b-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) fjärrvärden tillhandahöll ett ogiltigt certifikat.</span><span class="sxs-lookup"><span data-stu-id="a927b-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="a927b-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) den fjärranslutna värden skickade en avisering som indikerar ett fel och att TLS-sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="a927b-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="a927b-1830">**NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.</span><span class="sxs-lookup"><span data-stu-id="a927b-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1831">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1831">Allowed From</span></span>

<span data-ttu-id="a927b-1832">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a927b-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1833">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1833">Example</span></span>

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

## <a name="nx_web_http_server_start"></a><span data-ttu-id="a927b-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="a927b-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="a927b-1835">Starta HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="a927b-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1836">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-1837">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1837">Description</span></span>

<span data-ttu-id="a927b-1838">Den här tjänsten startar en tidigare skapad HTTP-eller HTTPS-serverinstans.</span><span class="sxs-lookup"><span data-stu-id="a927b-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="a927b-1839">HTTPS-servrar delar samma API som HTTP.</span><span class="sxs-lookup"><span data-stu-id="a927b-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="a927b-1840">Information om hur du aktiverar HTTPS med TLS på en HTTP-Server finns i tjänst *nx_web_http_server_secure_configure ().*</span><span class="sxs-lookup"><span data-stu-id="a927b-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1841">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1841">Input Parameters</span></span>

- <span data-ttu-id="a927b-1842">**http_server_ptr** Pekare till HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1843">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1843">Return Values</span></span>

- <span data-ttu-id="a927b-1844">**NX_SUCCESS** (0X00) http-servern har startats</span><span class="sxs-lookup"><span data-stu-id="a927b-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="a927b-1845">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1846">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1846">Allowed From</span></span>

<span data-ttu-id="a927b-1847">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="a927b-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1848">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="a927b-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="a927b-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="a927b-1850">Stoppa HTTP-servern</span><span class="sxs-lookup"><span data-stu-id="a927b-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1851">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a927b-1852">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1852">Description</span></span>

<span data-ttu-id="a927b-1853">Den här tjänsten stoppar den tidigare skapade HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="a927b-1854">Den här rutinen ska anropas innan en HTTP-serverinstans tas bort.</span><span class="sxs-lookup"><span data-stu-id="a927b-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1855">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1855">Input Parameters</span></span>

- <span data-ttu-id="a927b-1856">**http_server_ptr** Pekare till HTTP-serverinstansen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1857">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1857">Return Values</span></span>

- <span data-ttu-id="a927b-1858">**NX_SUCCESS** (0X00) http-servern stoppades</span><span class="sxs-lookup"><span data-stu-id="a927b-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="a927b-1859">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1860">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="a927b-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1861">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1861">Allowed From</span></span>

<span data-ttu-id="a927b-1862">Konversation</span><span class="sxs-lookup"><span data-stu-id="a927b-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1863">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="a927b-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="a927b-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="a927b-1865">Extrahera filtypen från klientens HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1866">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="a927b-1867">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="a927b-1868">Den här tjänsten är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="a927b-1868">This service is deprecated.</span></span> <span data-ttu-id="a927b-1869">Användarna uppmanas att använda tjänsten *nx_web_http_server_type_get_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="a927b-1870">Den här tjänsten extraherar typen av HTTP-begäran i bufferten *http_type_string* och dess längd *string_size* från indatabufferten *, vanligt vis URL: en*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="a927b-1871">Om det inte går att hitta någon MIME-mappning används standard typen text/plain.</span><span class="sxs-lookup"><span data-stu-id="a927b-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="a927b-1872">Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning.</span><span class="sxs-lookup"><span data-stu-id="a927b-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="a927b-1873">Standard-MIME-mappningarna i NetX webb-HTTP-server är:</span><span class="sxs-lookup"><span data-stu-id="a927b-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="a927b-1874">HTML-text/html</span><span class="sxs-lookup"><span data-stu-id="a927b-1874">html text/html</span></span>
- <span data-ttu-id="a927b-1875">htm-text/html</span><span class="sxs-lookup"><span data-stu-id="a927b-1875">htm text/html</span></span>
- <span data-ttu-id="a927b-1876">txt-text/plain</span><span class="sxs-lookup"><span data-stu-id="a927b-1876">txt text/plain</span></span>
- <span data-ttu-id="a927b-1877">GIF-bild/gif</span><span class="sxs-lookup"><span data-stu-id="a927b-1877">gif image/gif</span></span>
- <span data-ttu-id="a927b-1878">jpg-bild/JPEG</span><span class="sxs-lookup"><span data-stu-id="a927b-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="a927b-1879">ico-bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="a927b-1879">ico image/x-icon</span></span>

<span data-ttu-id="a927b-1880">Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="a927b-1881">Se *nx_web_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1882">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1882">Input Parameters</span></span>

- <span data-ttu-id="a927b-1883">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="a927b-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a927b-1884">**namn** Pekare för att söka</span><span class="sxs-lookup"><span data-stu-id="a927b-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="a927b-1885">**http_type_string** Pekare till extraherad HTML-typ sträng</span><span class="sxs-lookup"><span data-stu-id="a927b-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="a927b-1886">**string_size** Pekare för att returnera extraherad HTML-typ sträng längd.</span><span class="sxs-lookup"><span data-stu-id="a927b-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1887">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1887">Return Values</span></span>

- <span data-ttu-id="a927b-1888">**NX_SUCCESS** (0x00) extrahering av typ</span><span class="sxs-lookup"><span data-stu-id="a927b-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="a927b-1889">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) standard "text/plain" returnerades.</span><span class="sxs-lookup"><span data-stu-id="a927b-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1891">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1891">Allowed From</span></span>

<span data-ttu-id="a927b-1892">Program</span><span class="sxs-lookup"><span data-stu-id="a927b-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1893">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1893">Example</span></span>

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

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="a927b-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="a927b-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="a927b-1895">Extrahera filtypen från klientens HTTP-begäran</span><span class="sxs-lookup"><span data-stu-id="a927b-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1896">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="a927b-1897">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1897">Description</span></span>

<span data-ttu-id="a927b-1898">Den här tjänsten extraherar typen av HTTP-begäran i bufferten *http_type_string* och dess längd *string_size* från indatabufferten *, vanligt vis URL: en*.</span><span class="sxs-lookup"><span data-stu-id="a927b-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="a927b-1899">Om det inte går att hitta någon MIME-mappning används standard typen text/plain.</span><span class="sxs-lookup"><span data-stu-id="a927b-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="a927b-1900">Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning.</span><span class="sxs-lookup"><span data-stu-id="a927b-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="a927b-1901">Standard-MIME-mappningarna i NetX webb-HTTP-server är:</span><span class="sxs-lookup"><span data-stu-id="a927b-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="a927b-1902">HTML-text/html</span><span class="sxs-lookup"><span data-stu-id="a927b-1902">html text/html</span></span>
- <span data-ttu-id="a927b-1903">htm-text/html</span><span class="sxs-lookup"><span data-stu-id="a927b-1903">htm text/html</span></span>
- <span data-ttu-id="a927b-1904">txt-text/plain</span><span class="sxs-lookup"><span data-stu-id="a927b-1904">txt text/plain</span></span>
- <span data-ttu-id="a927b-1905">GIF-bild/gif</span><span class="sxs-lookup"><span data-stu-id="a927b-1905">gif image/gif</span></span>
- <span data-ttu-id="a927b-1906">jpg-bild/JPEG</span><span class="sxs-lookup"><span data-stu-id="a927b-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="a927b-1907">ico-bild/x-ikon</span><span class="sxs-lookup"><span data-stu-id="a927b-1907">ico image/x-icon</span></span>

<span data-ttu-id="a927b-1908">Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="a927b-1909">Se *nx_web_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.</span><span class="sxs-lookup"><span data-stu-id="a927b-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="a927b-1910">Den här tjänsten ersätter *nx_web_http_server_type_get*().</span><span class="sxs-lookup"><span data-stu-id="a927b-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="a927b-1911">Den här versionen kräver att anropare anger längd information för funktionen.</span><span class="sxs-lookup"><span data-stu-id="a927b-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1912">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1912">Input Parameters</span></span>

- <span data-ttu-id="a927b-1913">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="a927b-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a927b-1914">**namn** Pekare för att söka</span><span class="sxs-lookup"><span data-stu-id="a927b-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="a927b-1915">**name_length** Längd på namn</span><span class="sxs-lookup"><span data-stu-id="a927b-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="a927b-1916">**http_type_string** Pekare till extraherad HTML-typ sträng</span><span class="sxs-lookup"><span data-stu-id="a927b-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="a927b-1917">**http_type_string_max_size** Storlek på storleken på http_type_string-buffertstorleken</span><span class="sxs-lookup"><span data-stu-id="a927b-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="a927b-1918">**string_size** Pekare som returnerar extraherad HTML-typ sträng</span><span class="sxs-lookup"><span data-stu-id="a927b-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="a927b-1919">krävande.</span><span class="sxs-lookup"><span data-stu-id="a927b-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1920">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1920">Return Values</span></span>

- <span data-ttu-id="a927b-1921">**NX_SUCCESS** (0x00) extrahering av typ</span><span class="sxs-lookup"><span data-stu-id="a927b-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="a927b-1922">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) standard "text/plain" returnerades.</span><span class="sxs-lookup"><span data-stu-id="a927b-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1924">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1924">Allowed From</span></span>

<span data-ttu-id="a927b-1925">Program</span><span class="sxs-lookup"><span data-stu-id="a927b-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1926">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1926">Example</span></span>

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

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="a927b-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="a927b-1928">Ange funktionen Digest-autentisering</span><span class="sxs-lookup"><span data-stu-id="a927b-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1929">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1929">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-1930">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1930">Description</span></span>

<span data-ttu-id="a927b-1931">Den här tjänsten anger återanropet som anropas när Digest-autentisering utförs.</span><span class="sxs-lookup"><span data-stu-id="a927b-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1932">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1932">Input Parameters</span></span>

- <span data-ttu-id="a927b-1933">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="a927b-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a927b-1934">**digest_authenticate_callback** Pekare till sammanfattad autentisering av motringning</span><span class="sxs-lookup"><span data-stu-id="a927b-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1935">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1935">Return Values</span></span>

- <span data-ttu-id="a927b-1936">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="a927b-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a927b-1937">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a927b-1938">NX_NOT_SUPPORTED (0x4B) Digest-autentisering är inte aktiverat</span><span class="sxs-lookup"><span data-stu-id="a927b-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1939">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1939">Allowed From</span></span>

<span data-ttu-id="a927b-1940">Program</span><span class="sxs-lookup"><span data-stu-id="a927b-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1941">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1941">Example</span></span>

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

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="a927b-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="a927b-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="a927b-1943">Ange funktionen Digest-autentisering</span><span class="sxs-lookup"><span data-stu-id="a927b-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a927b-1944">Prototyp</span><span class="sxs-lookup"><span data-stu-id="a927b-1944">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="a927b-1945">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a927b-1945">Description</span></span>

<span data-ttu-id="a927b-1946">Den här tjänsten anger det motanrop som anropades när autentiserings kontroll utförs.</span><span class="sxs-lookup"><span data-stu-id="a927b-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a927b-1947">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="a927b-1947">Input Parameters</span></span>

- <span data-ttu-id="a927b-1948">**http_server_ptr** Pekare till HTTP-serverinstansen</span><span class="sxs-lookup"><span data-stu-id="a927b-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="a927b-1949">**authenticate_check_externded** Pekare för att autentisera check motringning</span><span class="sxs-lookup"><span data-stu-id="a927b-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="a927b-1950">Retur värden</span><span class="sxs-lookup"><span data-stu-id="a927b-1950">Return Values</span></span>

- <span data-ttu-id="a927b-1951">**NX_SUCCESS** (0X00) har angett återanropet</span><span class="sxs-lookup"><span data-stu-id="a927b-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="a927b-1952">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="a927b-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a927b-1953">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="a927b-1953">Allowed From</span></span>

<span data-ttu-id="a927b-1954">Program</span><span class="sxs-lookup"><span data-stu-id="a927b-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="a927b-1955">Exempel</span><span class="sxs-lookup"><span data-stu-id="a927b-1955">Example</span></span>

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
