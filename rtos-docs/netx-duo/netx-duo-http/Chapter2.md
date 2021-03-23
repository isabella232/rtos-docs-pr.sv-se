---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo HTTP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo HTTP-komponenten.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9a3ea37b180ab57a8dcd269092638fa74589836a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825965"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-http"></a><span data-ttu-id="7a64e-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo HTTP</span><span class="sxs-lookup"><span data-stu-id="7a64e-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo HTTP</span></span>

<span data-ttu-id="7a64e-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo HTTP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="7a64e-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="7a64e-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="7a64e-105">Product Distribution</span></span>

<span data-ttu-id="7a64e-106">Azure återställnings tider NetX Duo kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netxduo/](https://github.com/azure-rtos/netxduo/) .</span><span class="sxs-lookup"><span data-stu-id="7a64e-106">Azure RTOS NetX Duo can be obtained from our public source code repository at [https://github.com/azure-rtos/netxduo/](https://github.com/azure-rtos/netxduo/).</span></span>

 - <span data-ttu-id="7a64e-107">**nxd_http_client. h** Rubrik fil för HTTP-klient för NetX Duo</span><span class="sxs-lookup"><span data-stu-id="7a64e-107">**nxd_http_client.h** Header file for HTTP Client for NetX Duo</span></span>
 - <span data-ttu-id="7a64e-108">**nxd_http_server. h** Rubrik fil för HTTP-server för NetX Duo</span><span class="sxs-lookup"><span data-stu-id="7a64e-108">**nxd_http_server.h** Header file for HTTP Server for NetX Duo</span></span>
 - <span data-ttu-id="7a64e-109">**nxd_http_client. c** C-källfil för HTTP-klient för NetX Duo</span><span class="sxs-lookup"><span data-stu-id="7a64e-109">**nxd_http_client.c** C Source file for HTTP Client for NetX Duo</span></span>
 - <span data-ttu-id="7a64e-110">**nxd_http_server. c** C-källfil för HTTP-server för NetX Duo</span><span class="sxs-lookup"><span data-stu-id="7a64e-110">**nxd_http_server.c** C Source file for HTTP Server for NetX Duo</span></span>
 - <span data-ttu-id="7a64e-111">**nx_md5. c** MD5 Digest-algoritmer</span><span class="sxs-lookup"><span data-stu-id="7a64e-111">**nx_md5.c** MD5 digest algorithms</span></span>
 - <span data-ttu-id="7a64e-112">**filex_stub. h** Stub-fil om FileX inte finns</span><span class="sxs-lookup"><span data-stu-id="7a64e-112">**filex_stub.h** Stub file if FileX is not present</span></span>
 - <span data-ttu-id="7a64e-113">**nxd_http.pdf** Beskrivning av HTTP för NetX Duo</span><span class="sxs-lookup"><span data-stu-id="7a64e-113">**nxd_http.pdf** Description of HTTP for NetX Duo</span></span>
 - <span data-ttu-id="7a64e-114">**demo_netxduo_http. c** NetX Duo HTTP-demonstration</span><span class="sxs-lookup"><span data-stu-id="7a64e-114">**demo_netxduo_http.c** NetX Duo HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="7a64e-115">HTTP-installation</span><span class="sxs-lookup"><span data-stu-id="7a64e-115">HTTP Installation</span></span>

<span data-ttu-id="7a64e-116">För att du ska kunna använda HTTP för NetX Duo bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat.</span><span class="sxs-lookup"><span data-stu-id="7a64e-116">In order to use HTTP for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="7a64e-117">Om t. ex. NetX Duo installeras i katalogen *"\threadx\arm7\green"* , så *nxd_http_client. h*  och *Nxd_http_client. c* för netx duo http-klientprogram och *nxd_http_server. h* -och *nxd_http_server. c* för netx Duo http-serverprogram.</span><span class="sxs-lookup"><span data-stu-id="7a64e-117">For example, if NetX Duo is installed in the directory *“\threadx\arm7\green”* then the *nxd_http_client.h*  and *nxd_http_client.c* for NetX Duo HTTP Client applications, and *nxd_http_server.h* and *nxd_http_server.c* for NetX Duo HTTP Server applications.</span></span> <span data-ttu-id="7a64e-118">*nx_md5. c* ska kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="7a64e-118">*nx_md5.c* should be copied into this directory.</span></span> <span data-ttu-id="7a64e-119">För demonstrationens RAM-drivrutin ' Application NetX Duo HTTP Client och Server Files ska kopieras till samma katalog.</span><span class="sxs-lookup"><span data-stu-id="7a64e-119">For the demo ‘ram driver’ application NetX Duo HTTP Client and Server files should be copied into the same directory.</span></span>

## <a name="using-http"></a><span data-ttu-id="7a64e-120">Använda HTTP</span><span class="sxs-lookup"><span data-stu-id="7a64e-120">Using HTTP</span></span>

<span data-ttu-id="7a64e-121">Det är enkelt att använda HTTP för NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="7a64e-121">Using HTTP for NetX Duo is easy.</span></span> <span data-ttu-id="7a64e-122">I princip måste program koden innehålla *nxd_http_client. h* och/eller *nxd_http_server. h* när den innehåller *tx_api. h*, *fx_api. h* och *nx_api. h*, för att kunna använda ThreadX, FileX och netx Duo.</span><span class="sxs-lookup"><span data-stu-id="7a64e-122">Basically, the application code must include *nxd_http_client.h* and/or *nxd_http_server.h* after it includes *tx_api.h*, *fx_api.h*, and *nx_api.h*, in order to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="7a64e-123">När HTTP-huvudfilerna har inkluderats kan program koden göra HTTP-funktions anropen senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="7a64e-123">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="7a64e-124">Programmet måste också innehålla *nxd_http_client. c*, *nxd_http_server. c* och *MD5. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="7a64e-124">The application must also include *nxd_http_client.c*, *nxd_http_server.c*, and *md5.c* in the build process.</span></span> <span data-ttu-id="7a64e-125">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="7a64e-125">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="7a64e-126">Detta är allt som krävs för att använda NetX Duo HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a64e-126">This is all that is required to use NetX Duo HTTP.</span></span>

> [!NOTE]
> <span data-ttu-id="7a64e-127">Om NX_HTTP_DIGEST_ENABLE inte anges i build-processen behöver inte MD5. c-filen läggas till i programmet.</span><span class="sxs-lookup"><span data-stu-id="7a64e-127">If NX_HTTP_DIGEST_ENABLE is not specified in the build process, the md5.c file does not need to be added to the application.</span></span> <span data-ttu-id="7a64e-128">Om ingen HTTP-klient krävs, kan filen *nxd_http_client. c* utelämnas.</span><span class="sxs-lookup"><span data-stu-id="7a64e-128">Similarly, if no HTTP Client capabilities are required, the *nxd_http_client.c* file may be omitted.</span></span>

> [!NOTE]
> <span data-ttu-id="7a64e-129">Eftersom HTTP använder NetX Duo TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* anropet innan http används.</span><span class="sxs-lookup"><span data-stu-id="7a64e-129">Since HTTP utilizes NetX Duo TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using HTTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="7a64e-130">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="7a64e-130">Small Example System</span></span>

<span data-ttu-id="7a64e-131">Ett exempel på hur enkelt det är att använda NetX Duo HTTP beskrivs i bild 1,1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="7a64e-131">An example of how easy it is to use NetX Duo HTTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="7a64e-132">I det här exemplet används de Duo-tjänster som är tillgängliga i NetX Duo HTTP-placering av #define USE_DUO på rad 23.</span><span class="sxs-lookup"><span data-stu-id="7a64e-132">This example works with the ‘duo’ services available in NetX Duo HTTP placement of #define USE_DUO  on line 23.</span></span> <span data-ttu-id="7a64e-133">Annars används den äldre NetX HTTP-motsvarigheten (endast IPv4).</span><span class="sxs-lookup"><span data-stu-id="7a64e-133">Otherwise it uses the legacy NetX HTTP equivalent (limited to IPv4 only).</span></span> <span data-ttu-id="7a64e-134">Utvecklare uppmuntras att migrera befintliga program till att använda NetX Duo-HTTP-tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="7a64e-134">Developers are encouraged to migrate existing applications to using the NetX Duo HTTP services.</span></span>

<span data-ttu-id="7a64e-135">För att kunna ange IPv6-kommunikation definierar programmet IPTYPE till IPv6 på rad 24.</span><span class="sxs-lookup"><span data-stu-id="7a64e-135">To specify IPv6 communication, the application defines IPTYPE to IPv6 in line 24.</span></span>

<span data-ttu-id="7a64e-136">I det här exemplet tas HTTP-filerna *nxd_http_client. h* och *nxd_http_server. h* in på rad 8 och 9.</span><span class="sxs-lookup"><span data-stu-id="7a64e-136">In this example, the HTTP include files *nxd_http_client.h* and *nxd_http_server.h* are brought in at line 8 and 9.</span></span> <span data-ttu-id="7a64e-137">Sedan skapas HTTP-servern för hjälp, Packet-poolen och IP-instansen på raderna 89 – 112.</span><span class="sxs-lookup"><span data-stu-id="7a64e-137">Next, the helper HTTP Server thread, packet pool and IP instance are created in lines 89 – 112.</span></span> <span data-ttu-id="7a64e-138">IP-instansen för HTTP-servern måste vara TCP-aktiverad, som visas på rad 137.</span><span class="sxs-lookup"><span data-stu-id="7a64e-138">The HTTP Server IP instance must be TCP enabled, as seen in line 137.</span></span> <span data-ttu-id="7a64e-139">HTTP-servern skapas sedan på rad 159.</span><span class="sxs-lookup"><span data-stu-id="7a64e-139">The HTTP Server is then itself is created in at line 159.</span></span>

<span data-ttu-id="7a64e-140">Nästa HTTP-klient skapas.</span><span class="sxs-lookup"><span data-stu-id="7a64e-140">Next the HTTP Client is created.</span></span> <span data-ttu-id="7a64e-141">Först skapas klient tråden på rad 172 följt av Packet-poolen och IP-instansen, ungefär som HTTP-servern, i raderna 186 – 200.</span><span class="sxs-lookup"><span data-stu-id="7a64e-141">First the client thread is created in line 172 followed by packet pool and IP instance, similar to the HTTP Server, in lines 186 – 200.</span></span> <span data-ttu-id="7a64e-142">HTTP-klientens IP-instans måste vara TCP-aktiverad (rad 217).</span><span class="sxs-lookup"><span data-stu-id="7a64e-142">Again the HTTP Client IP instance must be TCP enabled (line 217).</span></span>

<span data-ttu-id="7a64e-143">HTTP-serverrollen körs och den första aktiviteten verifierar sin IP-adress med NetX Duo som den gör i rader 423-450.</span><span class="sxs-lookup"><span data-stu-id="7a64e-143">The HTTP Server thread runs and its first task is validate its IP address with NetX Duo which it does in lines 423 - 450.</span></span> <span data-ttu-id="7a64e-144">Nu är HTTP-servern redo att ta emot begär Anden.</span><span class="sxs-lookup"><span data-stu-id="7a64e-144">Now the HTTP Server is ready to take requests.</span></span>

<span data-ttu-id="7a64e-145">Den första aktiviteten i HTTP-klientens tråd är skapa och formatera FileX-mediet (raderna 236 och 260.</span><span class="sxs-lookup"><span data-stu-id="7a64e-145">The HTTP Client thread‘s first task is create and format the FileX media (lines 236 and 260.</span></span> <span data-ttu-id="7a64e-146">När mediet har initierats skapas HTTP-klienten på rad 271.</span><span class="sxs-lookup"><span data-stu-id="7a64e-146">After the media is initialized, the HTTP Client is created in line 271.</span></span> <span data-ttu-id="7a64e-147">Detta måste göras innan HTTP-servern kan betjäna HTTP-förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="7a64e-147">This must be done before the HTTP server can service HTTP requests.</span></span> <span data-ttu-id="7a64e-148">Den måste sedan verifiera sin IP-adress med NetX Duo som den gör i rader 282 – 316.</span><span class="sxs-lookup"><span data-stu-id="7a64e-148">It must then validate its IP address with NetX Duo which it does in lines 282 – 316.</span></span> <span data-ttu-id="7a64e-149">HTTP-klienten skapar och skickar filen client_test.html till HTTP-servern, väntar en stund och försöker läsa tillbaka filen från HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="7a64e-149">The HTTP Client then creates and sends the file client_test.html to the HTTP Server, waits briefly, then attempts to read the file back from the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="7a64e-150">HTTP-klientens API använder en annan tjänst om IPv6 inte är aktiverat (*nx_http_client_put_start* på rad 343 och *nx_http_client_get_start* på rad 399).</span><span class="sxs-lookup"><span data-stu-id="7a64e-150">The HTTP Client API uses a different service if IPv6 is not enabled (*nx_http_client_put_start* in line 343 and *nx_http_client_get_start* in line 399).</span></span> <span data-ttu-id="7a64e-151">Detta gör att NetX Duo kan stödja befintliga NetX HTTP-klientprogram.</span><span class="sxs-lookup"><span data-stu-id="7a64e-151">This enables NetX Duo to support existing NetX HTTP Client applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7a64e-152">HTTP-klientens API-anrop görs med relativt korta tids gränser.</span><span class="sxs-lookup"><span data-stu-id="7a64e-152">The HTTP Client API calls are made with relatively short timeouts.</span></span> <span data-ttu-id="7a64e-153">Det kan vara nödvändigt att utöka dessa tids gränser om en HTTP-klient kommunicerar med en upptagen server eller en fjärrserver på en långsammare processor.</span><span class="sxs-lookup"><span data-stu-id="7a64e-153">It may be necessary to extend those timeouts if an HTTP client is communicating with a busy server or remote server on a slower processor.</span></span>

```c
1    /* This is a small demo of the NetX Duo HTTP Client Server API running on a
2       high-performance NetX Duo TCP/IP stack. This demo is applicable for
3       either IPv4 or IPv6 enabled applications. */
4    
5    #include   "tx_api.h"
6    #include   "fx_api.h"
7    #include   "nx_api.h"
8    #include   "nxd_http_client.h"
9    #include   "nxd_http_server.h"
10   
11   #define     DEMO_STACK_SIZE         2048  
12   
13   /* Set up FileX and file memory resources. */
14   CHAR            *ram_disk_memory;
15   FX_MEDIA        ram_disk;
16   unsigned char   media_memory[512];
17      
18   /* Define device drivers. */
19   extern void _fx_ram_driver(FX_MEDIA *media_ptr);
20   VOID        _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
22   
23   #define USE_DUO        /* Use the duo service (not legacy netx) */
24   #define IPTYPE   6       /* Send packets over IPv6 */
25
26   /* Set up the HTTP client. */
27   TX_THREAD       client_thread;
28   NX_PACKET_POOL  client_pool;
29   NX_HTTP_CLIENT  my_client;
30   NX_IP           client_ip;
31   #define         CLIENT_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
32   void            thread_client_entry(ULONG thread_input);
33   
34   #define HTTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
35   #define HTTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)
36   
37   /* Set up the HTTP server */
38   
39   NX_HTTP_SERVER  my_server;
40   NX_PACKET_POOL  server_pool;
41   TX_THREAD       server_thread;
42   NX_IP           server_ip;
43   #define         SERVER_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
44   
45   void            thread_server_entry(ULONG thread_input);
46   #ifdef FEATURE_NX_IPV6
47   NXD_ADDRESS     server_ip_address;
48   #endif
49   
50   
51   /* Define the application's authentication check. This is called by
52      the HTTP server whenever a new request is received. */
53   UINT  authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
54               CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
55   {
56   
57       /* Just use a simple name, password, and realm for all
58          requests and resources. */
59       *name =     "name";
60       *password = "password";
61       *realm =    "NetX Duo HTTP demo";
62   
63       /* Request basic authentication. */
64       return(NX_HTTP_BASIC_AUTHENTICATE);
65   }
66   
67   /* Define main entry point. */
68   
69   int main()
70   {
71   
72       /* Enter the ThreadX kernel. */
73       tx_kernel_enter();
74   }
75   
76   
77   /* Define what the initial system looks like. */
78   void    tx_application_define(void *first_unused_memory)
79   {
80   
81   CHAR    *pointer;
82   UINT    status;
83   
84       
85       /* Setup the working pointer. */
86       pointer =  (CHAR *) first_unused_memory;
87   
88       /* Create a helper thread for the server. */
89       tx_thread_create(&server_thread, "HTTP Server thread", thread_server_entry, 0,  
90                        pointer, DEMO_STACK_SIZE,
91                        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
92   
93       pointer =  pointer + DEMO_STACK_SIZE;
94   
95       /* Initialize the NetX system. */
96       nx_system_initialize();
97   
98       /* Create the server packet pool. */
99       status =  nx_packet_pool_create(&server_pool, "HTTP Server Packet Pool",
        SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);
100
101  
102      pointer = pointer + SERVER_PACKET_SIZE * 4;
103  
104      /* Check for pool creation error. */
105      if (status)
106      {
107  
108          return;
109      }
110  
111      /* Create an IP instance. */
112      status = nx_ip_create(&server_ip, "HTTP Server IP", HTTP_SERVER_ADDRESS,
113                            0xFFFFFF00UL, &server_pool, _nx_ram_network_driver,
114                            pointer, 4096, 1);
115  
116      pointer =  pointer + 4096;
117  
118      /* Check for IP create errors. */
119      if (status)
120      {
121          printf("nx_ip_create failed. Status 0x%x\n", status);
122          return;
123      }
124  
125      /* Enable ARP and supply ARP cache memory for the server IP instance. */
126      status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
127  
128      /* Check for ARP enable errors. */
129      if (status)
130      {
131          return;
132      }
133  
134      pointer = pointer + 1024;
135  
136       /* Enable TCP traffic. */
137      status = nx_tcp_enable(&server_ip);
138  
139      if (status)
140      {
141          return;
142      }
143  
144  #if (IP_TYPE==6)
145  
146      /* Set up HTTPv6 server, but we have to wait till its address has been
147         validated before we can start the thread_server_entry thread. */
148  
149      /* Set up the server's IPv6 address here. */
150      server_ip_address.nxd_ip_address.v6[3] = 0x105;
151      server_ip_address.nxd_ip_address.v6[2] = 0x0;
152      server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
153      server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
154      server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
155  
156  #endif
157  
158      /* Create the NetX HTTP Server. */
159      status = nx_http_server_create(&my_server, "My HTTP Server", &server_ip,
            &ram_disk, pointer, 2048, &server_pool, authentication_check,
            NX_NULL);
160
161      if (status)
162      {
163          return;
164      }
165  
166      pointer =  pointer + 2048;
167  
168      /* Save the memory pointer for the RAM disk. */
169      ram_disk_memory =  pointer;
170  
171      /* Create the HTTP client thread. */
172      status = tx_thread_create(&client_thread, "HTTP Client", thread_client_entry, 0,  
173                       pointer, DEMO_STACK_SIZE,
174                       2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
175  
176      pointer =  pointer + DEMO_STACK_SIZE;
177  
178      /* Check for thread create error. */
179      if (status)
180      {
181  
182          return;
183      }
184  
185      /* Create the Client packet pool. */
186      status =  nx_packet_pool_create(&client_pool, "HTTP Client Packet Pool",
 SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);

187
188  
189      pointer = pointer + SERVER_PACKET_SIZE * 4;
190  
191      /* Check for pool creation error. */
192      if (status)
193      {
194  
195          return;
196      }
197  
198  
199      /* Create an IP instance. */
200      status = nx_ip_create(&client_ip, "HTTP Client IP", HTTP_CLIENT_ADDRESS,
201                            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver,
202                            pointer, 2048, 1);
203  
204      pointer =  pointer + 2048;
205  
206      /* Check for IP create errors. */
207      if (status)
208      {
209          return;
210      }
211  
212      nx_arp_enable(&client_ip, (void *) pointer, 1024);
213  
214      pointer =  pointer + 2048;
215  
216       /* Enable TCP traffic. */
217      nx_tcp_enable(&client_ip);
218  
219      return;
220  }
221  
222  
223  VOID thread_client_entry(ULONG thread_input)
224  {
225  
226  UINT            status;
227  NX_PACKET       *my_packet;
228  #ifdef FEATURE_NX_IPV6
229  NXD_ADDRESS     client_ip_address;
230  UINT            address_index;
230  #endif
231  
232  
233      /* Format the RAM disk - the memory for the RAM disk was setup in
234        tx_application_define above. This must be set up before the client(s) start
235        sending requests. */
236      status = fx_media_format(&ram_disk,
237                              _fx_ram_driver,         // Driver entry
238                              ram_disk_memory,        // RAM disk memory pointer
239                              media_memory,           // Media buffer pointer
240                              sizeof(media_memory),   // Media buffer size
241                              "MY_RAM_DISK",          // Volume Name
242                              1,                      // Number of FATs
243                              32,                     // Directory Entries
244                              0,                      // Hidden sectors
245                              256,                    // Total sectors
246                              128,                    // Sector size   
247                              1,                      // Sectors per cluster
248                              1,                      // Heads
249                              1);                     // Sectors per track
250  
251      /* Check the media format status. */
252      if (status != FX_SUCCESS)
253      {
254  
255          /* Error, bail out. */
256          return ;
257      }
258  
259      /* Open the RAM disk. */
260      status =  fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                media_memory, sizeof(media_memory));
261  
262      /* Check the media open status. */
263      if (status != FX_SUCCESS)
264      {
265  
266          /* Error, bail out. */
267          return ;
268      }
269  
270      /* Create an HTTP client instance. */
271      status = nx_http_client_create(&my_client, "HTTP Client", &client_ip,
                    &client_pool, 600);
272  
273      /* Check status. */
274      if (status != NX_SUCCESS)
275      {
276          return;
277      }
278  
279      /* Attempt to upload a file to the HTTP server. */
280  
281  
282  #if (IPTYPE== 6)
283  
284      /* Relinquish control so the HTTP server can get set up...*/
285      tx_thread_relinquish();
286  
287      /* Set up the client's IPv6 address here. */
288      client_ip_address.nxd_ip_address.v6[3] = 0x101;
289      client_ip_address.nxd_ip_address.v6[2] = 0x0;
290      client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
291      client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
292      client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
293                 
294      /* Here's where we make the HTTP Client IPv6 enabled. */
295  
296      nxd_ipv6_enable(&client_ip);
298      nxd_icmp_enable(&client_ip);     
299      
300      /* Wait till the IP task thread has set the device MAC address. */
302      tx_thread_sleep(100);
303  
305      /* Now update NetX Duo the Client's link local and global IPv6 address. */
306      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
307      nxd_ipv6_ address_set(&server_ip, 0, &client_ip_address, 64, &address_index);
311
313      /* Then make sure NetX Duo has had time to validate the addresses. */
314      
316      tx_thread_sleep(400);
317  
321      /* Now upload an HTML file to the HTTPv6 server. */
322      status =  nxd_http_client_put_start(&my_client, &server_ip_address,
323         "/client_test.htm", "name", "password", 103, 500);
324
325
326      /* Check status. */
327      if (status != NX_SUCCESS)
328      {
329
330          return;
331      }
332      
333
334  #else
335  
336      /* Relinquish control so the HTTP server can get set up...*/
337      tx_thread_relinquish();
338  
339      do
340      {
341      
342          /* Attempt to upload to the HTTP IPv4 server. */
343          status =  nx_http_client_put_start(&my_client, HTTP_SERVER_ADDRESS,
            "/client_test.htm", "name", "password", 103, 500);
344
345  
346          /* Check status. */
347          if (status != NX_SUCCESS)
348          {
349              tx_thread_sleep(100);
350          }
351  
352      } while (status != NX_SUCCESS);
353  
354  
355  #endif  /* (IPTYPE== 6) */
356  
357  
358      /* Allocate a packet. */
359      status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET,
                        NX_WAIT_FOREVER);
360  
361      /* Check status. */
362      if (status != NX_SUCCESS)
363      {
364          return;
365      }
366  
367      /* Build a simple 103-byte HTML page. */
368      nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
369                          &client_pool, NX_WAIT_FOREVER);
370      nx_packet_data_append(my_packet,
371                   "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
372                          &client_pool, NX_WAIT_FOREVER);
373      nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
374                          &client_pool, NX_WAIT_FOREVER);
375      nx_packet_data_append(my_packet, "<H1>Another NetX Test Page!</H1>\r\n", 25,
376                          &client_pool, NX_WAIT_FOREVER);
377      nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
378                          &client_pool, NX_WAIT_FOREVER);
379      nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
380                          &client_pool, NX_WAIT_FOREVER);
381  
382      /* Complete the PUT by writing the total length. */
383      status =  nx_http_client_put_packet(&my_client, my_packet, 50);
384  
385      /* Check status. */
386      if (status != NX_SUCCESS)
387      {
388          return;
389      }
390  
391      /* Now GET the test file  */
392  
393  #ifdef USE_DUO
394  
395      status =  nxd_http_client_get_start(&my_client, &server_ip_address,
396                     "/client_test.htm", NX_NULL, 0, "name", "password", 50);
397  #else
398  
399      status =  nx_http_client_get_start(&my_client, HTTP_SERVER_ADDRESS,
                 "/client_test.htm",  NX_NULL, 0, "name", "password", 50);
400
401  #endif
402  
403      /* Check status. */
404      if (status != NX_SUCCESS)
405      {
406          return;
407      }
408  
409      status = nx_http_client_delete(&my_client);
410  
411      return;
413  }
414  
416  /* Define the helper HTTP server thread. */
417  void    thread_server_entry(ULONG thread_input)
418  {
419  
420  UINT            status;
421  #if (IPTYPE == 6)
422  UINT            address_index
423  NXD_ADDRESS     ip_address
424  
425      /* Allow time for the IP task to initialize the driver. */
426      tx_thread_sleep(100);
427
428    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
429    ip_address.nxd_ip_address.v6[0] = 0x20010000;
430    ip_address.nxd_ip_address.v6[1] = 0;
431    ip_address.nxd_ip_address.v6[2] = 0;
432    ip_address.nxd_ip_address.v6[3] = 4;
433  
434      /* Here's where we make the HTTP server IPv6 enabled. */
435      nxd_ipv6_enable(&server_ip);
436      nxd_icmp_enable(&server_ip);
437  
438      /* Wait till the IP task thread has set the device MAC address. */
439      while (server_ip.nx_ip_arp_physical_address_msw == 0 ||
440             server_ip.nx_ip_arp_physical_address_lsw == 0)
441      {
442          tx_thread_sleep(30);
443      }
444  
445      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
446      nxd_ipv6_ address_set(&server_ip, 0, &ip_address, 64, &address_index);
447  
448      /* Wait for NetX Duo to validate server address. */
449      tx_thread_sleep(400);
450  
451  #endif  /* (IPTYPE == 6) */
452  
453      /* OK to start the HTTPv6 Server. */
454      status = nx_http_server_start(&my_server);
455  
456      if (status != NX_SUCCESS)
457      {
458          return;
459      }
460  
461      /* HTTP server ready to take requests! */
462  
463      /* Let the IP threads execute. */
464      tx_thread_relinquish();
465  
466      return;
467  }
```

<span data-ttu-id="7a64e-154">**Figur 1,1 exempel på HTTP-användning med NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="7a64e-154">**Figure 1.1 Example of HTTP use with NetX Duo**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="7a64e-155">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="7a64e-155">Configuration Options</span></span>

<span data-ttu-id="7a64e-156">Det finns flera konfigurations alternativ för att skapa HTTP för NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="7a64e-156">There are several configuration options for building HTTP for NetX Duo.</span></span> <span data-ttu-id="7a64e-157">Följande är en lista över alla alternativ, där var och en beskrivs i detalj.</span><span class="sxs-lookup"><span data-stu-id="7a64e-157">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="7a64e-158">Standardvärdena visas, men kan omdefinieras innan du kan inkludera *nxd_http_client. h* och *nxd_http_server. h*:</span><span class="sxs-lookup"><span data-stu-id="7a64e-158">The default values are listed, but can be redefined prior to inclusion of *nxd_http_client.h* and *nxd_http_server.h*:</span></span>

 - <span data-ttu-id="7a64e-159">**NX_DISABLE_ERROR_CHECKING** Definierad tar det här alternativet bort grundläggande HTTP-felkontroll.</span><span class="sxs-lookup"><span data-stu-id="7a64e-159">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="7a64e-160">Den används vanligt vis när programmet har felsökts</span><span class="sxs-lookup"><span data-stu-id="7a64e-160">It is typically used after the application has been debugged</span></span>
 - <span data-ttu-id="7a64e-161">**NX_HTTP_SERVER_PRIORITY** Prioriteten för HTTP-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="7a64e-161">**NX_HTTP_SERVER_PRIORITY** The priority of the HTTP Server thread.</span></span> <span data-ttu-id="7a64e-162">Som standard definieras värdet som 16 för att ange prioritet 16.</span><span class="sxs-lookup"><span data-stu-id="7a64e-162">By default, this value is defined as 16 to specify priority 16.</span></span>
 - <span data-ttu-id="7a64e-163">**NX_HTTP_NO_FILEX** Definierad är det här alternativet en stub för FileX-beroenden.</span><span class="sxs-lookup"><span data-stu-id="7a64e-163">**NX_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="7a64e-164">HTTP-klienten fungerar utan några ändringar om det här alternativet har definierats.</span><span class="sxs-lookup"><span data-stu-id="7a64e-164">The HTTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="7a64e-165">HTTP-servern måste antingen ändras eller så måste användaren skapa en fåtal av FileX-tjänsterna för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="7a64e-165">The HTTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
 - <span data-ttu-id="7a64e-166">**NX_HTTP_TYPE_OF_SERVICE** Typ av tjänst som krävs för HTTP TCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="7a64e-166">**NX_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTP TCP requests.</span></span> <span data-ttu-id="7a64e-167">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="7a64e-167">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
  - <span data-ttu-id="7a64e-168">**NX_HTTP_SERVER_THREAD_TIME_SLICE** Antalet timer-Tick som server tråden får köra innan den tilldelas trådar av samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="7a64e-168">**NX_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="7a64e-169">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="7a64e-169">The default value is 2.</span></span>
 - <span data-ttu-id="7a64e-170">**NX_HTTP_FRAGMENT_OPTION** Fragment aktivera för HTTP TCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="7a64e-170">**NX_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="7a64e-171">Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera HTTP TCP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="7a64e-171">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
 - <span data-ttu-id="7a64e-172">**NX_HTTP_SERVER_WINDOW_SIZE**   Serverns socket Window-storlek.</span><span class="sxs-lookup"><span data-stu-id="7a64e-172">**NX_HTTP_SERVER_WINDOW_SIZE**   Server socket window size.</span></span> <span data-ttu-id="7a64e-173">Som standard är det här värdet 2048 byte</span><span class="sxs-lookup"><span data-stu-id="7a64e-173">By default, this value is 2048 bytes</span></span>
 - <span data-ttu-id="7a64e-174">**NX_HTTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="7a64e-174">**NX_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="7a64e-175">Standardvärdet är inställt på 0x80.</span><span class="sxs-lookup"><span data-stu-id="7a64e-175">The default value is set to 0x80.</span></span>
 - <span data-ttu-id="7a64e-176">**NX_HTTP_SERVER_TIMEOUT**   Anger antalet ThreadX-Tick som interna tjänster ska pausas för.</span><span class="sxs-lookup"><span data-stu-id="7a64e-176">**NX_HTTP_SERVER_TIMEOUT**   Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="7a64e-177">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7a64e-177">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
 - <span data-ttu-id="7a64e-178">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_server_socket_accept* -anrop.</span><span class="sxs-lookup"><span data-stu-id="7a64e-178">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept* calls.</span></span> <span data-ttu-id="7a64e-179">Standardvärdet är inställt på (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7a64e-179">The default value is set to (10 \* NX_IP_PERIODIC_RATE).</span></span>
 - <span data-ttu-id="7a64e-180">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_disconnect* -anrop.</span><span class="sxs-lookup"><span data-stu-id="7a64e-180">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect* calls.</span></span> <span data-ttu-id="7a64e-181">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7a64e-181">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
 - <span data-ttu-id="7a64e-182">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_receive* -anrop.</span><span class="sxs-lookup"><span data-stu-id="7a64e-182">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive* calls.</span></span> <span data-ttu-id="7a64e-183">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7a64e-183">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
 - <span data-ttu-id="7a64e-184">**NX_HTTP_SERVER_TIMEOUT_SEND** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_send* -anrop.</span><span class="sxs-lookup"><span data-stu-id="7a64e-184">**NX_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send* calls.</span></span> <span data-ttu-id="7a64e-185">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7a64e-185">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
 - <span data-ttu-id="7a64e-186">**NX_HTTP_MAX_HEADER_FIELD** Anger den maximala storleken för fältet HTTP-huvud.</span><span class="sxs-lookup"><span data-stu-id="7a64e-186">**NX_HTTP_MAX_HEADER_FIELD** Specifies the maximum size of the HTTP header field.</span></span> <span data-ttu-id="7a64e-187">Standardvärdet är 256.</span><span class="sxs-lookup"><span data-stu-id="7a64e-187">The default value is 256.</span></span>
 - <span data-ttu-id="7a64e-188">**NX_HTTP_MULTIPART_ENABLE** Om det här alternativet har definierats kan HTTP-servern stödja multipart HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="7a64e-188">**NX_HTTP_MULTIPART_ENABLE** If defined, enables HTTP Server to support multipart HTTP requests.</span></span>
 - <span data-ttu-id="7a64e-189">**NX_HTTP_SERVER_MAX_PENDING**   Anger antalet anslutningar som kan köas för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="7a64e-189">**NX_HTTP_SERVER_MAX_PENDING**   Specifies the number of connections that can be queued for the HTTP Server.</span></span> <span data-ttu-id="7a64e-190">Standardvärdet är inställt på 5.</span><span class="sxs-lookup"><span data-stu-id="7a64e-190">The default value is set to 5.</span></span>
 - <span data-ttu-id="7a64e-191">**NX_HTTP_MAX_RESOURCE** Anger antalet byte som tillåts i ett klient *resurs namn* som anges.</span><span class="sxs-lookup"><span data-stu-id="7a64e-191">**NX_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="7a64e-192">Standardvärdet är inställt på 40.</span><span class="sxs-lookup"><span data-stu-id="7a64e-192">The default value is set to 40.</span></span>
 - <span data-ttu-id="7a64e-193">**NX_HTTP_MAX_NAME** Anger antalet byte som tillåts i en klient som har angett *användar namn*.</span><span class="sxs-lookup"><span data-stu-id="7a64e-193">**NX_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="7a64e-194">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="7a64e-194">The default value is set to 20.</span></span>
 - <span data-ttu-id="7a64e-195">**NX_HTTP_MAX_PASSWORD** Anger antalet byte som tillåts i ett *lösen ord* som anges av klienten.</span><span class="sxs-lookup"><span data-stu-id="7a64e-195">**NX_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="7a64e-196">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="7a64e-196">The default value is set to 20.</span></span>
 - <span data-ttu-id="7a64e-197">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när servern skapas.</span><span class="sxs-lookup"><span data-stu-id="7a64e-197">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Server creation.</span></span> <span data-ttu-id="7a64e-198">Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket.</span><span class="sxs-lookup"><span data-stu-id="7a64e-198">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="7a64e-199">Standardvärdet är inställt på 600.</span><span class="sxs-lookup"><span data-stu-id="7a64e-199">The default value is set to 600.</span></span>
 - <span data-ttu-id="7a64e-200">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när klienten skapades.</span><span class="sxs-lookup"><span data-stu-id="7a64e-200">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="7a64e-201">Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket.</span><span class="sxs-lookup"><span data-stu-id="7a64e-201">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="7a64e-202">Standardvärdet är inställt på 300.</span><span class="sxs-lookup"><span data-stu-id="7a64e-202">The default value is set to 300.</span></span>
 - <span data-ttu-id="7a64e-203">**NX_HTTP_SERVER_RETRY_SECONDS** Ange tids gränsen för återöverföring av Server-socket i sekunder.</span><span class="sxs-lookup"><span data-stu-id="7a64e-203">**NX_HTTP_SERVER_RETRY_SECONDS** Set the Server socket retransmission timeout in seconds.</span></span> <span data-ttu-id="7a64e-204">Standardvärdet är inställt på 2.</span><span class="sxs-lookup"><span data-stu-id="7a64e-204">The default value is set to 2.</span></span>
 - <span data-ttu-id="7a64e-205">**NX_HTTP_SERVER_ RETRY_MAX** Detta anger det maximala antalet återöverföringar på Server-socketen.</span><span class="sxs-lookup"><span data-stu-id="7a64e-205">**NX_HTTP_SERVER_ RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="7a64e-206">Standardvärdet är inställt på 10.</span><span class="sxs-lookup"><span data-stu-id="7a64e-206">The default value is set to 10.</span></span>
 - <span data-ttu-id="7a64e-207">**NX_HTTP_SERVER_ RETRY_SHIFT** Det här värdet används för att ange nästa timeout för återöverföring.</span><span class="sxs-lookup"><span data-stu-id="7a64e-207">**NX_HTTP_SERVER_ RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="7a64e-208">Den aktuella tids gränsen multipliceras med antalet återöverföringar, vilket innebär att värdet för timeout-värdet för socketen flyttas.</span><span class="sxs-lookup"><span data-stu-id="7a64e-208">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="7a64e-209">Standardvärdet är inställt på 1 för dubblerad tids gräns.</span><span class="sxs-lookup"><span data-stu-id="7a64e-209">The default value is set to 1 for doubling the timeout.</span></span>
 - <span data-ttu-id="7a64e-210">**NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** Detta anger det maximala antalet paket som kan köas på återställnings kön för Server-socket.</span><span class="sxs-lookup"><span data-stu-id="7a64e-210">**NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="7a64e-211">Om antalet paket som har placerats i kö når det här antalet kan inga fler paket skickas förrän ett eller flera köade paket släpps.</span><span class="sxs-lookup"><span data-stu-id="7a64e-211">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="7a64e-212">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="7a64e-212">The default value is set to 20.</span></span>
