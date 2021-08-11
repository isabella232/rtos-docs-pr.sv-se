---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo SNTP Client
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Duo SNTP-klienten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2058875c08d64e2c16f67b48323814ec77ec96882eec26aaf2c9454459511db3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799056"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo SNTP Client

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo SNTP Client.

## <a name="product-distribution"></a>Produktdistribution

SNTP för NetX Duo finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_sntp_client.c** SNTP Client C-källfil  
- **nxd_sntp_client.h** SNTP-klienthuvudfil  
- **demo_netxduo_sntp_client.c** Demonstration av SNTP-klientprogram  
- **nxd_sntp_client.pdf** Användarhandbok för NetX Duo SNTP-klient  

## <a name="netx-duo-sntp-client-installation"></a>NetX Duo SNTP-klientinstallation

För att kunna använda SNTP för NetX Duo ska hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\arm7\green*" ska NetX Duo SNTP-klientfilerna *nxd_sntp_client.c* och *nxd_sntp_client.h* (*nx_sntp_client.c* och *nx_sntp_client.h* i NetX) kopieras till den här katalogen.

## <a name="using-netx-duo-sntp-client"></a>Använda NetX Duo SNTP-klient

Det är enkelt att använda NetX Duo SNTP-klienten. I princip måste programkoden innehålla *nxd_sntp_client.h* efter att den innehåller *tx_api.h, fx_api.h* och *nx_api.h* för att kunna använda ThreadX respektive NetX Duo. När *nxd_sntp_client.h* ingår kan programkoden sedan göra de SNTP-funktionsanrop som anges senare i den här guiden. Programmet måste också inkludera *nxd_sntp_client.c* i byggprocessen. Dessa filer måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Detta är allt som krävs för att använda NetX Duo SNTP Client.

> [!NOTE]
> Eftersom NetX Duo SNTP-klienten använder NetX Duo UDP-tjänster  måste UDP aktiveras med nx_udp_enable-anropet innan du använder SNTP-tjänster.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur du använder NetX Duo SNTP visas nedan. Observera att det här **exemplet inte** garanterat fungerar som det är i systemet. Du kan behöva göra justeringar för ditt specifika system och din maskinvara. Du måste till exempel ersätta NetX RAM-drivrutinen med din faktiska drivrutinsfunktion. Det här exemplet är endast avsett i demonstrationssyfte.

I det här exemplet ingår *SNTP-nxd_sntp_client.h.* SNTP-klienten skapas i "*tx_application_define*". Observera att hanterarfunktionerna för dödsfall och skott i sekunden är valfria när du skapar SNTP-klienten.

Den här demonstrationen kan användas med IPv6 eller IPv4. Om du vill köra SNTP-klienten via IPv6 definierar du USE_IPV6. IPv6 måste också vara aktiverat i NetX Duo. SNTP-klientvärden har ställts in för IPv6-adressvalidering och ICMPv6- och IPv6-tjänster i NetX Duo. Mer information om IPv6-stöd i NetX Duo finns i användarhandboken för NetX Duo.

Sedan måste SNTP-klienten initieras för antingen unicast- eller broadcast-läge.

SNTP-klienten skriver inledningsvis tidsuppdateringar för servern till sin egen interna datastruktur. Detta är inte samma som enhetens lokala tid. Enhetens lokala tid kan anges som en baslinjetid i SNTP-klienten innan SNTP-klienttråden startas. Detta är användbart om SNTP-klienten är konfigurerad (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP inställd på NX_FALSE) för att jämföra den första serveruppdateringen med NX_SNTP_CLIENT_MAX_ADJUSTMENT (standardvärdet 180 millisekunder). Annars anger SNTP-klienten den första lokala tiden direkt när den första uppdateringen från servern.

En baslinjetid tillämpas på SNTP-klienten med hjälp *av nx_sntp_client_set_local_time tjänsten.*

SNTP-klienten startas för unicast- respektive broadcast-läge. För ett visst intervall (något mindre än unicast-avsökningsintervallet) uppdaterar programmet SNTP-klientens lokala tid med hjälp av *nx_sntp_client_set_local_time*, från "realtidsklockan" som vi simulerar genom att bara öka sekunderna och millisekunderna för den aktuella tiden. Efter varje intervall söker programmet regelbundet efter uppdateringar från SNTP-servern. Tjänsten *nx_sntp_client_receiving _updates* verifierar att SNTP-klienten för närvarande tar emot giltiga uppdateringar. I så fall hämtas den senaste  uppdateringstiden med hjälp av nx_sntp_client_get_local_time_extended tjänsten.

SNTP-klienten kan stoppas när som helst med *hjälp nx_sntp_client_stop-tjänsten* om den till exempel upptäcker att SNTP-klienten inte längre tar emot giltiga uppdateringar.. Om du vill starta om klienten måste programmet anropa antingen unicast- eller broadcast-initierartjänsten och sedan anropa antingen unicast- eller broadcast run-tjänster. När SNTP-klientens trådaktivitet stoppas kan SNTP-klienten växla SNTP-servrar och -lägen (unicast eller broadcast) om det behövs, t.ex. den tidigare SNTP-servern verkar vara nere.

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

Bild 1 Exempel på användning av SNTP-klient med NetX Duo

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att definiera NetX Duo SNTP-klienten. I följande lista beskrivs var och en i detalj:  
  

**NX_SNTP_CLIENT_THREAD_STACK_SIZE**  
Det här alternativet anger storleken på klienttrådstacken. Standardstorleken för NetX Duo SNTP-klienten är 2 048.

**NX_SNTP_CLIENT_THREAD_TIME_SLICE**  
Det här alternativet anger tidssegmentet för schemaläggaren som tillåter körning av klienttråd. Standardstorleken för NetX Duo SNTP-klienten är TX_NO_TIME_SLICE.

**NX_SNTP_CLIENT_ THREAD_PRIORITY**  
Det här alternativet anger prioritet för klienttråden. NetX Duo SNTP-klientens standardvärde är 2.

**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**  
Det här alternativet anger prioritetsnivån som klienttråden tillåter avinption på. Standardvärdet för NetX Duo SNTP-klienten är inställt på `NX_SNTP_CLIENT_ THREAD_PRIORITY` .

**NX_SNTP_CLIENT_UDP_SOCKET_NAME**  
Det här alternativet anger UDP-socketnamnet. Standardnamnet för NetX Duo SNTP-klientens UDP-socket är "SNTP-klientsocket".

**NX_SNTP_CLIENT_UDP_PORT**  
Detta anger porten som klientsocketen är bunden till. Standardporten för NetX Duo SNTP-klienten är 123.

**NX_SNTP_SERVER_UDP_PORT**  
Det här är den port som klienten skickar SNTP-meddelanden till SNTP-servern på. Standardporten för NetX SNTP-servern är 123.

**NX_SNTP_CLIENT_TIME_TO_LIVE**  
Anger antalet routrar som ett klientpaket kan skicka innan det tas bort. Standardklienten för NetX Duo SNTP är inställd på 0x80 *.*

**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**  
Maximalt antal UDP-paket (datagram) som kan köas i NetX Duo SNTP-klientsocketen. Ytterligare paket som tas emot innebär att de äldsta paketen släpps. Standardklienten för NetX Duo SNTP är inställd på 5.

**NX_SNTP_CLIENT_PACKET_TIMEOUT**  
Time out för Paketallokering för NetX Duo. Standardtidsinställningen för NetX Duo SNTP-klientpaket är 1 sekund.

**NX_SNTP_CLIENT_NTP_VERSION**  
SNTP-versionen som användes av klienten NetX Duo SNTP-klient-API:et baserades på version 4. Standardvärdet är 3.

**NX_SNTP_CLIENT_MIN_NTP_VERSION**  
Den äldsta SNTP-version som klienten kommer att kunna arbeta med. NetX Duo SNTP-klientens standard är Version 3.

**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**  
Den lägsta nivån (högsta numeriska stratumnivå) SNTP Server-stratum som klienten accepterar. NetX Duo SNTP-klientens standardvärde är 2.

**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**  
Den minsta tidsjusteringen i millisekunder som klienten gör till sin lokala klocktid. Tidsjusteringar under detta ignoreras. NetX Duo SNTP-klientens standardvärde är 10.

**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**  
Den maximala tidsjusteringen i millisekunder som klienten gör till sin lokala klocktid. Vid tidsjusteringar över den här mängden är den lokala klockjusteringen begränsad till den maximala tidsjusteringen. NetX Duo SNTP-klientens standardvärde är 180 000 (3 minuter).

**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**  
Detta gör att den maximala tidsjusteringen kan åsidosättas när klienten tar emot den första uppdateringen från sin tidsserver. Därefter tillämpas den maximala tidsjusteringen. Avsikten är att synkronisera klienten med serverklockan så snart som möjligt. Standardinställningen för NetX Duo SNTP-klienten är NX_TRUE.

**NX_SNTP_CLIENT_MAX_TIME_LAPSE**  
Längsta tillåtna tid (sekunder) förflutit utan en giltig tidsuppdatering som tagits emot av SNTP-klienten. SNTP-klienten fortsätter att arbeta, men SNTP-serverns status är inställd på NX_FALSE. Standardvärdet är 7200.


**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**  
Intervallet (sekunder) då SNTP-klienttimern uppdaterar den återstående SNTP-klienttiden sedan den senaste giltiga uppdateringen togs emot, och unicast-klienten uppdaterar avsökningsintervallet som återstår innan nästa SNTP-uppdateringsbegäran skickas. Standardvärdet är 1.

**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**  
Startintervallet för avsökning (sekunder) där klienten skickar en unicast-begäran till sin SNTP-server. NetX Duo SNTP-klientens standardvärde är 3600.

**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**  
Den faktor med vilken det aktuella unicast-avsökningsintervallet för klienten ökar. Om klienten inte kan ta emot en servertidsuppdatering eller får indikeringar från servern om att den är tillfälligt otillgänglig (t.ex. inte synkroniserad ännu) för tidsuppdateringstjänsten, ökar det aktuella avsökningsintervallet med den här frekvensen upp till men inte överstiger NX_SNTP_CLIENT_MAX_TIME_LAPSE. Standardvärdet är 2.

**NX_SNTP_CLIENT_RTT_REQUIRED**  
Om det här alternativet är aktiverat måste SNTP-klienten beräkna tur och retur-tid för SNTP-meddelanden när serveruppdateringar tillämpas på den lokala klockan. Standardvärdet är NX_FALSE (inaktiverat).

**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**  
Maximal spridning av serverklockor (mikrosekunder), vilket är ett mått på precisionen för serverklockan som klienten accepterar. Om du vill inaktivera det här kravet anger du maximal rotspridning till 0x0. Standardvärdet för NetX Duo SNTP-klienten är inställd på 50000.

**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**  
Gränsen för antalet ogiltiga uppdateringar i följd som tas emot från klientservern i broadcast- eller unicast-läge. När den här gränsen nås anger klienten den aktuella SNTP-serverstatusen till ogiltig (NX_FALSE) även om den fortsätter att försöka ta emot uppdateringar från servern. NetX Duo SNTP-klientens standard är 3.

**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**  
Detta avgör om SNTP-klienten i unicast-läge ska skicka sin första SNTP-begäran med den aktuella SNTP-servern efter ett slumpmässigt vänteintervall. Den används i fall där ett stort antal SNTP-klienter startas samtidigt för att begränsa trafikbelastningen på SNTP-servern. Standardvärdet är NX_FALSE.

**NX_SNTP_CLIENT_SLEEP_INTERVAL**  
Det tidsintervall då SNTP-klientaktiviteten försparar sig. Detta gör att programmets API-anrop kan köras av SNTP-klienten. Standardvärdet är 1 timer tick.

**NX_SNTP_CURRENT_YEAR**  
Om du vill visa datum i formatet år/månad/datum anger du det här värdet till lika med eller mindre än det aktuella året (behöver inte vara samma år som i NTP-tid som utvärderas). Standardvärdet är 2015.

**NTP_SECONDS_AT_01011999**  
Det här är antalet sekunder till den första NTP-epoken på NTP-huvudklockan. Den definieras som 0xBA368E80. Om du vill inaktivera visning av NTP-sekunder till datum och tid anger du noll.
