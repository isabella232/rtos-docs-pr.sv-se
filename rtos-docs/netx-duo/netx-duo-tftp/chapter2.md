---
title: Kapitel 2 – Installation och användning av Azure RTOS NetX Duo TFTP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo TFTP-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ae4e82a0f878af06bd178035cb9429cfe2a14d0bc4bbf848db7d321463586a20
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801265"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a>Kapitel 2 – Installation och användning av Azure RTOS NetX Duo TFTP

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av Azure RTOS NetX Duo TFTP-komponenten.

## <a name="product-distribution"></a>Produktdistribution

Azure RTOS NetX Duo kan hämtas från vår offentliga källkodsdatabas på https://github.com/azure-rtos/netxduo/ . Paketet innehåller följande filer:


- **nxd_tftp_client.h** Huvudfil för NetX Duo TFTP-klient

- **nxd_tftp_client.c** C-källfil för NetX Duo TFTP-klient

- **nxd_tftp_server.h** Huvudfil för NetX Duo TFTP-server

- **nxd_tftp_server.c** C-källfil för NetX Duo TFTP Server

- **filex_stub.h** Stub-fil om FileX inte finns

- **nxd_tftp.pdf** PDF-beskrivning av NetX Duo TFTP

- **demo_netxduo_tftp.c** Demonstration av NetX Duo TFTP

## <a name="tftp-installation"></a>TFTP-installation

Om du vill använda NetX Duo TFTP kan hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\arm7\green*" kan filerna *nxd_tftp_client.h*, *nxd_tftp_client.c*, *nxd_tftp_server.h* och *nxd_tftp_server.c* kopieras till den här katalogen.

## <a name="using-tftp"></a>Använda TFTP

Om du vill köra ett TFTP-program måste programkoden innehålla *nxd_tftp_client.h* och/eller nxd_tftp_server.h efter att den innehåller *tx_api.h, fx_api.h* och *nx_api.h*, för att kunna använda ThreadX, FileX respektive NetX Duo. Programprojektet måste även innehålla *nxd_tftp_client.c* *och/eller nxd_tftp_server.c* i byggprocessen. Dessa filer måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX Duo TFTP. När *huvudfilerna ingår* kan programkoden sedan använda TFTP-tjänster.

> [!NOTE]
> Eftersom TFTP använder NetX Duo UDP-tjänster måste UDP aktiveras med *nx_udp_enable* innan TFTP används.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur enkelt det är att använda NetX Duo TFTP beskrivs i bild 1.1 som visas nedan. I det här exemplet inkluderar TFTP *filen nxd_tftp_client.h* *och nxd_tftp_server.h* på rad 19 och 20. Därefter skapas TFTP-servern i "*tx_application_define*" på rad 179. 

> [!NOTE]
> TFTP-serverkontrollblocket "*server*" definierades som en global variabel på rad 45 tidigare. Den här demonstrationen väljer att använda IPv4 för TFTP-kommunikation på rad 14. När TFTP-servern har skapats startas den på rad 304. På rad 411 skapas TFTP-klienten. Slutligen skriver klienten filen på rad 450 och läser tillbaka filen på rad 485.

TFTP-servertrådaktiviteten stoppas och TFTP-servern tas bort på rad 324. Programmet bör anropa fx_media_close (rad 331) för att stänga alla filer och uppdatera fil- och katalogdata till USB-mediet.

> [!NOTE]
> I det här exemplet används FileX för TFTP-serverhanteringen för att ta emot och ladda ned TFTP-klientfilbegäranden. Men om NX_TFTP_NO_FILEX definieras kan programmet innehålla file_stub.h i stället för fx_api.h.
>
> Observera också att befintliga NetX TFTP-klient- och serverprogram fungerar med NetX Duo TFTP. Programutvecklaren uppmanas dock att porta sina NetX TFTP-program till NetX Duo. Motsvarande NetX TFTP-tjänster är:

- *nxd_tftp_server_start*

- *nxd_tftp_server_stop*

- *nxd_tftp_client_file_read*

- *nxd_tftp_client_file_write*

- *nxd_tftp_client_file_open*

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

Bild 1.1 Exempel på TFTP-användning med NetX Duo

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa NetX Duo TFTP. I följande lista beskrivs var och en i detalj. Om inget annat anges finns dessa alternativ i *nxd_tftp_client.h* och *nxd_tftp_server.h*.


- **NX_DISABLE_ERROR_CHECKING** Det här alternativet tar bort den grundläggande TFTP-felkontrollen. Det används vanligtvis när programmet har felsökts.

- **NX_TFTP_SERVER_PRIORITY** Prioriteten för TFTP-servertråden. Som standard definieras det här värdet som 16 för att ange prioritet 16.

- **NX_TFTP_SERVER_TIME_SLICE** Tidssegmentet för TFTP-servern att köras innan den ger andra trådar med samma prioritet. Standardvärdet är 2.

- **NX_TFTP_MAX_CLIENTS** Det maximala antalet klienter som servern kan hantera samtidigt. Som standard är det här värdet 10 för att stödja 10 klienter samtidigt.

- **NX_TFTP_ERROR_STRING_MAX** Det maximala antalet tecken i felsträngen. Som standard är det här värdet 64.

- **NX_TFTP_NO_FILEX** Det här alternativet har definierats och tillhandahåller en stub för FileX-beroenden. TFTP-klienten fungerar utan ändringar om det här alternativet har definierats. TFTP-servern måste antingen ändras eller så måste användaren skapa ett fåtal FileX-tjänster för att fungera korrekt.

- **NX_TFTP_TYPE_OF_SERVICE** Typ av tjänst som krävs för TFTP UDP-begäranden. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera normal IP-pakettjänst.

- **NX_TFTP_FRAGMENT_OPTION** Fragmentaktivera för TFTP UDP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT inaktivera TFTP UDP-fragmentering.

- **NX_TFTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan skicka innan det tas bort. Standardvärdet är inställt på 0x80.

- **NX_TFTP_SOURCE_PORT** Med det här alternativet kan ett TFTP-klientprogram ange TFTP-klientens UDP-socketport. Standardvärdet är NX_ANY_PORT.

- ***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** Aktiverar TFTP-serverns timer för att kontrollera varje TFTP-klientsession med för den senaste aktiviteten (antingen ett ACK- eller datapaket). När tidsgränsen för sessionen upphör att gälla efter det maximala antalet gånger antas anslutningen ha gått förlorad. Servern rensar klientbegäran, stänger alla öppna filer och gör anslutningsbegäran tillgänglig för nästa klient. Standardinställningen är inaktiverad.

- **NX_TFTP_SERVER_TIMEOUT_PERIOD** Anger intervallet när TFTP-serverns timerinmatningsfunktion kontrollerar klientanslutningar för att ta emot paket. Standardvärdet är 20 (timer tick).

- **NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** Det här är tidsgränsen för att ta emot ett giltigt ACK- eller datapaket från klienten. Standardvärdet är 200 (timer *tick).*

- **NX_TFTP_SERVER_MAX_RETRIES** Anger det maximala antalet gånger som tidsgränsen för återöverföring av klientsessionen förnyas. Därefter stängs sessionen av servern.

- **NX_TFTP_MAX_CLIENT_RETRANSMITS** Anger det maximala antalet gånger som servern tar emot ett duplicerat ACK- eller datapaket från klienten (som det släpper) utan att skicka ett felmeddelande till klienten och stänga sessionen. Har ingen effekt om NX_TFTP_SERVER_RETRANSMIT_ENABLE har definierats.
