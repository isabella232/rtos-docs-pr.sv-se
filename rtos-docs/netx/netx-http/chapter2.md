---
title: Kapitel 2 – installation och användning av NetX HTTP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX HTTP-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826715"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a><span data-ttu-id="8ba24-103">Kapitel 2 – installation och användning av NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="8ba24-103">Chapter 2 - Installation and use of NetX HTTP</span></span>

<span data-ttu-id="8ba24-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX HTTP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="8ba24-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="8ba24-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="8ba24-105">Product Distribution</span></span>

<span data-ttu-id="8ba24-106">Azure återställnings tider-NetX kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="8ba24-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span>

- <span data-ttu-id="8ba24-107">**nx_http_client. h** Rubrik fil för HTTP-klient för NetX</span><span class="sxs-lookup"><span data-stu-id="8ba24-107">**nx_http_client.h** Header file for HTTP Client for NetX</span></span>
- <span data-ttu-id="8ba24-108">**nx_http_server. h** Rubrik fil för HTTP-server för NetX</span><span class="sxs-lookup"><span data-stu-id="8ba24-108">**nx_http_server.h** Header file for HTTP Server for NetX</span></span>
- <span data-ttu-id="8ba24-109">**nx_http_client. c** C-källfil för HTTP-klient för NetX</span><span class="sxs-lookup"><span data-stu-id="8ba24-109">**nx_http_client.c** C Source file for HTTP Client for NetX</span></span>
- <span data-ttu-id="8ba24-110">**nx_http_server. c** C-källfil för HTTP-server för NetX</span><span class="sxs-lookup"><span data-stu-id="8ba24-110">**nx_http_server.c** C Source file for HTTP Server for NetX</span></span>
- <span data-ttu-id="8ba24-111">**nx_md5. c** MD5 Digest-algoritmer</span><span class="sxs-lookup"><span data-stu-id="8ba24-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="8ba24-112">**filex_stub. h** Stub-fil om FileX inte finns</span><span class="sxs-lookup"><span data-stu-id="8ba24-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="8ba24-113">**nx_http.pdf** Beskrivning av HTTP för NetX</span><span class="sxs-lookup"><span data-stu-id="8ba24-113">**nx_http.pdf** Description of HTTP for NetX</span></span>
- <span data-ttu-id="8ba24-114">**demo_netx_http. c** NetX HTTP-demonstration</span><span class="sxs-lookup"><span data-stu-id="8ba24-114">**demo_netx_http.c** NetX HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="8ba24-115">HTTP-installation</span><span class="sxs-lookup"><span data-stu-id="8ba24-115">HTTP Installation</span></span>

<span data-ttu-id="8ba24-116">För att du ska kunna använda HTTP för NetX, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats.</span><span class="sxs-lookup"><span data-stu-id="8ba24-116">In order to use HTTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="8ba24-117">Om t. ex. NetX har installerats i katalogen "*\threadx\arm7\green*", används *nx_http_client. h* och *NX_HTTP_CLIENT. c* för NetX http-klientprogram och *nx_http_server. h* och *nx_http_server. c* för netx http-serverprogram.</span><span class="sxs-lookup"><span data-stu-id="8ba24-117">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_http_client.h* and *nx_http_client.c* for NetX HTTP Client applications, and *nx_http_server.h* and *nx_http_server.c* for NetX HTTP Server applications.</span></span> <span data-ttu-id="8ba24-118">*nx_md5. c* ska kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="8ba24-118">*nx_md5.c* should be copied into this directory.</span></span> <span data-ttu-id="8ba24-119">För demonstrationen av "ram-drivrutinen" program NetX HTTP-klient och server filer ska kopieras till samma katalog.</span><span class="sxs-lookup"><span data-stu-id="8ba24-119">For the demo ‘ram driver’ application NetX HTTP Client and Server files should be copied into the same directory.</span></span>

## <a name="using-http"></a><span data-ttu-id="8ba24-120">Använda HTTP</span><span class="sxs-lookup"><span data-stu-id="8ba24-120">Using HTTP</span></span>

<span data-ttu-id="8ba24-121">Det är enkelt att använda HTTP för NetX.</span><span class="sxs-lookup"><span data-stu-id="8ba24-121">Using HTTP for NetX is easy.</span></span> <span data-ttu-id="8ba24-122">I princip måste program koden innehålla *nx_http_client. h* och/eller *nx_http_server. h* när den innehåller *tx_api. h, fx_api. h* och *nx_api. h*, för att kunna använda ThreadX, FileX och netx.</span><span class="sxs-lookup"><span data-stu-id="8ba24-122">Basically, the application code must include *nx_http_client.h* and/or *nx_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="8ba24-123">När HTTP-huvudfilerna har inkluderats kan program koden göra HTTP-funktions anropen senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="8ba24-123">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="8ba24-124">Programmet måste också innehålla *nx_http_client. c*, *nx_http_server. c* och *MD5. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="8ba24-124">The application must also include *nx_http_client.c*, *nx_http_server.c*, and *md5.c* in the build process.</span></span> <span data-ttu-id="8ba24-125">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="8ba24-125">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="8ba24-126">Detta är allt som krävs för att använda NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ba24-126">This is all that is required to use NetX HTTP.</span></span>

>[!NOTE] 
> <span data-ttu-id="8ba24-127">Om NX_HTTP_DIGEST_ENABLE inte anges i build-processen behöver inte *MD5. c* -filen läggas till i programmet.</span><span class="sxs-lookup"><span data-stu-id="8ba24-127">If NX_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="8ba24-128">Om ingen HTTP-klient krävs, kan filen *nx_http_client. c* utelämnas.</span><span class="sxs-lookup"><span data-stu-id="8ba24-128">Similarly, if no HTTP Client capabilities are required, the *nx_http_client.c* file may be omitted.</span></span>

>[!NOTE] 
> <span data-ttu-id="8ba24-129">Eftersom HTTP använder sig av NetX TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* samtalet innan http används.</span><span class="sxs-lookup"><span data-stu-id="8ba24-129">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using HTTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="8ba24-130">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="8ba24-130">Small Example System</span></span>

<span data-ttu-id="8ba24-131">Ett exempel på hur enkelt det är att använda NetX HTTP beskrivs i bild 1,1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="8ba24-131">An example of how easy it is to use NetX HTTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="8ba24-132">I det här exemplet tas HTTP-filen *nx_http_client. h och nx_http_server. h* in på rad 8.</span><span class="sxs-lookup"><span data-stu-id="8ba24-132">In this example, the HTTP include file *nx_http_client.h and nx_http_server.h are* brought in at line 8.</span></span> <span data-ttu-id="8ba24-133">Därefter skapas HTTP-servern i "*tx_application_define*" på rad 131.</span><span class="sxs-lookup"><span data-stu-id="8ba24-133">Next, the HTTP Server is created in “*tx_application_define*” at line 131.</span></span>

>[!NOTE] 
> <span data-ttu-id="8ba24-134">HTTP Server Control Block "*Server*" har definierats som en global variabel på rad 25 tidigare.</span><span class="sxs-lookup"><span data-stu-id="8ba24-134">The HTTP Server control block “*Server*” was defined as a global variable at line 25 previously.</span></span>

<span data-ttu-id="8ba24-135">När den har skapats startas en HTTP-server på rad 136.</span><span class="sxs-lookup"><span data-stu-id="8ba24-135">After successful creation, an HTTP Server is started at line 136.</span></span> <span data-ttu-id="8ba24-136">På rad 149 har HTTP-klienten skapats.</span><span class="sxs-lookup"><span data-stu-id="8ba24-136">At line 149 the HTTP Client is created.</span></span> <span data-ttu-id="8ba24-137">Slutligen skriver klienten filen på rad 157 och läser tillbaka filen på rad 195.</span><span class="sxs-lookup"><span data-stu-id="8ba24-137">And finally, the Client writes the file at line 157 and reads the file back at line 195.</span></span>

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
                         "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

<span data-ttu-id="8ba24-138">Figur 1,1 exempel på HTTP-användning med NetX</span><span class="sxs-lookup"><span data-stu-id="8ba24-138">Figure 1.1 Example of HTTP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="8ba24-139">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="8ba24-139">Configuration Options</span></span>

<span data-ttu-id="8ba24-140">Det finns flera konfigurations alternativ för att skapa HTTP för NetX.</span><span class="sxs-lookup"><span data-stu-id="8ba24-140">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="8ba24-141">Följande är en lista över alla alternativ, där var och en beskrivs i detalj.</span><span class="sxs-lookup"><span data-stu-id="8ba24-141">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="8ba24-142">Standardvärdena visas, men kan omdefinieras innan du kan inkludera *nx_http_client. h och nx_http_server. h*:</span><span class="sxs-lookup"><span data-stu-id="8ba24-142">The default values are listed, but can be redefined prior to inclusion of *nx_http_client.h and nx_http_server.h*:</span></span>

- <span data-ttu-id="8ba24-143">**NX_DISABLE_ERROR_CHECKING** Definierad tar det här alternativet bort grundläggande HTTP-felkontroll.</span><span class="sxs-lookup"><span data-stu-id="8ba24-143">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="8ba24-144">Den används vanligt vis när programmet har felsökts.</span><span class="sxs-lookup"><span data-stu-id="8ba24-144">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="8ba24-145">**NX_HTTP_SERVER_PRIORITY** Prioriteten för HTTP-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="8ba24-145">**NX_HTTP_SERVER_PRIORITY** The priority of the HTTP Server thread.</span></span> <span data-ttu-id="8ba24-146">Som standard definieras värdet som 16 för att ange prioritet 16.</span><span class="sxs-lookup"><span data-stu-id="8ba24-146">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="8ba24-147">**NX_HTTP_NO_FILEX** Definierad är det här alternativet en stub för FileX-beroenden.</span><span class="sxs-lookup"><span data-stu-id="8ba24-147">**NX_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="8ba24-148">HTTP-klienten fungerar utan några ändringar om det här alternativet har definierats.</span><span class="sxs-lookup"><span data-stu-id="8ba24-148">The HTTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="8ba24-149">HTTP-servern måste antingen ändras eller så måste användaren skapa en fåtal av FileX-tjänsterna för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="8ba24-149">The HTTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="8ba24-150">**NX_HTTP_TYPE_OF_SERVICE** Typ av tjänst som krävs för HTTP TCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8ba24-150">**NX_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTP TCP requests.</span></span> <span data-ttu-id="8ba24-151">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="8ba24-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="8ba24-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** Antalet timer-Tick som server tråden får köra innan den tilldelas trådar av samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="8ba24-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="8ba24-153">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="8ba24-153">The default value is 2.</span></span>
- <span data-ttu-id="8ba24-154">**NX_HTTP_FRAGMENT_OPTION** Fragment aktivera för HTTP TCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8ba24-154">**NX_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="8ba24-155">Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera HTTP TCP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="8ba24-155">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="8ba24-156">**NX_HTTP_SERVER_WINDOW_SIZE** Serverns socket Window-storlek.</span><span class="sxs-lookup"><span data-stu-id="8ba24-156">**NX_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="8ba24-157">Som standard är det här värdet 2048 byte.</span><span class="sxs-lookup"><span data-stu-id="8ba24-157">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="8ba24-158">**NX_HTTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="8ba24-158">**NX_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="8ba24-159">Standardvärdet är inställt på 0x80.</span><span class="sxs-lookup"><span data-stu-id="8ba24-159">The default value is set to 0x80.</span></span>
- <span data-ttu-id="8ba24-160">**NX_HTTP_SERVER_TIMEOUT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för.</span><span class="sxs-lookup"><span data-stu-id="8ba24-160">**NX_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="8ba24-161">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="8ba24-161">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="8ba24-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_server_socket_accept* -anrop.</span><span class="sxs-lookup"><span data-stu-id="8ba24-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept* calls.</span></span> <span data-ttu-id="8ba24-163">Standardvärdet är inställt på (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="8ba24-163">The default value is set to (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="8ba24-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_disconnect* -anrop.</span><span class="sxs-lookup"><span data-stu-id="8ba24-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect* calls.</span></span> <span data-ttu-id="8ba24-165">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="8ba24-165">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="8ba24-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_receive* -anrop.</span><span class="sxs-lookup"><span data-stu-id="8ba24-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive* calls.</span></span> <span data-ttu-id="8ba24-167">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="8ba24-167">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="8ba24-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_send* -anrop.</span><span class="sxs-lookup"><span data-stu-id="8ba24-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send* calls.</span></span> <span data-ttu-id="8ba24-169">Standardvärdet är inställt på 10 sekunder (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="8ba24-169">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="8ba24-170">**NX_HTTP_MAX_HEADER_FIELD** Anger den maximala storleken för fältet HTTP-huvud.</span><span class="sxs-lookup"><span data-stu-id="8ba24-170">**NX_HTTP_MAX_HEADER_FIELD** Specifies the maximum size of the HTTP header field.</span></span> <span data-ttu-id="8ba24-171">Standardvärdet är 256.</span><span class="sxs-lookup"><span data-stu-id="8ba24-171">The default value is 256.</span></span>
- <span data-ttu-id="8ba24-172">**NX_HTTP_MULTIPART_ENABLE** Om det här alternativet har definierats kan HTTP-servern stödja multipart HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="8ba24-172">**NX_HTTP_MULTIPART_ENABLE** If defined, enables HTTP Server to support multipart HTTP requests.</span></span>
- <span data-ttu-id="8ba24-173">**NX_HTTP_SERVER_MAX_PENDING** Anger antalet anslutningar som kan köas för HTTP-servern.</span><span class="sxs-lookup"><span data-stu-id="8ba24-173">**NX_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTP Server.</span></span> <span data-ttu-id="8ba24-174">Standardvärdet är inställt på 5.</span><span class="sxs-lookup"><span data-stu-id="8ba24-174">The default value is set to 5.</span></span>
- <span data-ttu-id="8ba24-175">**NX_HTTP_MAX_RESOURCE** Anger antalet byte som tillåts i ett klient *resurs namn* som anges.</span><span class="sxs-lookup"><span data-stu-id="8ba24-175">**NX_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="8ba24-176">Standardvärdet är inställt på 40.</span><span class="sxs-lookup"><span data-stu-id="8ba24-176">The default value is set to 40.</span></span>
- <span data-ttu-id="8ba24-177">**NX_HTTP_MAX_NAME** Anger antalet byte som tillåts i en klient som har angett *användar namn*.</span><span class="sxs-lookup"><span data-stu-id="8ba24-177">**NX_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="8ba24-178">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="8ba24-178">The default value is set to 20.</span></span>
- <span data-ttu-id="8ba24-179">**NX_HTTP_MAX_PASSWORD** Anger antalet byte som tillåts i ett *lösen ord* som anges av klienten.</span><span class="sxs-lookup"><span data-stu-id="8ba24-179">**NX_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="8ba24-180">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="8ba24-180">The default value is set to 20.</span></span>
- <span data-ttu-id="8ba24-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när servern skapas.</span><span class="sxs-lookup"><span data-stu-id="8ba24-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Server creation.</span></span> <span data-ttu-id="8ba24-182">Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket.</span><span class="sxs-lookup"><span data-stu-id="8ba24-182">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="8ba24-183">Standardvärdet är inställt på 600.</span><span class="sxs-lookup"><span data-stu-id="8ba24-183">The default value is set to 600.</span></span>
- <span data-ttu-id="8ba24-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när klienten skapades.</span><span class="sxs-lookup"><span data-stu-id="8ba24-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="8ba24-185">Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket.</span><span class="sxs-lookup"><span data-stu-id="8ba24-185">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="8ba24-186">Standardvärdet är inställt på 300.</span><span class="sxs-lookup"><span data-stu-id="8ba24-186">The default value is set to 300.</span></span>
- <span data-ttu-id="8ba24-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Ange tids gränsen för återöverföring av Server-socket i sekunder.* Standardvärdet är inställt på 2.</span><span class="sxs-lookup"><span data-stu-id="8ba24-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Set the Server socket retransmission timeout in seconds. The* default value is set to 2.</span></span>
- <span data-ttu-id="8ba24-188">**NX_HTTP_SERVER_RETRY_MAX** Detta anger det maximala antalet återöverföringar på Server-socketen.</span><span class="sxs-lookup"><span data-stu-id="8ba24-188">**NX_HTTP_SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="8ba24-189">Standardvärdet är inställt på 10.</span><span class="sxs-lookup"><span data-stu-id="8ba24-189">The default value is set to 10.</span></span>
- <span data-ttu-id="8ba24-190">**NX_HTTP_SERVER_RETRY_SHIFT** Det här värdet används för att ange nästa timeout för återöverföring.</span><span class="sxs-lookup"><span data-stu-id="8ba24-190">**NX_HTTP_SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="8ba24-191">Den aktuella tids gränsen multipliceras med antalet återöverföringar, vilket innebär att värdet för timeout-värdet för socketen flyttas.</span><span class="sxs-lookup"><span data-stu-id="8ba24-191">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="8ba24-192">Standardvärdet är inställt på 1 för dubblerad tids gräns.</span><span class="sxs-lookup"><span data-stu-id="8ba24-192">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="8ba24-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** Detta anger det maximala antalet paket som kan köas på återställnings kön för Server-socket.</span><span class="sxs-lookup"><span data-stu-id="8ba24-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="8ba24-194">Om antalet paket som har placerats i kö når det här antalet kan inga fler paket skickas förrän ett eller flera köade paket släpps.</span><span class="sxs-lookup"><span data-stu-id="8ba24-194">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="8ba24-195">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="8ba24-195">The default value is set to 20.</span></span>