---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX FTP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX FTP-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 812422566b9761baac5f9c2477dba1f0fcc0a778
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826724"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-ftp"></a><span data-ttu-id="cbe68-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX FTP</span><span class="sxs-lookup"><span data-stu-id="cbe68-103">Chapter 2 - Installation and use of Azure RTOS NetX FTP</span></span>

<span data-ttu-id="cbe68-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX FTP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="cbe68-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX FTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="cbe68-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="cbe68-105">Product Distribution</span></span>

<span data-ttu-id="cbe68-106">Azure återställnings tider-NetX kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]) .</span><span class="sxs-lookup"><span data-stu-id="cbe68-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]).</span></span> <span data-ttu-id="cbe68-107">Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="cbe68-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="cbe68-108">**nx_ftp. h**: rubrik fil för FTP för netx</span><span class="sxs-lookup"><span data-stu-id="cbe68-108">**nx_ftp.h**: Header file for FTP for NetX</span></span>
- <span data-ttu-id="cbe68-109">**nx_ftp_client. c**: c-källfil för FTP-klient för netx</span><span class="sxs-lookup"><span data-stu-id="cbe68-109">**nx_ftp_client.c**: C Source file for FTP Client for NetX</span></span>
- <span data-ttu-id="cbe68-110">**nx_ftp_server. c**: c-källfil för FTP-server för netx</span><span class="sxs-lookup"><span data-stu-id="cbe68-110">**nx_ftp_server.c**: C Source file for FTP Server for NetX</span></span>
- <span data-ttu-id="cbe68-111">**filex_stub. h**: stub-fil om filex inte finns</span><span class="sxs-lookup"><span data-stu-id="cbe68-111">**filex_stub.h**: Stub file if FileX is not present</span></span>
- <span data-ttu-id="cbe68-112">**nx_ftp.pdf**: PDF-Beskrivning av FTP för netx</span><span class="sxs-lookup"><span data-stu-id="cbe68-112">**nx_ftp.pdf**: PDF description of FTP for NetX</span></span>
- <span data-ttu-id="cbe68-113">**demo_netx_ftp. c**: FTP demonstrations system</span><span class="sxs-lookup"><span data-stu-id="cbe68-113">**demo_netx_ftp.c**: FTP demonstration system</span></span>

## <a name="ftp-installation"></a><span data-ttu-id="cbe68-114">FTP-installation</span><span class="sxs-lookup"><span data-stu-id="cbe68-114">FTP Installation</span></span>

<span data-ttu-id="cbe68-115">För att du ska kunna använda FTP för NetX bör hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats.</span><span class="sxs-lookup"><span data-stu-id="cbe68-115">In order to use FTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="cbe68-116">Om NetX till exempel är installerat i katalogen "*\threadx\arm7\green*", ska *nx_ftp. h*-, *nx_ftp_client. c*-och *nx_ftp_server. c* -filer kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="cbe68-116">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_ftp.h*, *nx_ftp_client.c*, and *nx_ftp_server.c* files should be copied into this directory.</span></span>

## <a name="using-ftp"></a><span data-ttu-id="cbe68-117">Använd FTP</span><span class="sxs-lookup"><span data-stu-id="cbe68-117">Using FTP</span></span>

<span data-ttu-id="cbe68-118">Det är enkelt att använda FTP för NetX.</span><span class="sxs-lookup"><span data-stu-id="cbe68-118">Using FTP for NetX is easy.</span></span> <span data-ttu-id="cbe68-119">I princip måste program koden innehålla *nx_ftp. h* när den innehåller *tx_api. h, fx_api. h* , och *nx_api. h*, för att kunna använda ThreadX, FileX respektive netx.</span><span class="sxs-lookup"><span data-stu-id="cbe68-119">Basically, the application code must include *nx_ftp.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="cbe68-120">När *nx_ftp. h* ingår kan program koden sedan göra FTP-funktions anropen angivna senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="cbe68-120">Once *nx_ftp.h* is included, the application code is then able to make the FTP function calls specified later in this guide.</span></span> <span data-ttu-id="cbe68-121">Programmet måste även innehålla *nx_ftp_client. c* och *nx_ftp_server. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="cbe68-121">The application must also include *nx_ftp_client.c* and *nx_ftp_server.c* in the build process.</span></span> <span data-ttu-id="cbe68-122">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="cbe68-122">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="cbe68-123">Detta är allt som krävs för att använda NetX FTP.</span><span class="sxs-lookup"><span data-stu-id="cbe68-123">This is all that is required to use NetX FTP.</span></span>

> [!NOTE]
> <span data-ttu-id="cbe68-124">Eftersom FTP använder sig av NetX TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* samtalet innan FTP används.</span><span class="sxs-lookup"><span data-stu-id="cbe68-124">Since FTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using FTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="cbe68-125">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="cbe68-125">Small Example System</span></span>

<span data-ttu-id="cbe68-126">Ett exempel på hur enkelt det är att använda NetX FTP beskrivs i bild 1,1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="cbe68-126">An example of how easy it is to use NetX FTP is described in Figure 1.1 that appears below.</span></span>

> [!NOTE]
> <span data-ttu-id="cbe68-127">Detta är för en värd enhet med ett enda nätverks gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="cbe68-127">This is for a host device with a single network interface.</span></span>

<span data-ttu-id="cbe68-128">I det här exemplet tas FTP-filen *nx_ftp_client. h* och *nx_ftp_server. h* till rad 10 och 11.</span><span class="sxs-lookup"><span data-stu-id="cbe68-128">In this example, the FTP include file *nx_ftp_client.h* and *nx_ftp_server.h* are brought at line 10 and 11.</span></span> <span data-ttu-id="cbe68-129">Därefter skapas FTP-servern i "*tx_application_define*" på rad 134.</span><span class="sxs-lookup"><span data-stu-id="cbe68-129">Next, the FTP Server is created in "*tx_application_define*" at line 134.</span></span> <span data-ttu-id="cbe68-130">Observera att FTP Server Control Block "*Server*" har definierats som en global variabel på rad 31 tidigare.</span><span class="sxs-lookup"><span data-stu-id="cbe68-130">Note that the FTP Server control block "*Server*" was defined as a global variable at line 31 previously.</span></span> <span data-ttu-id="cbe68-131">När den har skapats startas en FTP-server på rad 363.</span><span class="sxs-lookup"><span data-stu-id="cbe68-131">After successful creation, an FTP Server is started at line 363.</span></span> <span data-ttu-id="cbe68-132">På rad 183 skapas FTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="cbe68-132">At line 183 the FTP Client is created.</span></span> <span data-ttu-id="cbe68-133">Slutligen skriver klienten filen på rad 229 och läser tillbaka filen på rad 318.</span><span class="sxs-lookup"><span data-stu-id="cbe68-133">And finally, the Client writes the file at line 229 and reads the file back at line 318.</span></span>

```c
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack. This demo
relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
and then back to the server. */

#include     "tx_api.h"
#include     "fx_api.h"
#include     "nx_api.h"
#include     "nx_ftp_client.h"
#include     "nx_ftp_server.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD          server_thread;
TX_THREAD          client_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_PACKET_POOL     client_pool;
NX_IP              client_ip;
FX_MEDIA           ram_disk;

/* Define the NetX FTP object control blocks. */

NX_FTP_CLIENT     ftp_client;
NX_FTP_SERVER     ftp_server;

/* Define the counters used in the demo application... */

ULONG     error_counter = 0;

/* Define the memory area for the FileX RAM disk. */

UCHAR     ram_disk_memory[32000];
UCHAR     ram_disk_sector_cache[512];

#define FTP_SERVER_ADDRESS IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS IP_ADDRESS(1,2,3,5)

extern UINT _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                    VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                    CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                    UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                    UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions. */
VOID     _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

void     client_thread_entry(ULONG thread_input);
void     thread_server_entry(ULONG thread_input);

/* Define server login/logout functions. These are stubs for functions that would
validate a client login request. */

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port, CHAR *name,
                CHAR *password, CHAR *extra_info);

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port, CHAR *name,
                    CHAR *password, CHAR *extra_info);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry,
                    0, pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize NetX. */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server. */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance",
                        FTP_SERVER_ADDRESS, 0xFFFFFF00UL, &server_pool,
                        _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance. */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP. */
    nx_tcp_enable(&server_ip);

    /* Create the FTP server. */
    status = nx_ftp_server_create(&ftp_server, "FTP Server Instance",
                    &server_ip, &ram_disk, pointer, DEMO_STACK_SIZE,
                    &server_pool, server_login, server_logout);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread. */
    status = tx_thread_create(&client_thread, "FTP Client thread ",
                            client_thread_entry, 0,
                            pointer, DEMO_STACK_SIZE,
                            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client. */
    status = nx_packet_pool_create(&client_pool, "NetX Client Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance for the FTP client. */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS,
            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP. */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance. */
    nx_tcp_enable(&client_ip);

    return;
}

/* Define the FTP client thread. */
void     client_thread_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = _fx_media_format(&ram_disk,
            _fx_ram_driver, /* Driver entry */
            ram_disk_memory, /* RAM disk memory pointer */
            ram_disk_sector_cache, /* Media buffer pointer */
            sizeof(ram_disk_sector_cache), /* Media buffer size */
            "MY_RAM_DISK", /* Volume Name */
            1, /* Number of FATs */
            32, /* Directory Entries */
            0, /* Hidden sectors */
            256, /* Total sectors */
            128, /* Sector size */
            1, /* Sectors per cluster */
            1, /* Heads */
            1); /* Sectors per track */

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                            ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

     /* Let the IP threads and driver initialize the system. */
    tx_thread_sleep(100);

    /* Create an FTP client. */
    status = nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Created the FTP Client\n");

    /* Now connect with the NetX FTP (IPv4) server. */
    status = nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS,
                                    "name", "password", 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet. */
    status = nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Write ABCs into the packet payload! */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length = 28;
    my_packet -> nx_packet_append_ptr = my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt. */
    status = nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");

    /* Close the file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");

    /* Now open the same file for reading. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file. */
    status = nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
        printf("Reread the FTP client test.txt file\n");
        nx_packet_release(my_packet);
    }

    /* Close this file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server. */
    status = nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    /* Delete the FTP client. */
    status = nx_ftp_client_delete(&ftp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
}

/* Define the helper FTP server thread. */
void     thread_server_entry(ULONG thread_input)
{

UINT     status;

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

    /* OK to start the FTP Server. */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute. */
    tx_thread_relinquish();

    return;
}

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port,
                CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success. */
    return(NX_SUCCESS);
}

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success. */
    return(NX_SUCCESS);
}
```

<span data-ttu-id="cbe68-134">Figur 1,1 exempel på en FTP-klient och server med NetX (Single Network Interface Host)</span><span class="sxs-lookup"><span data-stu-id="cbe68-134">Figure 1.1 Example of FTP Client and Server with NetX (Single network interface host)</span></span>

## <a name="configuration-options"></a><span data-ttu-id="cbe68-135">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="cbe68-135">Configuration Options</span></span>

<span data-ttu-id="cbe68-136">Det finns flera konfigurations alternativ för att skapa FTP för NetX.</span><span class="sxs-lookup"><span data-stu-id="cbe68-136">There are several configuration options for building FTP for NetX.</span></span> <span data-ttu-id="cbe68-137">I följande lista beskrivs var och en i detalj:</span><span class="sxs-lookup"><span data-stu-id="cbe68-137">The following list describes each in detail:</span></span>  

- <span data-ttu-id="cbe68-138">**NX_FTP_SERVER_PRIORITY**: prioriteten för FTP-serverrollen.</span><span class="sxs-lookup"><span data-stu-id="cbe68-138">**NX_FTP_SERVER_PRIORITY**: The priority of the FTP Server thread.</span></span> <span data-ttu-id="cbe68-139">Som standard definieras värdet som 16 för att ange prioritet 16.</span><span class="sxs-lookup"><span data-stu-id="cbe68-139">By default, this value is defined as 16 to specify priority 16.</span></span>

- <span data-ttu-id="cbe68-140">**NX_FTP_MAX_CLIENTS**: det maximala antalet klienter som servern kan hantera på en och samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="cbe68-140">**NX_FTP_MAX_CLIENTS**: The maximum number of Clients the Server can handle at one time.</span></span> <span data-ttu-id="cbe68-141">Som standard är det här värdet 4 för att stödja 4 klienter på en gång.</span><span class="sxs-lookup"><span data-stu-id="cbe68-141">By default, this value is 4 to support 4 Clients at once.</span></span>

- <span data-ttu-id="cbe68-142">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: den minsta storleken på nytto lasten i byte för Server paketets pool, inklusive TCP-, IP-och nätverks ram-rubriker och http-data.</span><span class="sxs-lookup"><span data-stu-id="cbe68-142">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: The minimum size of the Server packet pool payload in bytes, including TCP, IP and network frame headers plus HTTP data.</span></span> <span data-ttu-id="cbe68-143">Standardvärdet är 256 (den maximala längden på filename i FileX) + 12 byte för fil information och NX_PHYSICAL_TRAILER.</span><span class="sxs-lookup"><span data-stu-id="cbe68-143">The default value is 256 (maximum length of filename in FileX) + 12 bytes for file information, and NX_PHYSICAL_TRAILER.</span></span>

- <span data-ttu-id="cbe68-144">**NX_FTP_NO_FILEX**: det här alternativet är ett stub-alternativ för FILEX-beroenden.</span><span class="sxs-lookup"><span data-stu-id="cbe68-144">**NX_FTP_NO_FILEX**: Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="cbe68-145">FTP-klienten fungerar utan några ändringar om det här alternativet har definierats.</span><span class="sxs-lookup"><span data-stu-id="cbe68-145">The FTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="cbe68-146">FTP-servern måste antingen ändras eller så måste användaren skapa en fåtal av FileX-tjänster för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="cbe68-146">The FTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>

- <span data-ttu-id="cbe68-147">**NX_FTP_CONTROL_TOS**: typ av tjänst som krävs för förfrågningar om FTP TCP-kontroll.</span><span class="sxs-lookup"><span data-stu-id="cbe68-147">**NX_FTP_CONTROL_TOS**: Type of service required for the FTP TCP control requests.</span></span> <span data-ttu-id="cbe68-148">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="cbe68-148">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="cbe68-149">Den här inställningen kan anges av programmet innan *nx_ftp. h*.</span><span class="sxs-lookup"><span data-stu-id="cbe68-149">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="cbe68-150">**NX_FTP_DATA_TOS**: typ av tjänst som krävs för FTP TCP-data begär Anden.</span><span class="sxs-lookup"><span data-stu-id="cbe68-150">**NX_FTP_DATA_TOS**: Type of service required for the FTP TCP data requests.</span></span> <span data-ttu-id="cbe68-151">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="cbe68-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="cbe68-152">Den här inställningen kan anges av programmet innan *nx_ftp. h*.</span><span class="sxs-lookup"><span data-stu-id="cbe68-152">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="cbe68-153">**NX_FTP_FRAGMENT_OPTION**: fragment aktivera för FTP TCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="cbe68-153">**NX_FTP_FRAGMENT_OPTION**: Fragment enable for FTP TCP requests.</span></span> <span data-ttu-id="cbe68-154">Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera FTP TCP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="cbe68-154">By default, this value is NX_DONT_FRAGMENT to disable FTP TCP fragmenting.</span></span> <span data-ttu-id="cbe68-155">Den här inställningen kan anges av programmet innan *nx_ftp. h*.</span><span class="sxs-lookup"><span data-stu-id="cbe68-155">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="cbe68-156">**NX_FTP_CONTROL_WINDOW_SIZE**: kontrol lera socket-fönstrets storlek.</span><span class="sxs-lookup"><span data-stu-id="cbe68-156">**NX_FTP_CONTROL_WINDOW_SIZE**: Control socket window size.</span></span> <span data-ttu-id="cbe68-157">Som standard är det här värdet 400 byte.</span><span class="sxs-lookup"><span data-stu-id="cbe68-157">By default, this value is 400 bytes.</span></span> <span data-ttu-id="cbe68-158">Den här inställningen kan anges av programmet innan *nx_ftp. h*.</span><span class="sxs-lookup"><span data-stu-id="cbe68-158">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="cbe68-159">**NX_FTP_DATA_WINDOW_SIZE**: storlek för datasocket window.</span><span class="sxs-lookup"><span data-stu-id="cbe68-159">**NX_FTP_DATA_WINDOW_SIZE**: Data socket window size.</span></span> <span data-ttu-id="cbe68-160">Som standard är det här värdet 2048 byte.</span><span class="sxs-lookup"><span data-stu-id="cbe68-160">By default, this value is 2048 bytes.</span></span> <span data-ttu-id="cbe68-161">Den här inställningen kan anges av programmet innan *nx_ftp. h*.</span><span class="sxs-lookup"><span data-stu-id="cbe68-161">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="cbe68-162">**NX_FTP_TIME_TO_LIVE**: anger antalet routrar som det här paketet kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="cbe68-162">**NX_FTP_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="cbe68-163">Standardvärdet är inställt på 0x80, men kan omdefinieras innan du tar med *nx_ftp. h.*</span><span class="sxs-lookup"><span data-stu-id="cbe68-163">The default value is set to 0x80, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="cbe68-164">**NX_FTP_SERVER_TIMEOUT**: anger antalet ThreadX-Tick som interna tjänster ska pausas för.</span><span class="sxs-lookup"><span data-stu-id="cbe68-164">**NX_FTP_SERVER_TIMEOUT**: Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="cbe68-165">Standardvärdet är inställt på 100, men kan omdefinieras innan *nx_ftp. h.*</span><span class="sxs-lookup"><span data-stu-id="cbe68-165">The default value is set to 100, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="cbe68-166">**NX_FTP_USERNAME_SIZE**: anger antalet byte som tillåts i en klient som har angett *användar namn*.</span><span class="sxs-lookup"><span data-stu-id="cbe68-166">**NX_FTP_USERNAME_SIZE**: Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="cbe68-167">Standardvärdet är inställt på 20, men kan omdefinieras innan *nx_ftp. h.*</span><span class="sxs-lookup"><span data-stu-id="cbe68-167">The default value is set to 20, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="cbe68-168">**NX_FTP_PASSWORD_SIZE**: anger antalet byte som tillåts i ett *lösen ord* som angetts av klienten.</span><span class="sxs-lookup"><span data-stu-id="cbe68-168">**NX_FTP_PASSWORD_SIZE**: Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="cbe68-169">Standardvärdet är inställt på 20, men kan omdefinieras innan *nx_ftp. h.*</span><span class="sxs-lookup"><span data-stu-id="cbe68-169">The default value is set to 20, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="cbe68-170">**NX_FTP_ACTIVITY_TIMEOUT**: anger antalet sekunder som en klient anslutning upprätthålls om det inte finns någon aktivitet.</span><span class="sxs-lookup"><span data-stu-id="cbe68-170">**NX_FTP_ACTIVITY_TIMEOUT**: Specifies the number of seconds a client connection is maintained if there is no activity.</span></span> <span data-ttu-id="cbe68-171">Standardvärdet är inställt på 240, men kan omdefinieras innan *nx_ftp. h.*</span><span class="sxs-lookup"><span data-stu-id="cbe68-171">The default value is set to 240, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="cbe68-172">**NX_FTP_TIMEOUT_PERIOD**: anger antalet sekunder mellan server kontrollen för inaktivitet i klienten.</span><span class="sxs-lookup"><span data-stu-id="cbe68-172">**NX_FTP_TIMEOUT_PERIOD**: Specifies the number of seconds between the Server checking for client inactivity.</span></span> <span data-ttu-id="cbe68-173">Standardvärdet är inställt på 60, men kan omdefinieras innan *nx_ftp. h.*</span><span class="sxs-lookup"><span data-stu-id="cbe68-173">The default value is set to 60, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>
