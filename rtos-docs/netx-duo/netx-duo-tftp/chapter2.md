---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo TFTP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ffb0c433bf1a5665e07da3cc6c240f1d0d8c87d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826997"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="adb7e-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="adb7e-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo TFTP</span></span>

<span data-ttu-id="adb7e-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo-komponenten.</span><span class="sxs-lookup"><span data-stu-id="adb7e-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo TFTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="adb7e-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="adb7e-105">Product Distribution</span></span>

<span data-ttu-id="adb7e-106">Azure återställnings tider NetX Duo kan hämtas från vår offentliga käll kods lagrings plats på https://github.com/azure-rtos/netxduo/ .</span><span class="sxs-lookup"><span data-stu-id="adb7e-106">Azure RTOS NetX Duo can be obtained from our public source code repository at https://github.com/azure-rtos/netxduo/.</span></span> <span data-ttu-id="adb7e-107">Paketet innehåller följande filer:</span><span class="sxs-lookup"><span data-stu-id="adb7e-107">The package includes the following files:</span></span>


- <span data-ttu-id="adb7e-108">**nxd_tftp_client. h** Rubrik fil för NetX Duo TFTP-klient</span><span class="sxs-lookup"><span data-stu-id="adb7e-108">**nxd_tftp_client.h** Header file for NetX Duo TFTP Client</span></span>

- <span data-ttu-id="adb7e-109">**nxd_tftp_client. c** C-källfil för NetX Duo TFTP-klient</span><span class="sxs-lookup"><span data-stu-id="adb7e-109">**nxd_tftp_client.c** C Source file for NetX Duo TFTP Client</span></span>

- <span data-ttu-id="adb7e-110">**nxd_tftp_server. h** Rubrik fil för NetX Duo TFTP-server</span><span class="sxs-lookup"><span data-stu-id="adb7e-110">**nxd_tftp_server.h** Header file for NetX Duo TFTP Server</span></span>

- <span data-ttu-id="adb7e-111">**nxd_tftp_server. c** C-källfil för NetX Duo TFTP-server</span><span class="sxs-lookup"><span data-stu-id="adb7e-111">**nxd_tftp_server.c** C Source file for NetX Duo TFTP Server</span></span>

- <span data-ttu-id="adb7e-112">**filex_stub. h** Stub-fil om FileX inte finns</span><span class="sxs-lookup"><span data-stu-id="adb7e-112">**filex_stub.h** Stub file if FileX is not present</span></span>

- <span data-ttu-id="adb7e-113">**nxd_tftp.pdf** PDF-Beskrivning av NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="adb7e-113">**nxd_tftp.pdf** PDF description of NetX Duo TFTP</span></span>

- <span data-ttu-id="adb7e-114">**demo_netxduo_tftp. c** NetX Duo TFTP-demonstration</span><span class="sxs-lookup"><span data-stu-id="adb7e-114">**demo_netxduo_tftp.c** NetX Duo TFTP demonstration</span></span>

## <a name="tftp-installation"></a><span data-ttu-id="adb7e-115">TFTP-installation</span><span class="sxs-lookup"><span data-stu-id="adb7e-115">TFTP Installation</span></span>

<span data-ttu-id="adb7e-116">Om du vill använda NetX Duo TFTP kan hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat.</span><span class="sxs-lookup"><span data-stu-id="adb7e-116">To use NetX Duo TFTP, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="adb7e-117">Om t. ex. NetX Duo är installerat i katalogen "*\threadx\arm7\green*" kan *nxd_tftp_client. h*-, *nxd_tftp_client. c*, *nxd_tftp_server. h* -och *nxd_tftp_server. c* -filer kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="adb7e-117">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_tftp_client.h*, *nxd_tftp_client.c*, *nxd_tftp_server.h* and *nxd_tftp_server.c* files could be copied into this directory.</span></span>

## <a name="using-tftp"></a><span data-ttu-id="adb7e-118">Använda TFTP</span><span class="sxs-lookup"><span data-stu-id="adb7e-118">Using TFTP</span></span>

<span data-ttu-id="adb7e-119">Om du vill köra ett TFTP-program måste program koden innehålla *nxd_tftp_client. h* och/eller nxd_tftp_server. h när den innehåller *tx_api. h, fx_api. h* och *nx_api. h*, för att kunna använda ThreadX, FileX och netx Duo.</span><span class="sxs-lookup"><span data-stu-id="adb7e-119">To run a TFTP application, the application code must include *nxd_tftp_client.h* and/or nxd_tftp_server.h after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="adb7e-120">Programprojektet måste också innehålla *nxd_tftp_client. c* och/eller *nxd_tftp_server. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="adb7e-120">The application project must also include *nxd_tftp_client.c* and/or *nxd_tftp_server.c* in the build process.</span></span> <span data-ttu-id="adb7e-121">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="adb7e-121">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="adb7e-122">Detta är allt som krävs för att använda NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="adb7e-122">This is all that is required to use NetX Duo TFTP.</span></span> <span data-ttu-id="adb7e-123">När *rubrik fil (er) har* inkluderats kan program koden använda TFTP-tjänster.</span><span class="sxs-lookup"><span data-stu-id="adb7e-123">Once *the header file(s) is* included, the application code is then able to use TFTP services.</span></span>

> [!NOTE]
> <span data-ttu-id="adb7e-124">Eftersom TFTP använder NetX Duo UDP-tjänster måste UDP aktive ras med det *nx_udp_enable* samtalet innan TFTP används.</span><span class="sxs-lookup"><span data-stu-id="adb7e-124">Since TFTP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using TFTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="adb7e-125">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="adb7e-125">Small Example System</span></span>

<span data-ttu-id="adb7e-126">Ett exempel på hur enkelt det är att använda NetX Duo TFTP beskrivs i bild 1,1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="adb7e-126">An example of how easy it is to use NetX Duo TFTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="adb7e-127">I det här exemplet tas filen *nxd_tftp_client. h* och *nxd_tftp_server. h* in på rad 19 och 20.</span><span class="sxs-lookup"><span data-stu-id="adb7e-127">In this example, the TFTP include file *nxd_tftp_client.h* and *nxd_tftp_server.h* are brought in at line 19 and 20.</span></span> <span data-ttu-id="adb7e-128">Sedan skapas TFTP-servern i "*tx_application_define*" på rad 179.</span><span class="sxs-lookup"><span data-stu-id="adb7e-128">Next, the TFTP Server is created in “*tx_application_define*” at line 179.</span></span> 

> [!NOTE]
> <span data-ttu-id="adb7e-129">TFTP-serverns kontroll block "*Server*" definierades som en global variabel på rad 45 tidigare.</span><span class="sxs-lookup"><span data-stu-id="adb7e-129">The TFTP Server control block “*server*” was defined as a global variable at line 45 previously.</span></span> <span data-ttu-id="adb7e-130">Den här demon väljer att använda IPv4 för sin TFTP-kommunikation på rad 14.</span><span class="sxs-lookup"><span data-stu-id="adb7e-130">This demo chooses to use IPv4 for its TFTP communication in line 14.</span></span> <span data-ttu-id="adb7e-131">När du har skapat den startas TFTP-servern på rad 304.</span><span class="sxs-lookup"><span data-stu-id="adb7e-131">After successful creation, the TFTP Server is started at line 304.</span></span> <span data-ttu-id="adb7e-132">På rad 411 har TFTP-klienten skapats.</span><span class="sxs-lookup"><span data-stu-id="adb7e-132">At line 411 the TFTP Client is created.</span></span> <span data-ttu-id="adb7e-133">Slutligen skriver klienten filen på rad 450 och läser tillbaka filen på rad 485.</span><span class="sxs-lookup"><span data-stu-id="adb7e-133">And finally, the Client writes the file at line 450 and reads the file back at line 485.</span></span>

<span data-ttu-id="adb7e-134">TFTP-serverns tråd aktivitet stoppas och TFTP-servern tas bort på rad 324.</span><span class="sxs-lookup"><span data-stu-id="adb7e-134">The TFTP server thread task is stopped and the TFTP Server is deleted on line 324.</span></span> <span data-ttu-id="adb7e-135">Programmet bör anropa fx_media_close (rad 331) för att stänga alla filer och uppdatera fil-och katalog data till USB-mediet.</span><span class="sxs-lookup"><span data-stu-id="adb7e-135">The application should call fx_media_close (line 331) to close all files and update file and directory data to the USB media.</span></span>

> [!NOTE]
> <span data-ttu-id="adb7e-136">I det här exemplet används FileX för hantering av TFTP-servrar för att ta emot och hämta TFTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="adb7e-136">This example uses FileX for the TFTP Server handling of receiving and downloading TFTP Client file requests.</span></span> <span data-ttu-id="adb7e-137">Men om NX_TFTP_NO_FILEX har definierats kan programmet innehålla file_stub. h i stället för fx_api. h.</span><span class="sxs-lookup"><span data-stu-id="adb7e-137">However, if NX_TFTP_NO_FILEX is defined, the application can include file_stub.h instead of fx_api.h.</span></span>
>
> <span data-ttu-id="adb7e-138">Observera också att befintliga NetX TFTP-klienter och serverprogram fungerar med NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="adb7e-138">Also note that existing NetX TFTP client and server applications will work with NetX Duo TFTP.</span></span> <span data-ttu-id="adb7e-139">Programutvecklaren uppmanas dock att Porta sina NetX TFTP-program till NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="adb7e-139">However, the application developer is encouraged to port their NetX TFTP applications to NetX Duo.</span></span> <span data-ttu-id="adb7e-140">Motsvarande NetX TFTP-tjänster är:</span><span class="sxs-lookup"><span data-stu-id="adb7e-140">The equivalent NetX TFTP services are:</span></span>

- <span data-ttu-id="adb7e-141">*nxd_tftp_server_start*</span><span class="sxs-lookup"><span data-stu-id="adb7e-141">*nxd_tftp_server_start*</span></span>

- <span data-ttu-id="adb7e-142">*nxd_tftp_server_stop*</span><span class="sxs-lookup"><span data-stu-id="adb7e-142">*nxd_tftp_server_stop*</span></span>

- <span data-ttu-id="adb7e-143">*nxd_tftp_client_file_read*</span><span class="sxs-lookup"><span data-stu-id="adb7e-143">*nxd_tftp_client_file_read*</span></span>

- <span data-ttu-id="adb7e-144">*nxd_tftp_client_file_write*</span><span class="sxs-lookup"><span data-stu-id="adb7e-144">*nxd_tftp_client_file_write*</span></span>

- <span data-ttu-id="adb7e-145">*nxd_tftp_client_file_open*</span><span class="sxs-lookup"><span data-stu-id="adb7e-145">*nxd_tftp_client_file_open*</span></span>

```C
/* This is a small demo of TFTP on the high-performance NetX TCP/IP stack. This demo
   relies on ThreadX and NetX Duo, to show a simple file transfer from the client
   and then back to the server. */



/* Indicate if using IPv6. */
#define USE_DUO

/* If the host application is using NetX Duo, determine which IP version to use.
   Make sure IPv6 in NetX Duo is enabled if planning to use TFTP over IPv6 */
#ifdef USE_DUO
#define     IP_TYPE     6
#endif /* USE_DUO        */

#include    "tx_api.h"
#include    "nx_api.h"
#include    "nxd_tftp_client.h"
#include    "nxd_tftp_server.h"
#ifndef     NX_TFTP_NO_FILEX
#include    "fx_api.h"
#endif


#define     DEMO_STACK_SIZE         4096

/* To use another file storage utility define this symbol:
#define NX_TFTP_NO_FILEX
*/

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;

/* Define the NetX TFTP object control blocks. */

NX_TFTP_CLIENT          client;
NX_TFTP_SERVER          server;

/* Define the application global variables */

#define                 CLIENT_ADDRESS  IP_ADDRESS(1, 2, 3, 5)
#define                 SERVER_ADDRESS  IP_ADDRESS(1, 2, 3, 4)

NXD_ADDRESS             server_ip_address;
NXD_ADDRESS             client_ip_address;

UINT                    error_counter = 0;

/* Define buffer used in the demo application. */
UCHAR                   buffer[255];
ULONG                   data_length;


/* Define the memory area for the FileX RAM disk. */
#ifndef NX_TFTP_NO_FILEX
UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];
#endif


/* Define function prototypes. */

VOID    _fx_ram_driver(FX_MEDIA *media_ptr);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
void    client_thread_entry(ULONG thread_input);
void    server_thread_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;
UCHAR   *pointer;


    /* Setup the working pointer. */
    pointer =  (UCHAR *) first_unused_memory;


    /* Create the main TFTP server thread. */
    status = tx_thread_create(&server_thread, "TFTP Server Thread", server_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              4,4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the main TFTP client thread at a slightly lower priority. */
    status = tx_thread_create(&client_thread, "TFTP Client Thread", client_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              5, 5, TX_NO_TIME_SLICE, TX_DONT_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&server_pool, "TFTP Server Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the TFTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&server_ip);

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the TFTP server. */
#ifdef USE_DUO
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
    /* Specify the tftp server global address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x102;
#endif
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_ADDRESS;

#endif

    status =  nxd_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#else
    status =  nx_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#endif

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for errors for the server. */
    if (status)
        error_counter++;

    /* Create a packet pool for the TFTP client. */

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&client_pool, "TFTP Client Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the TFTP client. */
    status = nx_ip_create(&client_ip, "TFTP Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable UDP for client IP instance. */
    status |=  nx_udp_enable(&client_ip);
    status |= nx_icmp_enable(&client_ip);

    tx_thread_resume(&client_thread);
}

void server_thread_entry(ULONG thread_input)
{

UINT        status, running;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#ifndef  NX_TFTP_NO_FILEX

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry             */
                            ram_disk_memory,                 /* RAM disk memory pointer  */
                            ram_disk_sector_cache,           /* Media buffer pointer     */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size        */
                            "MY_RAM_DISK",                   /* Volume Name              */
                            1,                               /* Number of FATs           */
                            32,                              /* Directory Entries        */
                            0,                               /* Hidden sectors           */
                            256,                            /* Total sectors            */
                            128,                             /* Sector size              */
                            1,                               /* Sectors per cluster      */
                            1,                               /* Heads                    */
                            1);                              /* Sectors per track        */

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory, ram_disk_sector_cache,
                               sizeof(ram_disk_sector_cache));

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

#endif /*  NX_TFTP_NO_FILEX */

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ICMPv6 services. */
    status |= nxd_icmp_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the server. */
    status = nxd_ipv6_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for DAD to validate the address. */
    tx_thread_sleep(500);
#endif

#endif /* IP_TYPE == 6 */

    /* Start the NetX TFTP server. */
#ifdef USE_DUO
    status =  nxd_tftp_server_start(&server);
#else
    status =  nx_tftp_server_start(&server);
#endif

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Run for a while */
    running = NX_TRUE;
    while(running)
        tx_thread_sleep(200);


    /* Stop and delete the TFTP server. */
#ifdef USE_DUO
    nxd_tftp_server_delete(&server);
#else
    nx_tftp_server_delete(&server);
#endif

    /* Close all open files and ensure directory information is also written out to the media.
    This will also flush the file data to USB media*/
    status = fx_media_close(&ram_disk);

    if (status)
    {
        error_counter++;
    }

    return;

}


/* Define the TFTP client thread. */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
UINT        all_done = NX_FALSE;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ECMPv6 services for the client. */
    status = nxd_icmp_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the client. */
    status = nxd_ipv6_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the Client IPv6 address */
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_address.v6[1] = 0xf101;
    client_ip_address.nxd_ip_address.v6[2] = 0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for the link local and global addresses to be validated. */
    tx_thread_sleep(500);
#endif
#endif /*(IP_TYPE == 6) */


    /* The TFTP services used below include the NetX equivalent service which will work with
       NetX Duo TFTP. However, it is recommended for developers to port their applications
       to the newer services that take the NXD_ADDRESS type and support both IPv4 and IPv6
       communication.
    */

    /* Create a TFTP client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool, IP_TYPE);
#else
    status =  nx_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool);
#endif

    /* Check status. */
    if (status)
        return;

    /* Open a TFTP file for writing. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_WRITE, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_WRITE, 100);
#endif

    /* Check status. */
    if (status)
        return;

    /* Allocate a TFTP packet. */
#ifdef USE_DUO
    status =  nxd_tftp_client_packet_allocate(&client_pool, &my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_packet_allocate(&client_pool, &my_packet, 100);
#endif
    /* Check status. */
    if (status)
        error_counter++;

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write this packet to the file via TFTP. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_write(&client, my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_write(&client, my_packet, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Close this file. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Open the same file for reading. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_READ, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_READ, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;
    do
    {

    /* Read the file back. */
#ifdef USE_DUO
        status =  nxd_tftp_client_file_read(&client, &my_packet, 100, IP_TYPE);
#else
        status =  nx_tftp_client_file_read(&client, &my_packet, 100);
#endif
        /* Check for retranmission/dropped packet error. Benign. Try again... */
        if (status == NX_TFTP_INVALID_BLOCK_NUMBER)
        {

            continue;
        }
        else if (status == NX_TFTP_END_OF_FILE)
        {

            /* All done. */
            all_done = NX_TRUE;
        }
        else if (status != NX_SUCCESS)
        {

            /* Internal error, invalid packet or error on read. */
            break;
        }


        /* Do something with the packet data and release when done. */
        nx_packet_data_retrieve(my_packet, buffer, &data_length);
        buffer[data_length] = 0;
        printf("Receive data: %s\n", buffer);

        printf("release packet in demo.\n");

        nx_packet_release(my_packet);

    } while (all_done == NX_FALSE);

    /* Close the file again. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Delete the client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_delete(&client);
#else
    status =  nx_tftp_client_delete(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    return;
}
```

<span data-ttu-id="adb7e-146">Figur 1,1 exempel på TFTP-användning med NetX Duo</span><span class="sxs-lookup"><span data-stu-id="adb7e-146">Figure 1.1 Example of TFTP use with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="adb7e-147">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="adb7e-147">Configuration Options</span></span>

<span data-ttu-id="adb7e-148">Det finns flera konfigurations alternativ för att skapa NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="adb7e-148">There are several configuration options for building NetX Duo TFTP.</span></span> <span data-ttu-id="adb7e-149">I följande lista beskrivs var och en i detalj.</span><span class="sxs-lookup"><span data-stu-id="adb7e-149">The following list describes each in detail.</span></span> <span data-ttu-id="adb7e-150">Om inget annat anges finns de här alternativen i *nxd_tftp_client. h* och *nxd_tftp_server. h*.</span><span class="sxs-lookup"><span data-stu-id="adb7e-150">Unless otherwise specified, these options are found in *nxd_tftp_client.h* and *nxd_tftp_server.h*.</span></span>


- <span data-ttu-id="adb7e-151">**NX_DISABLE_ERROR_CHECKING** Definierad, tar det här alternativet bort grundläggande TFTP-felkontroll.</span><span class="sxs-lookup"><span data-stu-id="adb7e-151">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic TFTP error checking.</span></span> <span data-ttu-id="adb7e-152">Den används vanligt vis när programmet har felsökts.</span><span class="sxs-lookup"><span data-stu-id="adb7e-152">It is typically used after the application has been debugged.</span></span>

- <span data-ttu-id="adb7e-153">**NX_TFTP_SERVER_PRIORITY** Prioriteten för TFTP-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="adb7e-153">**NX_TFTP_SERVER_PRIORITY** The priority of the TFTP server thread.</span></span> <span data-ttu-id="adb7e-154">Som standard definieras värdet som 16 för att ange prioritet 16.</span><span class="sxs-lookup"><span data-stu-id="adb7e-154">By default, this value is defined as 16 to specify priority 16.</span></span>

- <span data-ttu-id="adb7e-155">**NX_TFTP_SERVER_TIME_SLICE** Tids sektorn för TFTP-servern som ska köras innan den ger andra trådar av samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="adb7e-155">**NX_TFTP_SERVER_TIME_SLICE** The time slice for the TFTP Server to run before yielding to other threads of the same priority.</span></span> <span data-ttu-id="adb7e-156">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="adb7e-156">The default value is 2.</span></span>

- <span data-ttu-id="adb7e-157">**NX_TFTP_MAX_CLIENTS** Det maximala antalet klienter som servern kan hantera på en och samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="adb7e-157">**NX_TFTP_MAX_CLIENTS** The maximum number of clients the server can handle at one time.</span></span> <span data-ttu-id="adb7e-158">Som standard är det här värdet 10 för att stödja 10 klienter samtidigt.</span><span class="sxs-lookup"><span data-stu-id="adb7e-158">By default, this value is 10 to support 10 clients at once.</span></span>

- <span data-ttu-id="adb7e-159">**NX_TFTP_ERROR_STRING_MAX** Det maximala antalet tecken i fel strängen.</span><span class="sxs-lookup"><span data-stu-id="adb7e-159">**NX_TFTP_ERROR_STRING_MAX** The maximum number of characters in the error string.</span></span> <span data-ttu-id="adb7e-160">Som standard är det här värdet 64.</span><span class="sxs-lookup"><span data-stu-id="adb7e-160">By default, this value is 64.</span></span>

- <span data-ttu-id="adb7e-161">**NX_TFTP_NO_FILEX** Definierad är det här alternativet en stub för FileX-beroenden.</span><span class="sxs-lookup"><span data-stu-id="adb7e-161">**NX_TFTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="adb7e-162">TFTP-klienten fungerar utan några ändringar om det här alternativet har definierats.</span><span class="sxs-lookup"><span data-stu-id="adb7e-162">The TFTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="adb7e-163">TFTP-servern måste antingen ändras eller så måste användaren skapa en fåtal av FileX-tjänster för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="adb7e-163">The TFTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>

- <span data-ttu-id="adb7e-164">**NX_TFTP_TYPE_OF_SERVICE** Typ av tjänst som krävs för TFTP UDP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="adb7e-164">**NX_TFTP_TYPE_OF_SERVICE** Type of service required for the TFTP UDP requests.</span></span> <span data-ttu-id="adb7e-165">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="adb7e-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>

- <span data-ttu-id="adb7e-166">**NX_TFTP_FRAGMENT_OPTION** Fragment aktivera för TFTP UDP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="adb7e-166">**NX_TFTP_FRAGMENT_OPTION** Fragment enable for TFTP UDP requests.</span></span> <span data-ttu-id="adb7e-167">Som standard är det här värdet NX_DONT_FRAGMENT att inaktivera TFTP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="adb7e-167">By default, this value is NX_DONT_FRAGMENT to disable TFTP UDP fragmenting.</span></span>

- <span data-ttu-id="adb7e-168">**NX_TFTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="adb7e-168">**NX_TFTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="adb7e-169">Standardvärdet är inställt på 0x80.</span><span class="sxs-lookup"><span data-stu-id="adb7e-169">The default value is set to 0x80.</span></span>

- <span data-ttu-id="adb7e-170">**NX_TFTP_SOURCE_PORT** Med det här alternativet kan du använda ett TFTP-klientcertifikat för att ange TFTP-klientens UDP-socket-port.</span><span class="sxs-lookup"><span data-stu-id="adb7e-170">**NX_TFTP_SOURCE_PORT** This option allows a TFTP Client application to specify the TFTP Client UDP socket port.</span></span> <span data-ttu-id="adb7e-171">Standardvärdet är NX_ANY_PORT.</span><span class="sxs-lookup"><span data-stu-id="adb7e-171">It is defaulted to NX_ANY_PORT.</span></span>

- <span data-ttu-id="adb7e-172">***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** Aktiverar TFTP-serverns timer för att kontrol lera varje TFTP-klientsession med för senaste aktivitet (antingen ett ACK-eller data paket).</span><span class="sxs-lookup"><span data-stu-id="adb7e-172">***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** Enables the TFTP server’s timer to check each TFTP client session with for recent activity (either an ACK or data packet).</span></span> <span data-ttu-id="adb7e-173">När tids gränsen för sessionen upphör att gälla efter det maximala antalet gånger, antas anslutningen förloras.</span><span class="sxs-lookup"><span data-stu-id="adb7e-173">When the session timeout expires after the maximum number of times, it is assumed the connection was lost.</span></span> <span data-ttu-id="adb7e-174">Servern rensar klientbegäran, stänger alla öppna filer och gör anslutnings förfrågan tillgänglig för nästa klient.</span><span class="sxs-lookup"><span data-stu-id="adb7e-174">The Server clears the Client request, closes any open files and makes the connection request available for the next Client.</span></span> <span data-ttu-id="adb7e-175">Standardinställningen är inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="adb7e-175">The default setting is disabled.</span></span>

- <span data-ttu-id="adb7e-176">**NX_TFTP_SERVER_TIMEOUT_PERIOD** Anger det intervall som ska användas när funktionen för tidsinställd TFTP-server kontrollerar klient anslutningar för att ta emot paket.</span><span class="sxs-lookup"><span data-stu-id="adb7e-176">**NX_TFTP_SERVER_TIMEOUT_PERIOD** Specifies the interval when the TFTP server timer entry function checks Client connections for receiving any packets.</span></span> <span data-ttu-id="adb7e-177">Standardvärdet är 20 (timer-Tick).</span><span class="sxs-lookup"><span data-stu-id="adb7e-177">The default value is 20 (timer ticks).</span></span>

- <span data-ttu-id="adb7e-178">**NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** Detta är tids gränsen för att ta emot ett giltigt ACK-eller data paket från klienten.</span><span class="sxs-lookup"><span data-stu-id="adb7e-178">**NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** This is the timeout for receiving a valid ACK or data packet from the Client.</span></span> <span data-ttu-id="adb7e-179">Standardvärdet är 200 (timer-Tick)*.*</span><span class="sxs-lookup"><span data-stu-id="adb7e-179">The default value is 200 (timer ticks)*.*</span></span>

- <span data-ttu-id="adb7e-180">**NX_TFTP_SERVER_MAX_RETRIES** Anger det maximala antalet gånger som tids gränsen för klient sessions överföring förnyas.</span><span class="sxs-lookup"><span data-stu-id="adb7e-180">**NX_TFTP_SERVER_MAX_RETRIES** Specifies the maximum number of times the Client session retransmit timeout is renewed.</span></span> <span data-ttu-id="adb7e-181">Därefter stängs sessionen av servern.</span><span class="sxs-lookup"><span data-stu-id="adb7e-181">Thereafter, the session is closed by the Server.</span></span>

- <span data-ttu-id="adb7e-182">**NX_TFTP_MAX_CLIENT_RETRANSMITS** Anger det maximala antalet gånger som servern får ett dubbelt ACK-eller data paket från klienten (som den tappas) utan att skicka ett fel meddelande till klienten och stänga sessionen.</span><span class="sxs-lookup"><span data-stu-id="adb7e-182">**NX_TFTP_MAX_CLIENT_RETRANSMITS** Specifies the maximum number of times the Server receives a duplicate ACK or data packet from the Client (which it drops) without sending an error message to the Client and closing the session.</span></span> <span data-ttu-id="adb7e-183">Har ingen påverkan om NX_TFTP_SERVER_RETRANSMIT_ENABLE har definierats.</span><span class="sxs-lookup"><span data-stu-id="adb7e-183">Has no effect if NX_TFTP_SERVER_RETRANSMIT_ENABLE is defined.</span></span>
