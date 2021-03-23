---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo SNTP-klienten
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo SNTP-klienten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd917e7e70ce21dbff6c8081c2ff115c0acad8a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825749"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a><span data-ttu-id="3d798-103">Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo SNTP-klienten</span><span class="sxs-lookup"><span data-stu-id="3d798-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo SNTP Client</span></span>

<span data-ttu-id="3d798-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3d798-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo SNTP Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="3d798-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="3d798-105">Product Distribution</span></span>

<span data-ttu-id="3d798-106">SNTP för NetX Duo finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="3d798-106">SNTP for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="3d798-107">Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="3d798-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="3d798-108">**nxd_sntp_client. c** SNTP-klient C-källfil</span><span class="sxs-lookup"><span data-stu-id="3d798-108">**nxd_sntp_client.c** SNTP Client C source file</span></span>  
- <span data-ttu-id="3d798-109">**nxd_sntp_client. h** SNTP-klientens huvud fil</span><span class="sxs-lookup"><span data-stu-id="3d798-109">**nxd_sntp_client.h** SNTP Client Header file</span></span>  
- <span data-ttu-id="3d798-110">**demo_netxduo_sntp_client. c** Demonstrations paket för SNTP-klient</span><span class="sxs-lookup"><span data-stu-id="3d798-110">**demo_netxduo_sntp_client.c** Demonstration SNTP Client application</span></span>  
- <span data-ttu-id="3d798-111">**nxd_sntp_client.pdf** Användar handbok för NetX Duo SNTP-klienten</span><span class="sxs-lookup"><span data-stu-id="3d798-111">**nxd_sntp_client.pdf** NetX Duo SNTP Client User Guide</span></span>  

## <a name="netx-duo-sntp-client-installation"></a><span data-ttu-id="3d798-112">Installation av NetX Duo SNTP-klient</span><span class="sxs-lookup"><span data-stu-id="3d798-112">NetX Duo SNTP Client Installation</span></span>

<span data-ttu-id="3d798-113">För att du ska kunna använda SNTP för NetX Duo, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat.</span><span class="sxs-lookup"><span data-stu-id="3d798-113">In order to use SNTP for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="3d798-114">Om t. ex. NetX Duo installeras i katalogen "*\threadx\arm7\green*", ska netx Duo SNTP- *nxd_sntp_client. c* och *nxd_sntp_client. h* (*nx_sntp_client. c* och *nx_sntp_client. h* i netx) kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="3d798-114">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the NetX Duo SNTP Client files *nxd_sntp_client.c* and *nxd_sntp_client.h* (*nx_sntp_client.c* and *nx_sntp_client.h* in NetX) should be copied into this directory.</span></span>

## <a name="using-netx-duo-sntp-client"></a><span data-ttu-id="3d798-115">Använda NetX Duo SNTP-klienten</span><span class="sxs-lookup"><span data-stu-id="3d798-115">Using NetX Duo SNTP Client</span></span>

<span data-ttu-id="3d798-116">Det är enkelt att använda NetX Duo SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3d798-116">Using NetX Duo SNTP Client is easy.</span></span> <span data-ttu-id="3d798-117">I princip måste program koden innehålla *nxd_sntp_client. h* när den innehåller *tx_api. h, fx_api. h* , och *nx_api. h*, för att kunna använda ThreadX respektive netx Duo.</span><span class="sxs-lookup"><span data-stu-id="3d798-117">Basically, the application code must include *nxd_sntp_client.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="3d798-118">När *nxd_sntp_client. h* ingår kan program koden sedan göra de SNTP-funktions anrop som anges senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="3d798-118">Once *nxd_sntp_client.h* is included, the application code is then able to make the SNTP function calls specified later in this guide.</span></span> <span data-ttu-id="3d798-119">Programmet måste även innehålla *nxd_sntp_client. c* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="3d798-119">The application must also include *nxd_sntp_client.c* in the build process.</span></span> <span data-ttu-id="3d798-120">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="3d798-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="3d798-121">Detta är allt som krävs för att använda NetX Duo SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3d798-121">This is all that is required to use NetX Duo SNTP Client.</span></span>

> [!NOTE]
> <span data-ttu-id="3d798-122">Eftersom NetX Duo SNTP-klienten använder NetX Duo UDP-tjänster måste UDP aktive ras med *nx_udp_enable* anrop innan SNTP-tjänster används.</span><span class="sxs-lookup"><span data-stu-id="3d798-122">Since the NetX Duo SNTP Client utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using SNTP services.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="3d798-123">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="3d798-123">Small Example System</span></span>

<span data-ttu-id="3d798-124">Ett exempel på hur du använder NetX Duo SNTP visas nedan.</span><span class="sxs-lookup"><span data-stu-id="3d798-124">An example of how to use NetX Duo SNTP is shown below.</span></span> <span data-ttu-id="3d798-125">Observera att det här exemplet **inte** garanterat fungerar som det är i systemet.</span><span class="sxs-lookup"><span data-stu-id="3d798-125">Note that this example is **not** guaranteed to work as is on your system.</span></span> <span data-ttu-id="3d798-126">Du kan behöva göra justeringar för din specifika system-och maskin vara.</span><span class="sxs-lookup"><span data-stu-id="3d798-126">You may need to make adjustments for your particular system and hardware.</span></span> <span data-ttu-id="3d798-127">Till exempel måste du ersätta NetX ram-drivrutinen med din faktiska driv rutins funktion.</span><span class="sxs-lookup"><span data-stu-id="3d798-127">For example you will have to replace the NetX ram driver with your actual driver function.</span></span> <span data-ttu-id="3d798-128">Det här exemplet är endast avsett för demonstrations ändamål.</span><span class="sxs-lookup"><span data-stu-id="3d798-128">This example is intended strictly for demonstration purposes.</span></span>

<span data-ttu-id="3d798-129">I det här exemplet ingår SNTP-huvudfilen *nxd_sntp_client. h* .</span><span class="sxs-lookup"><span data-stu-id="3d798-129">In this example, the SNTP header file *nxd_sntp_client.h* is included.</span></span> <span data-ttu-id="3d798-130">SNTP-klienten skapas i "*tx_application_define*".</span><span class="sxs-lookup"><span data-stu-id="3d798-130">The SNTP Client is created in “*tx_application_define*”.</span></span> <span data-ttu-id="3d798-131">Observera att kyss för döden och andras andra hanterare är valfria när du skapar SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3d798-131">Note that the kiss of death and leap second handler functions are optional when creating the SNTP Client.</span></span>

<span data-ttu-id="3d798-132">Den här demon kan användas med IPv6 eller IPv4.</span><span class="sxs-lookup"><span data-stu-id="3d798-132">This demo can be used with IPv6 or IPv4.</span></span> <span data-ttu-id="3d798-133">Om du vill köra SNTP-klienten via IPv6 definierar du USE_IPV6.</span><span class="sxs-lookup"><span data-stu-id="3d798-133">To run the SNTP Client over IPv6, define USE_IPV6.</span></span> <span data-ttu-id="3d798-134">IPv6 måste också vara aktiverat i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3d798-134">IPv6 must be enabled in NetX Duo as well.</span></span> <span data-ttu-id="3d798-135">SNTP-klientens värd konfigureras för IPv6-adress validering och ICMPv6-och IPv6-tjänster i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3d798-135">The SNTP Client host is set up for IPv6 address validation and ICMPv6 and IPv6 services in NetX Duo.</span></span> <span data-ttu-id="3d798-136">I användar handboken för NetX Duo finns mer information om IPv6-stöd i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3d798-136">See the NetX Duo User Guide for more details on IPv6 support in NetX Duo.</span></span>

<span data-ttu-id="3d798-137">Sedan måste SNTP-klienten initieras för antingen unicast-eller broadcast-läge.</span><span class="sxs-lookup"><span data-stu-id="3d798-137">Then the SNTP Client must be initialized for either unicast or broadcast mode.</span></span>

<span data-ttu-id="3d798-138">SNTP-klienten skriver inlednings vis uppdateringar av Server tiden till sin egen interna data struktur.</span><span class="sxs-lookup"><span data-stu-id="3d798-138">SNTP Client initially writes Server time updates to its own internal data structure.</span></span> <span data-ttu-id="3d798-139">Detta är inte samma som lokal tid för enheten.</span><span class="sxs-lookup"><span data-stu-id="3d798-139">This is not the same as the device local time.</span></span> <span data-ttu-id="3d798-140">Enhetens lokala tid kan anges som en bas linje i SNTP-klienten innan du startar klient tråden för SNTP.</span><span class="sxs-lookup"><span data-stu-id="3d798-140">The device local time can be set as a baseline time in the SNTP Client before starting the SNTP Client thread.</span></span> <span data-ttu-id="3d798-141">Detta är användbart om SNTP-klienten är konfigurerad (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP inställd på NX_FALSE) för att jämföra den första Server uppdateringen med NX_SNTP_CLIENT_MAX_ADJUSTMENT (standardvärdet 180 millisekunder).</span><span class="sxs-lookup"><span data-stu-id="3d798-141">This is useful if the SNTP Client is configured (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP set to NX_FALSE) to compare the first Server update to the NX_SNTP_CLIENT_MAX_ADJUSTMENT (default value 180 milliseconds).</span></span> <span data-ttu-id="3d798-142">Annars ställer SNTP-klienten in den första lokala tiden direkt när den hämtar den första uppdateringen från servern.</span><span class="sxs-lookup"><span data-stu-id="3d798-142">Otherwise the SNTP Client will set the initial local time directly when it gets the first update from the Server.</span></span>

<span data-ttu-id="3d798-143">En bas linje tid som tillämpas på SNTP-klienten med hjälp av tjänsten *nx_sntp_client_set_local_time* .</span><span class="sxs-lookup"><span data-stu-id="3d798-143">A baseline time is applied to the SNTP Client using the *nx_sntp_client_set_local_time* service.</span></span>

<span data-ttu-id="3d798-144">SNTP-klienten startas på för unicast-och sändnings läge.</span><span class="sxs-lookup"><span data-stu-id="3d798-144">The SNTP Client is started on for unicast and broadcast mode respectively.</span></span> <span data-ttu-id="3d798-145">För ett visst intervall (något lägre än unicast avsöknings intervall) uppdaterar programmet SNTP-klientens lokala tid, med hjälp av *nx_sntp_client_set_local_time*, från "real tids klocka" som vi simulerar genom att bara öka antalet sekunder och millisekunder av den aktuella tiden.</span><span class="sxs-lookup"><span data-stu-id="3d798-145">For a certain interval (slightly less than the unicast polling interval) the application updates the SNTP Client local time, using the *nx_sntp_client_set_local_time*, from the “real time clock” which we simulate by just incrementing the seconds and milliseconds of the current time.</span></span> <span data-ttu-id="3d798-146">Efter varje intervall söker programmet regelbundet efter uppdateringar från SNTP-servern.</span><span class="sxs-lookup"><span data-stu-id="3d798-146">After each interval, the application then periodically checks for updates from the SNTP server.</span></span> <span data-ttu-id="3d798-147">Tjänsten *nx_sntp_client_receiving _updates* verifierar att SNTP-klienten för närvarande tar emot giltiga uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="3d798-147">The *nx_sntp_client_receiving _updates* service verifies that the SNTP Client is currently receiving valid updates.</span></span> <span data-ttu-id="3d798-148">I så fall hämtas den senaste uppdaterings tiden med hjälp av tjänsten *nx_sntp_client_get_local_time_extended* .</span><span class="sxs-lookup"><span data-stu-id="3d798-148">If so, it will retrieve the latest update time using the *nx_sntp_client_get_local_time_extended* service.</span></span>

<span data-ttu-id="3d798-149">SNTP-klienten kan stoppas när som helst med hjälp av *nx_sntp_client_stops* tjänsten, om till exempel identifierar att SNTP-klienten inte längre tar emot giltiga uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="3d798-149">The SNTP Client can be stopped at any time using the *nx_sntp_client_stop* service if for example it detects the SNTP Client is no longer receiving valid updates..</span></span> <span data-ttu-id="3d798-150">För att starta om klienten måste programmet anropa antingen unicast-eller Broadcast-initierings tjänsten och sedan anropa antingen unicast-eller broadcast-körnings tjänster.</span><span class="sxs-lookup"><span data-stu-id="3d798-150">To restart the Client, the application must call either the unicast or broadcast initialize service and then call either unicast or broadcast run services.</span></span> <span data-ttu-id="3d798-151">När klient tråds aktiviteten för SNTP stoppas, kan SNTP-klienten växla SNTP-servrar och-lägen (unicast eller broadcast) om det behövs, t. ex. att den tidigare SNTP-servern verkar vara avstängd.</span><span class="sxs-lookup"><span data-stu-id="3d798-151">While the SNTP Client thread task is stopped, the SNTP Client can switch SNTP servers and modes (unicast or broadcast) if needed e.g. the previous SNTP server appears to be down.</span></span>

```c
/* 
   This is a small demo of the NetX SNTP Client on the high-performance NetX
   TCP/IP stack. This demo relies on Thread, NetX and NetX SNTP Client API to
   execute the Simple Network Time Protocol in unicast and broadcast modes.  
 */

#include <stdio.h>
#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_sntp_client.h"
                
/* Define SNTP packet size. */
#define NX_SNTP_CLIENT_PACKET_SIZE      (NX_UDP_PACKET + 100)

/* Define SNTP packet pool size. */
#define NX_SNTP_CLIENT_PACKET_POOL_SIZE      (4 * (NX_SNTP_CLIENT_PACKET_SIZE + 
                                                            sizeof(NX_PACKET)))

/* Define how often the demo checks for SNTP updates. */
#define DEMO_PERIODIC_CHECK_INTERVAL      (1 * NX_IP_PERIODIC_RATE) 

/* Define how often we check on SNTP server status. 
   We expect updates from the SNTP server about every hour using 
   the SNTP Client defaults. For testing
   make this (much) shorter. */
#define CHECK_SNTP_UPDATES_TIMEOUT       (180 * NX_IP_PERIODIC_RATE) 

/* Set up generic network driver for demo program. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Application defined services of the NetX SNTP Client. */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator);
UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, 
                                        UINT KOD_code);
VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time);


/* Set up client thread and network resources. */

NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;
TX_THREAD           demo_client_thread;
NX_SNTP_CLIENT      demo_sntp_client;
TX_EVENT_FLAGS_GROUP sntp_flags;

#define DEMO_SNTP_UPDATE_EVENT  1

/* Configure the SNTP Client to use IPv6. If not enabled, the 
   Client will use IPv4.  Note: IPv6 must be enabled in NetX Duo
   for the Client to communicate over IPv6.    */
#ifdef FEATURE_NX_IPV6
/* #define USE_IPV6 */
#endif /* FEATURE_NX_IPV6 */


/* Configure the SNTP Client to use unicast SNTP. */
#define USE_UNICAST


#define CLIENT_IP_ADDRESS       IP_ADDRESS(192,2,2,66)
#define SERVER_IP_ADDRESS       IP_ADDRESS(192,2,2,92)
#define SERVER_IP_ADDRESS_2     SERVER_IP_ADDRESS

/* Set up the SNTP network and address index; */
UINT     iface_index =0;
UINT     prefix = 64;   
UINT     address_index;

/* Set up client thread entry point. */
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return 0;
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT     status;
UCHAR    *free_memory_pointer;


    free_memory_pointer = (UCHAR *)first_unused_memory;

    /* Create client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool, 
                                "SNTP Client Packet Pool",
                                NX_SNTP_CLIENT_PACKET_SIZE, 
                                free_memory_pointer, 
                                NX_SNTP_CLIENT_PACKET_POOL_SIZE);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + NX_SNTP_CLIENT_PACKET_POOL_SIZE;

    /* Create Client IP instances */
    status = nx_ip_create(&client_ip, "SNTP IP Instance", 
                                        CLIENT_IP_ADDRESS, 
                                        0xFFFFFF00UL, 
                                        &client_packet_pool, 
                                       _nx_ram_network_driver, 
                                       free_memory_pointer, 2048, 1);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    free_memory_pointer =  free_memory_pointer + 2048;

#ifndef NX_DISABLE_IPV4
    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 2048);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;
    
    /* Enable UDP for client. */
    status =  nx_udp_enable(&client_ip);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

#ifndef NX_DISABLE_IPV4
    status = nx_icmp_enable(&client_ip);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "SNTP Client Thread", 
                                                demo_client_thread_entry, 
                                              (ULONG)(&demo_sntp_client), 
                                                free_memory_pointer, 2048, 
                                                  4, 4, TX_NO_TIME_SLICE, 
                                                        TX_DONT_START);

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Create the event flags. */
    status = tx_event_flags_create(&sntp_flags, "SNTP event flags");

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* set the SNTP network interface to the primary interface. */
    iface_index = 0;

    /* Create the SNTP Client to run in broadcast mode.. */
status =  nx_sntp_client_create(&demo_sntp_client, &client_ip,
                           iface_index, &client_packet_pool,  
                               leap_second_handler, 
                               kiss_of_death_handler, 
                               NULL /* no random_number_generator callback */);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        /* Bail out!*/
        return;
    }

    tx_thread_resume(&demo_client_thread);

    return;
}

/* Define size of buffer to display client's local time. */
#define BUFSIZE 50

/* Define the client thread.  */
void    demo_client_thread_entry(ULONG info)
{

UINT   status;
UINT   spin;
UINT   server_status;
ULONG  base_seconds;
ULONG  base_fraction;
ULONG  seconds, milliseconds, microseconds, fraction;
UINT   wait = 0;
UINT   error_counter = 0;
ULONG  events = 0;
#ifdef USE_IPV6
NXD_ADDRESS sntp_server_address;
NXD_ADDRESS client_ip_address;
#endif

    NX_PARAMETER_NOT_USED(info);

    /* Give other threads (IP instance) initialize first. */
    tx_thread_sleep(NX_IP_PERIODIC_RATE); 

#ifdef USE_IPV6
    /* Set up IPv6 services. */
    status = nxd_ipv6_enable(&client_ip);

    status += nxd_icmp_enable(&client_ip);

    if (status  != NX_SUCCESS)
        return;

    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Set the IPv6 server address. */
    sntp_server_address.nxd_ip_address.v6[0] = 0x20010db8;  
    sntp_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    sntp_server_address.nxd_ip_address.v6[2] = 0x0;
    sntp_server_address.nxd_ip_address.v6[3] = 0x00000106;
    sntp_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address. */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, NULL);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

     /* Set the host global IP address. We are assuming a 64 
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, 
                                        &client_ip_address, 
                                    prefix, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

    /* Wait while NetX Duo validates the global and link local addresses. */
    tx_thread_sleep(5 * NX_IP_PERIODIC_RATE);

#endif

    /* Setup time update callback function. */
    nx_sntp_client_set_time_update_notify(&demo_sntp_client, 
                                        time_update_callback);

    /* Set up client time updates depending on mode. */
#ifdef USE_UNICAST

    /* Initialize the Client for unicast mode to 
       poll the SNTP server once an hour. */
#ifdef USE_IPV6
/* Use the duo service to set up the Client and set the IPv6 SNTP server.
   Note: this can take either an IPv4 or IPv6 address. */
    status = nxd_sntp_client_initialize_unicast(&demo_sntp_client, 
                                            &sntp_server_address);
#else
    /* Use the IPv4 service to set up the Client and set the IPv4 SNTP server. */
    status = nx_sntp_client_initialize_unicast(&demo_sntp_client, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */


#else   /* Broadcast mode */

/* Initialize the Client for broadcast mode, no roundtrip calculation
   required and a broadcast SNTP service. */
#ifdef USE_IPV6
    /* Use the duo service to initialize the Client 
       and set IPv6 SNTP all hosts multicast address. 
       (Note: This can take either an IPv4 or IPv6 address.)*/
    status = nxd_sntp_client_initialize_broadcast(&demo_sntp_client, 
                                                &sntp_server_address, 
                                                            NX_NULL);
#else

    /* Use the IPv4 service to initialize the Client and set 
       IPv4 SNTP broadcast address. */
    status = nx_sntp_client_initialize_broadcast(&demo_sntp_client,  
                                                NX_NULL, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */
#endif  /* USE_UNICAST */

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the base time which is approximately the number of seconds since
       the turn of the last century. If this is not available in SNTP format,
       the nx_sntp_client_utility_add_msecs_to_ntp_time service can convert
       milliseconds to fraction.  For how to compute NTP seconds from real
   time, read the NetX SNTP User Guide. Otherwise set the base time to 
   zero and set NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP to NX_TRUE for
       the SNTP CLient to accept the first time update without applying a
       minimum or maximum adjustment parameters
      (NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT and
       NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT). */

    base_seconds =  0xd2c96b90;  /* Jan 24, 2012 UTC */
    base_fraction = 0xa132db1e;

    /* Apply to the SNTP Client local time.  */
status = nx_sntp_client_set_local_time(&demo_sntp_client, base_seconds,
                                base_fraction);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Run whichever service the client is configured for. */
#ifdef USE_UNICAST
    status = nx_sntp_client_run_unicast(&demo_sntp_client);
#else
    status = nx_sntp_client_run_broadcast(&demo_sntp_client);
#endif  /* USE_UNICAST */

    if (status != NX_SUCCESS)
    {
        return;
    }

    spin = NX_TRUE;

    /* Now check periodically for time changes. */
    while(spin)
    {
        /* Wait for a server update event. */
        tx_event_flags_get(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, 
                                          TX_OR_CLEAR, &events, 
                                 DEMO_PERIODIC_CHECK_INTERVAL);

        if (events == DEMO_SNTP_UPDATE_EVENT)
        {

            /* Check for valid SNTP server status. */
            status = nx_sntp_client_receiving_updates(&demo_sntp_client,
                                               &server_status);

            if ((status != NX_SUCCESS) || (server_status == NX_FALSE))
            {

                /* We do not have a valid update. Skip processing any time
                   data. If this happens repeatedly, consider stopping the
                   SNTP Client thread, picking another SNTP server and
                   resuming the SNTP Client thread task (more details about
                   that in the comments at the end of this function).
                 
                   If SNTP Client configurable parameters are too restrictive,
                   such as Max Adjustment, that may also cause valid server
                   updates to be rejected. Configurable parameters, however,
                   cannot be changed at run time.
                 */
                 
                continue;
            }

            /* We have a valid update.  Get the SNTP Client time.  */
            status = nx_sntp_client_get_local_time_extended(&demo_sntp_client, 
                                                    &seconds, &fraction,  
                                                    NX_NULL, 0); 

            /* Convert fraction to microseconds. */
            nx_sntp_client_utility_fraction_to_usecs(fraction, &microseconds);

            milliseconds = ((microseconds + 500) / 1000);

            if (status != NX_SUCCESS)
            {
                printf("Internal error with getting local time 0x%x\n", 
                       status);
                error_counter++;
            }
            else
            {
                printf("\nSNTP updated\n");
                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }

            /* Clear all events in our event flag. */
            events = 0;
        }
        else
        {

            /* No SNTP update event.             
               In the meantime, if we have an RTC we might want to check
               its notion of time. In this demo, we simulate the passage of 
               time on our 'RTC' really just the CPU counter, assuming that 
               seconds and milliseconds have previously been set to a base 
              (starting) time (as was the SNTP Client before running it) 
             */

            seconds += 1;
            milliseconds += 1;

            /* Update our timer. */
            wait += DEMO_PERIODIC_CHECK_INTERVAL;

            /* Check if it is time to display the local 'RTC' time. */
            if (wait >= CHECK_SNTP_UPDATES_TIMEOUT)
            {
                /* It is. Reset the timeout and print local time. */
                wait = 0;

                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }           
        }
    }

/* We can stop the SNTP service if for example we think the SNTP server 
   has stopped sending updates.
     
       To restart the SNTP Client, simply call the
       nx_sntp_client_initialize_unicast or
       nx_sntp_client_initialize_broadcast using another SNTP server IP
       address as input, and resume the SNTP Client by calling
       nx_sntp_client_run_unicast or
       nx_sntp_client_run_braodcast. */
    status = nx_sntp_client_stop(&demo_sntp_client);

    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* When done with the SNTP Client, we delete it */
    status = nx_sntp_client_delete(&demo_sntp_client);

    return;
}


/* This application defined handler for handling an 
   impending leap second is not required by 
   the SNTP Client. The default handler below only logs the
   event for every time stamp received with the 
   leap indicator set.  */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator)
{
    NX_PARAMETER_NOT_USED(client_ptr);
    NX_PARAMETER_NOT_USED(leap_indicator);

    /* Handle the leap second handler... */

    return NX_SUCCESS;
}

/* This application defined handler for handling 
   a Kiss of Death packet is not required by the SNTP Client. 
   A KOD handler should determine if the Client task should continue vs. 
   abort sending/receiving time data from its current time server, 
   and if aborting if it should remove
   the server from its active server list. 

   Note that the KOD list of codes is subject to change. The list
   below is current at the time of this software release. */

UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, UINT KOD_code)
{

UINT    remove_server_from_list = NX_FALSE;
UINT    status = NX_SUCCESS;

    NX_PARAMETER_NOT_USED(client_ptr);

    /* Handle kiss of death by code group. */
    switch (KOD_code)
    {

        case NX_SNTP_KOD_RATE:
        case NX_SNTP_KOD_NOT_INIT:
        case NX_SNTP_KOD_STEP:

            /* Find another server while this one 
               is temporarily out of service.  */
            status =  NX_SNTP_KOD_SERVER_NOT_AVAILABLE;

        break;

        case NX_SNTP_KOD_AUTH_FAIL:
        case NX_SNTP_KOD_NO_KEY:
        case NX_SNTP_KOD_CRYP_FAIL:

            /* These indicate the server will not 
               service client with time updates
               without successful authentication. */


            remove_server_from_list =  NX_TRUE;

        break;


        default:

            /* All other codes. Remove server 
               before resuming time updates. */

            remove_server_from_list =  NX_TRUE;
        break;
    }

    /* Removing the server from the active server list? */
    if (remove_server_from_list)
    {

        /* Let the caller know it has to bail on 
           this server before resuming service. */
        status = NX_SNTP_KOD_REMOVE_SERVER;
    }

    return status;
}


/* This application defined handler for notifying SNTP time update event.  */

VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time)
{
    tx_event_flags_set(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, TX_OR);
}

```

<span data-ttu-id="3d798-152">Figur 1 exempel på användning av SNTP-klienten med NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3d798-152">Figure 1 Example of using SNTP Client with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="3d798-153">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="3d798-153">Configuration Options</span></span>

<span data-ttu-id="3d798-154">Det finns flera konfigurations alternativ för att definiera NetX Duo SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3d798-154">There are several configuration options for defining the NetX Duo SNTP Client.</span></span> <span data-ttu-id="3d798-155">I följande lista beskrivs var och en i detalj:</span><span class="sxs-lookup"><span data-stu-id="3d798-155">The following list describes each in detail:</span></span>  
  

<span data-ttu-id="3d798-156">**NX_SNTP_CLIENT_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="3d798-156">**NX_SNTP_CLIENT_THREAD_STACK_SIZE**</span></span>  
<span data-ttu-id="3d798-157">Det här alternativet anger storleken på klient tråds Tacken.</span><span class="sxs-lookup"><span data-stu-id="3d798-157">This option sets the size of the Client thread stack.</span></span> <span data-ttu-id="3d798-158">Standard storleken på NetX Duo SNTP är 2048.</span><span class="sxs-lookup"><span data-stu-id="3d798-158">The default NetX Duo SNTP Client size is 2048.</span></span>

<span data-ttu-id="3d798-159">**NX_SNTP_CLIENT_THREAD_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="3d798-159">**NX_SNTP_CLIENT_THREAD_TIME_SLICE**</span></span>  
<span data-ttu-id="3d798-160">Med det här alternativet anges tids segmentet för Schemaläggaren för körning av klient tråd.</span><span class="sxs-lookup"><span data-stu-id="3d798-160">This option sets the time slice of the scheduler allows for Client thread execution.</span></span> <span data-ttu-id="3d798-161">Standard storleken för NetX Duo SNTP är TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="3d798-161">The default NetX Duo SNTP Client size is TX_NO_TIME_SLICE.</span></span>

<span data-ttu-id="3d798-162">**NX_SNTP_CLIENT_ THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="3d798-162">**NX_SNTP_CLIENT_ THREAD_PRIORITY**</span></span>  
<span data-ttu-id="3d798-163">Med det här alternativet anges klient Trådens prioritet.</span><span class="sxs-lookup"><span data-stu-id="3d798-163">This option sets the Client thread priority.</span></span> <span data-ttu-id="3d798-164">Standardvärdet för NetX Duo SNTP-klienten är 2.</span><span class="sxs-lookup"><span data-stu-id="3d798-164">The NetX Duo SNTP Client default value is 2.</span></span>

<span data-ttu-id="3d798-165">**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="3d798-165">**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**</span></span>  
<span data-ttu-id="3d798-166">Med det här alternativet anges den prioritets nivå som klient tråden tillåter avstängningen.</span><span class="sxs-lookup"><span data-stu-id="3d798-166">This option sets the sets the level of priority at which the Client thread allows preemption.</span></span> <span data-ttu-id="3d798-167">Standardvärdet för NetX Duo SNTP är inställt på `NX_SNTP_CLIENT_ THREAD_PRIORITY` .</span><span class="sxs-lookup"><span data-stu-id="3d798-167">The default NetX Duo SNTP Client value is set to `NX_SNTP_CLIENT_ THREAD_PRIORITY`.</span></span>

<span data-ttu-id="3d798-168">**NX_SNTP_CLIENT_UDP_SOCKET_NAME**</span><span class="sxs-lookup"><span data-stu-id="3d798-168">**NX_SNTP_CLIENT_UDP_SOCKET_NAME**</span></span>  
<span data-ttu-id="3d798-169">Med det här alternativet anges UDP-socketens namn.</span><span class="sxs-lookup"><span data-stu-id="3d798-169">This option sets the UDP socket name.</span></span> <span data-ttu-id="3d798-170">NetX Duo SNTP-klientens UDP-socket som standard är "SNTP client socket".</span><span class="sxs-lookup"><span data-stu-id="3d798-170">The NetX Duo SNTP Client UDP socket name default is “SNTP Client socket.”</span></span>

<span data-ttu-id="3d798-171">**NX_SNTP_CLIENT_UDP_PORT**</span><span class="sxs-lookup"><span data-stu-id="3d798-171">**NX_SNTP_CLIENT_UDP_PORT**</span></span>  
<span data-ttu-id="3d798-172">Detta anger den port som klient-socketen är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="3d798-172">This sets the port which the Client socket is bound to.</span></span> <span data-ttu-id="3d798-173">Standard klient porten för NetX Duo SNTP är 123.</span><span class="sxs-lookup"><span data-stu-id="3d798-173">The default NetX Duo SNTP Client port is 123.</span></span>

<span data-ttu-id="3d798-174">**NX_SNTP_SERVER_UDP_PORT**</span><span class="sxs-lookup"><span data-stu-id="3d798-174">**NX_SNTP_SERVER_UDP_PORT**</span></span>  
<span data-ttu-id="3d798-175">Detta är porten som klienten skickar SNTP-meddelanden till till SNTP-servern på.</span><span class="sxs-lookup"><span data-stu-id="3d798-175">This is port which the Client sends SNTP messages to the SNTP Server on.</span></span> <span data-ttu-id="3d798-176">Standard porten för NetX SNTP är 123.</span><span class="sxs-lookup"><span data-stu-id="3d798-176">The default NetX SNTP Server port is 123.</span></span>

<span data-ttu-id="3d798-177">**NX_SNTP_CLIENT_TIME_TO_LIVE**</span><span class="sxs-lookup"><span data-stu-id="3d798-177">**NX_SNTP_CLIENT_TIME_TO_LIVE**</span></span>  
<span data-ttu-id="3d798-178">Anger antalet routrar som ett klient paket kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="3d798-178">Specifies the number of routers a Client packet can pass before it is discarded.</span></span> <span data-ttu-id="3d798-179">Standard NetX Duo SNTP-klienten är inställd på 0x80 *.*</span><span class="sxs-lookup"><span data-stu-id="3d798-179">The default NetX Duo SNTP Client is set to 0x80 *.*</span></span>

<span data-ttu-id="3d798-180">**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**</span><span class="sxs-lookup"><span data-stu-id="3d798-180">**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**</span></span>  
<span data-ttu-id="3d798-181">Maximalt antal UDP-paket (datagram) som kan placeras i kö i NetX Duo SNTP-klientens socket.</span><span class="sxs-lookup"><span data-stu-id="3d798-181">Maximum number of UDP packets (datagrams) that can be queued in the NetX Duo SNTP Client socket.</span></span> <span data-ttu-id="3d798-182">Ytterligare paket som tas emot innebär att de äldsta paketen släpps.</span><span class="sxs-lookup"><span data-stu-id="3d798-182">Additional packets received mean the oldest packets are released.</span></span> <span data-ttu-id="3d798-183">Standard-NetX Duo SNTP-klienten är inställd på 5.</span><span class="sxs-lookup"><span data-stu-id="3d798-183">The default NetX Duo SNTP Client is set to 5.</span></span>

<span data-ttu-id="3d798-184">**NX_SNTP_CLIENT_PACKET_TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="3d798-184">**NX_SNTP_CLIENT_PACKET_TIMEOUT**</span></span>  
<span data-ttu-id="3d798-185">Timeout för NetX Duo-paket tilldelning.</span><span class="sxs-lookup"><span data-stu-id="3d798-185">Time out for NetX Duo packet allocation.</span></span> <span data-ttu-id="3d798-186">Standardvärdet för NetX Duo SNTP-klientprogrammet är 1 sekund.</span><span class="sxs-lookup"><span data-stu-id="3d798-186">The default NetX Duo SNTP Client packet timeout is 1 second.</span></span>

<span data-ttu-id="3d798-187">**NX_SNTP_CLIENT_NTP_VERSION**</span><span class="sxs-lookup"><span data-stu-id="3d798-187">**NX_SNTP_CLIENT_NTP_VERSION**</span></span>  
<span data-ttu-id="3d798-188">Den SNTP-version som används av klienten NetX Duo SNTP-klientens API baserade på version 4.</span><span class="sxs-lookup"><span data-stu-id="3d798-188">SNTP version used by the Client The NetX Duo SNTP Client API was based on Version 4.</span></span> <span data-ttu-id="3d798-189">Standardvärdet är 3.</span><span class="sxs-lookup"><span data-stu-id="3d798-189">The default value is 3.</span></span>

<span data-ttu-id="3d798-190">**NX_SNTP_CLIENT_MIN_NTP_VERSION**</span><span class="sxs-lookup"><span data-stu-id="3d798-190">**NX_SNTP_CLIENT_MIN_NTP_VERSION**</span></span>  
<span data-ttu-id="3d798-191">Äldsta SNTP-version som klienten kommer att kunna arbeta med.</span><span class="sxs-lookup"><span data-stu-id="3d798-191">Oldest SNTP version the Client will be able to work with.</span></span> <span data-ttu-id="3d798-192">Standardvärdet för NetX Duo SNTP-klienten är version 3.</span><span class="sxs-lookup"><span data-stu-id="3d798-192">The NetX Duo SNTP Client default is Version 3.</span></span>

<span data-ttu-id="3d798-193">**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**</span><span class="sxs-lookup"><span data-stu-id="3d798-193">**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**</span></span>  
<span data-ttu-id="3d798-194">Den lägsta nivån (högsta numeriska stratum-nivån) SNTP-server stratum som klienten accepterar.</span><span class="sxs-lookup"><span data-stu-id="3d798-194">The lowest level (highest numeric stratum level) SNTP Server stratum the Client will accept.</span></span> <span data-ttu-id="3d798-195">Standardvärdet för NetX Duo SNTP-klienten är 2.</span><span class="sxs-lookup"><span data-stu-id="3d798-195">The NetX Duo SNTP Client default is 2.</span></span>

<span data-ttu-id="3d798-196">**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**</span><span class="sxs-lookup"><span data-stu-id="3d798-196">**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**</span></span>  
<span data-ttu-id="3d798-197">Den minsta tids justeringen i millisekunder som klienten kommer att göra till den lokala klock tiden.</span><span class="sxs-lookup"><span data-stu-id="3d798-197">The minimum time adjustment in milliseconds the Client will make to its local clock time.</span></span> <span data-ttu-id="3d798-198">Tids justeringar under detta kommer att ignoreras.</span><span class="sxs-lookup"><span data-stu-id="3d798-198">Time adjustments below this will be ignored.</span></span> <span data-ttu-id="3d798-199">Standardvärdet för NetX Duo SNTP-klienten är 10.</span><span class="sxs-lookup"><span data-stu-id="3d798-199">The NetX Duo SNTP Client default is 10.</span></span>

<span data-ttu-id="3d798-200">**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**</span><span class="sxs-lookup"><span data-stu-id="3d798-200">**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**</span></span>  
<span data-ttu-id="3d798-201">Den längsta tids justeringen i millisekunder som klienten kommer att göra till den lokala klock tiden.</span><span class="sxs-lookup"><span data-stu-id="3d798-201">The maximum time adjustment in milliseconds the Client will make to its local clock time.</span></span> <span data-ttu-id="3d798-202">Vid tids justeringar över den här mängden är den lokala klock justeringen begränsad till den maximala tids justeringen.</span><span class="sxs-lookup"><span data-stu-id="3d798-202">For time adjustments above this amount, the local clock adjustment is limited to the maximum time adjustment.</span></span> <span data-ttu-id="3d798-203">Standardvärdet för NetX Duo SNTP-klienten är 180000 (3 minuter).</span><span class="sxs-lookup"><span data-stu-id="3d798-203">The NetX Duo SNTP Client default is 180000 (3 minutes).</span></span>

<span data-ttu-id="3d798-204">**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**</span><span class="sxs-lookup"><span data-stu-id="3d798-204">**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**</span></span>  
<span data-ttu-id="3d798-205">Detta gör det möjligt att åsidosätta den maximala tids justeringen när klienten tar emot den första uppdateringen från sin tids Server.</span><span class="sxs-lookup"><span data-stu-id="3d798-205">This enables the maximum time adjustment to be waived when the Client receives the first update from its time server.</span></span> <span data-ttu-id="3d798-206">Därefter tillämpas den maximala tids justeringen.</span><span class="sxs-lookup"><span data-stu-id="3d798-206">Thereafter, the maximum time adjustment is enforced.</span></span> <span data-ttu-id="3d798-207">Avsikten är att hämta klienten i synk med Server klockan så snart som möjligt.</span><span class="sxs-lookup"><span data-stu-id="3d798-207">The intention is to get the Client in synch with the server clock as soon as possible.</span></span> <span data-ttu-id="3d798-208">Standardvärdet för NetX Duo SNTP-klienten är NX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="3d798-208">The NetX Duo SNTP Client default is NX_TRUE.</span></span>

<span data-ttu-id="3d798-209">**NX_SNTP_CLIENT_MAX_TIME_LAPSE**</span><span class="sxs-lookup"><span data-stu-id="3d798-209">**NX_SNTP_CLIENT_MAX_TIME_LAPSE**</span></span>  
<span data-ttu-id="3d798-210">Maximalt tillåten tids period (sekunder) förflutit utan en giltig tids uppdatering mottagen av SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3d798-210">Maximum allowable amount of time (seconds) elapsed without a valid time update received by the SNTP Client.</span></span> <span data-ttu-id="3d798-211">SNTP-klienten fortsätter att fungera men SNTP-serverns status är inställd på NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="3d798-211">The SNTP Client will continue in operation but the SNTP Server status is set to NX_FALSE.</span></span> <span data-ttu-id="3d798-212">Standardvärdet är 7200.</span><span class="sxs-lookup"><span data-stu-id="3d798-212">The default value is 7200.</span></span>


<span data-ttu-id="3d798-213">**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="3d798-213">**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**</span></span>  
<span data-ttu-id="3d798-214">Det intervall (sekunder) som SNTP-klienten timer uppdaterar, sedan den senaste giltiga uppdateringen togs emot, och unicast-klienten uppdaterar avsöknings intervallet som återstår innan nästa uppdatering av SNTP-begäran skickades.</span><span class="sxs-lookup"><span data-stu-id="3d798-214">The interval (seconds) at which the SNTP Client timer updates the SNTP Client time remaining since the last valid update received, and the unicast Client updates the poll interval time remaining before sending the next SNTP update request.</span></span> <span data-ttu-id="3d798-215">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="3d798-215">The default value is 1.</span></span>

<span data-ttu-id="3d798-216">**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="3d798-216">**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**</span></span>  
<span data-ttu-id="3d798-217">Det första avsöknings intervallet (sekunder) som klienten skickar en unicast-begäran till sin SNTP-server.</span><span class="sxs-lookup"><span data-stu-id="3d798-217">The starting poll interval (seconds) on which the Client sends a unicast request to its SNTP server.</span></span> <span data-ttu-id="3d798-218">Standardvärdet för NetX Duo SNTP-klienten är 3600.</span><span class="sxs-lookup"><span data-stu-id="3d798-218">The NetX Duo SNTP Client default is 3600.</span></span>

<span data-ttu-id="3d798-219">**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**</span><span class="sxs-lookup"><span data-stu-id="3d798-219">**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**</span></span>  
<span data-ttu-id="3d798-220">Den faktor som det aktuella klient-unicast-avsöknings intervallet ökar med.</span><span class="sxs-lookup"><span data-stu-id="3d798-220">The factor by which the current Client unicast poll interval is increased.</span></span> <span data-ttu-id="3d798-221">När klienten inte kan ta emot en uppdatering av Server tiden eller tar emot indikationer från servern som den är tillfälligt otillgänglig (t. ex. ännu inte synkroniserad) för tids uppdaterings tjänsten, ökar det aktuella avsöknings intervallet med denna hastighet upp till men inte mer NX_SNTP_CLIENT_MAX_TIME_LAPSE.</span><span class="sxs-lookup"><span data-stu-id="3d798-221">When the Client fails to receive a server time update, or receiving indications from the server that it is temporarily unavailable (e.g. not synchronized yet) for time update service, it will increase the current poll interval by this rate up to but not exceeding NX_SNTP_CLIENT_MAX_TIME_LAPSE.</span></span> <span data-ttu-id="3d798-222">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="3d798-222">The default is 2.</span></span>

<span data-ttu-id="3d798-223">**NX_SNTP_CLIENT_RTT_REQUIRED**</span><span class="sxs-lookup"><span data-stu-id="3d798-223">**NX_SNTP_CLIENT_RTT_REQUIRED**</span></span>  
<span data-ttu-id="3d798-224">Det här alternativet om aktive rad kräver att SNTP-klienten beräknar en fördröjning i SNTP-meddelanden vid tillämpning av Server uppdateringar på den lokala klockan.</span><span class="sxs-lookup"><span data-stu-id="3d798-224">This option if enabled requires that the SNTP Client calculate round trip time of SNTP messages when applying Server updates to the local clock.</span></span> <span data-ttu-id="3d798-225">Standardvärdet är NX_FALSE (inaktive rad).</span><span class="sxs-lookup"><span data-stu-id="3d798-225">The default value is NX_FALSE (disabled).</span></span>

<span data-ttu-id="3d798-226">**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**</span><span class="sxs-lookup"><span data-stu-id="3d798-226">**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**</span></span>  
<span data-ttu-id="3d798-227">Den maximala spridningen av Server klockor (mikrosekunder), vilket är ett mått på precisionen för Server klock slag, klienten accepterar.</span><span class="sxs-lookup"><span data-stu-id="3d798-227">The maximum server clock dispersion (microseconds), which is a measure of server clock precision, the Client will accept.</span></span> <span data-ttu-id="3d798-228">Om du vill inaktivera det här kravet ställer du in den maximala rot spridningen på 0x0.</span><span class="sxs-lookup"><span data-stu-id="3d798-228">To disable this requirement, set the maximum root dispersion to 0x0.</span></span> <span data-ttu-id="3d798-229">Standardvärdet för NetX Duo SNTP-klienten är inställt på 50000.</span><span class="sxs-lookup"><span data-stu-id="3d798-229">The NetX Duo SNTP Client default is set to 50000.</span></span>

<span data-ttu-id="3d798-230">**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**</span><span class="sxs-lookup"><span data-stu-id="3d798-230">**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**</span></span>  
<span data-ttu-id="3d798-231">Gränsen för antalet ogiltiga uppdateringar i följd som tagits emot från klient servern i broadcast-eller unicast-läge.</span><span class="sxs-lookup"><span data-stu-id="3d798-231">The limit on the number of consecutive invalid updates received from the Client server in either broadcast or unicast mode.</span></span> <span data-ttu-id="3d798-232">När den här gränsen uppnås anger klienten aktuell status för SNTP-servern till ogiltig (NX_FALSE) även om den fortsätter att försöka ta emot uppdateringar från servern.</span><span class="sxs-lookup"><span data-stu-id="3d798-232">When this limit is reached, the Client sets the current SNTP Server status to invalid (NX_FALSE) although it will continue to try to receive updates from the Server.</span></span> <span data-ttu-id="3d798-233">Standardvärdet för NetX Duo SNTP-klienten är 3.</span><span class="sxs-lookup"><span data-stu-id="3d798-233">The NetX Duo SNTP Client default is 3.</span></span>

<span data-ttu-id="3d798-234">**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**</span><span class="sxs-lookup"><span data-stu-id="3d798-234">**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**</span></span>  
<span data-ttu-id="3d798-235">Detta fastställer om SNTP-klienten i unicast-läge ska skicka sin första SNTP-begäran med den aktuella SNTP-servern efter ett slumpmässigt vänte intervall.</span><span class="sxs-lookup"><span data-stu-id="3d798-235">This determines if the SNTP Client in unicast mode should send its first SNTP request with the current SNTP server after a random wait interval.</span></span> <span data-ttu-id="3d798-236">Den används i fall där betydande antal SNTP-klienter startas samtidigt för att begränsa trafik överbelastningen på SNTP-servern.</span><span class="sxs-lookup"><span data-stu-id="3d798-236">It is used in cases where significant numbers of SNTP Clients are starting up simultaneously to limit traffic congestion on the SNTP Server.</span></span> <span data-ttu-id="3d798-237">Standardvärdet är NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="3d798-237">The default value is NX_FALSE.</span></span>

<span data-ttu-id="3d798-238">**NX_SNTP_CLIENT_SLEEP_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="3d798-238">**NX_SNTP_CLIENT_SLEEP_INTERVAL**</span></span>  
<span data-ttu-id="3d798-239">Det tidsintervall under vilket SNTP-klientens aktivitet är i vilo läge.</span><span class="sxs-lookup"><span data-stu-id="3d798-239">The time interval during which the SNTP Client task sleeps.</span></span> <span data-ttu-id="3d798-240">Detta gör att API-anropen kan köras av SNTP-klienten.</span><span class="sxs-lookup"><span data-stu-id="3d798-240">This allows the application API calls to be executed by the SNTP Client.</span></span> <span data-ttu-id="3d798-241">Standardvärdet är 1 timer-Ticket.</span><span class="sxs-lookup"><span data-stu-id="3d798-241">The default value is 1 timer tick.</span></span>

<span data-ttu-id="3d798-242">**NX_SNTP_CURRENT_YEAR**</span><span class="sxs-lookup"><span data-stu-id="3d798-242">**NX_SNTP_CURRENT_YEAR**</span></span>  
<span data-ttu-id="3d798-243">Om du vill visa datum i formatet år/månad/datum ställer du in det här värdet på lika med eller mindre än det aktuella året (behöver inte vara samma år som den NTP-tid som utvärderas).</span><span class="sxs-lookup"><span data-stu-id="3d798-243">To display date in year/month/date format, set this value to equal or less than current year (need not be same year as in NTP time being evaluated).</span></span> <span data-ttu-id="3d798-244">Standardvärdet är 2015.</span><span class="sxs-lookup"><span data-stu-id="3d798-244">The default value is 2015.</span></span>

<span data-ttu-id="3d798-245">**NTP_SECONDS_AT_01011999**</span><span class="sxs-lookup"><span data-stu-id="3d798-245">**NTP_SECONDS_AT_01011999**</span></span>  
<span data-ttu-id="3d798-246">Detta är antalet sekunder till den första NTP-epoken på huvud-NTP-klockan.</span><span class="sxs-lookup"><span data-stu-id="3d798-246">This is the number of seconds into the first NTP Epoch on the master NTP clock.</span></span> <span data-ttu-id="3d798-247">Den definieras som 0xBA368E80.</span><span class="sxs-lookup"><span data-stu-id="3d798-247">It is defined as 0xBA368E80.</span></span> <span data-ttu-id="3d798-248">Om du vill inaktivera visning av NTP-sekunder i datum och tid anger du noll.</span><span class="sxs-lookup"><span data-stu-id="3d798-248">To disable display of NTP seconds into date and time, set to zero.</span></span>
