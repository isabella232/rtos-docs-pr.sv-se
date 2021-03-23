---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo Telnet
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo Telnet-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5b24690db6ccbc582387dd9dba5b0471e6f278d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825725"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-telnet"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Duo Telnet

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Duo Telnet-komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider NetX Duo Telnet-paketet finns på <https://github.com/azure-rtos/netxduo> . Paketet innehåller följande filer:

- **nxd_telnet_client. h**: rubrik fil för Telnet-klienten för netx Duo
- **nxd_telnet_client. c**: c-källfil för Telnet-klienten för netx Duo
- **nxd_telnet_server. h**: rubrik fil för Telnet Server för netx Duo
- **nxd_telnet_server. c**: c-källfil för Telnet Server för netx Duo
- **nxd_telnet.pdf**: PDF-Beskrivning av Telnet för netx Duo
- **demo_netxduo_telnet. c**: netx Duo Telnet-demonstration

## <a name="telnet-installation"></a>Telnet-installation

För att kunna använda Telnet för NetX Duo, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat. Om t. ex. NetX Duo installeras i katalogen "*\threadx\arm7\green*" måste *nxd_telnet_client. h*-, *nxd_telnet_client. c*-, *nxd_telnet_server. c-och nxd_telnet_server. h* -filer kopieras till den här katalogen.

## <a name="using-telnet"></a>Använda Telnet

Det är enkelt att använda Telnet för NetX Duo. Program koden måste i princip innehålla *nxd_telnet_server. h* för Telnet Server-program och *nxd_telnet_client. h* för Telnet-klientprogram när den innehåller *tx_api. h* och *Nx_api. h* för att kunna använda ThreadX och netx Duo. När *rubriken* är inkluderad kan program koden sedan göra Telnet-funktions anropen senare i den här hand boken. Programmet måste även innehålla *nxd_telnet_client. c* och *nxd_telnet_server. c* i build-processen. De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Detta är allt som krävs för att använda NetX Duo Telnet.

Om det inte krävs några funktioner för Telnet-klienter, kan filen *nxd_telnet_client. c* utelämnas.

Observera också att om Telnet använder NetX Duo TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* samtalet innan Telnet används.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur du använder NetX Duo Telnet visas i bild 1,1 nedan. I det här exemplet innehåller *telnet filer på* rad 7 och 8. Därefter skapas Telnet-servern i "*tx_application_define*" på rad 146. Observera att Telnet-servern och klient kontroll block definieras som globala variabler på rad 23-24 tidigare.

Innan Telnet-servern eller-klienten kan startas måste de verifiera sin IP-adress med NetX Duo. För IPv4-anslutningar görs detta genom att bara vänta en kort stund att låta NetX-drivrutinen initiera systemet på rad 166. För IPv6-anslutningar kräver detta att aktivera IPv6 och ICMPv6 som det gör i raderna 171-172. Klienten anger dess globala och länkade lokala IPv6-adresser på det primära gränssnittet på raderna 181-186 och väntar på att NetX Duo-verifieringen ska slutföras i bakgrunden. Servern anger också dess globala och lokala lokala adresser på det primära gränssnittet på raderna 192 – 198. Observera att de två tjänsterna, *nxd_ipv6_global_address_set* och *nxd_ipv6_linklocal_address_set* ersätts med *nxd_ipv6_address_set-tjänsten*. De två tidigare tjänsterna är fortfarande tillgängliga för äldre NetX Duo-program men är slutligen föråldrade. Utvecklare uppmanas att använda *nxd_ipv6_address_set* i stället.

Efter lyckad verifiering av IP-adress med NetX Duo, startas Telnet-servern på rad 215 med hjälp av tjänsten *nxd_telnet_server_start* . På rad 226 skapas Telnet-klienten med hjälp av tjänsten *nx_telnet_client_create* . Den ansluter sedan med Telnet-servern på rad 242 för IPv4-program och rad 238 för IPv6-program med hjälp av *Nxd_telnet_client_connect* -och *nx_telnet_client_connect* -tjänsterna. Efter lyckad verifiering och anslutning till servern, gör det några utbyten innan du kopplar från.

```c
/* This is a small demo of TELNET on the high-performance NetX Duo TCP/IP stack.  
       This demo relies on ThreadX and NetX Duo to show a simple TELNET connection,
       send, server echo, and then disconnection from the TELNET server.  */
    
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_telnet_client.h"
#include  "nxd_telnet_server.h"
#define     DEMO_STACK_SIZE         4096    
   
/* Define the ThreadX and NetX object control blocks...  */
TX_THREAD               test_thread;
NX_PACKET_POOL          pool_server;
NX_PACKET_POOL          pool_client;
NX_IP                   ip_server;
NX_IP                   ip_client;
   
/* Define TELNET objects.  */

NX_TELNET_SERVER        my_server;
NX_TELNET_CLIENT        my_client;


#ifdef FEATURE_NX_IPV6

/* Define NetX Duo IP address for the NetX Duo Telnet Server and Client. */

NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;

#endif

#define         SERVER_ADDRESS          IP_ADDRESS(1,2,3,4)
#define         CLIENT_ADDRESS          IP_ADDRESS(1,2,3,5)

/* Define the counters used in the demo application...  */
ULONG                   error_counter;

/* Define timeout in ticks for connecting and sending/receiving data. */

#define                 TELNET_TIMEOUT  200

/* Define function prototypes.  */

void    thread_test_entry(ULONG thread_input);
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define the application's TELNET Server callback routines.  */

void    telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection); 
void    telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection, 
                            NX_PACKET *packet_ptr);
void    telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection);

/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT    status;
CHAR    *pointer;
UINT    iface_index, address_index;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;
    
    /* Create the main thread.  */
    tx_thread_create(&test_thread, "test thread", thread_test_entry, 0,  
                     pointer, DEMO_STACK_SIZE, 
                     2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;
    
    /* Initialize the NetX system.  */
    nx_system_initialize();
    
    /* Create packet pool.  */
    nx_packet_pool_create(&pool_server, "Server NetX Packet Pool", 600, pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create an IP instance.  */
    nx_ip_create(&ip_server, "Server NetX IP Instance", SERVER_ADDRESS, 
                 0xFFFFFF00UL, &pool_server, _nx_ram_network_driver,
                 pointer, 4096, 1);
    
    pointer =  pointer + 4096;
    
    /* Create another packet pool. */
    nx_packet_pool_create(&pool_client, "Client NetX Packet Pool", 600, 
                          pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create another IP instance.  */
    nx_ip_create(&ip_client, "Client NetX IP Instance", CLIENT_ADDRESS, 
                 0xFFFFFF00UL, &pool_client, _nx_ram_network_driver, 
                 pointer, 4096, 1);
    
    pointer = pointer + 4096;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_server, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_client, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_server);
    nx_tcp_enable(&ip_client);

#ifdef FEATURE_NX_IPV6

    /* Next set the NetX Duo Telnet Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

#endif

    /* Create the NetX Duo TELNET Server.  */
    status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_server, 
                                      pointer, 2048, telnet_new_connection, telnet_receive_data, 
                                      telnet_connection_end);
    
    /* Check for errors.  */
    if (status)
        error_counter++;
    
    return;
}

/* Define the test thread.  */
void    thread_test_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
    
    /* Allow other threads (e.g. IP thread task) to run first. */
    tx_thread_sleep(100);
    
    #ifdef FEATURE_NX_IPV6
    /* Here's where we make the Telnet Client IPv6 enabled. */
    nxd_ipv6_enable(&ip_client);
    nxd_icmp_enable(&ip_client);     
    
    /* Wait till the IP task thread initializes the system. */
    tx_thread_sleep(100);
        
    /* Set up the Client addresses on the Client IP for the primary interface. */
    if_index = 0;
    
    status = nxd_ipv6_address_set(&ip_ client, iface_index, NX_NULL, 10, 
                                  &address_index);
    status = nxd_ipv6_address_set(&ip_ client, iface_index, & client _ip_address, 
                                   64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */
    tx_thread_sleep(400);
    
    /* Set up the Server addresses on the Client IP. */
    iface_index = 0;
    status = nxd_ipv6_address_set (&ip_server, iface_index, NX_NULL, 10, 
                                   &address_index);
    
    status = nxd_ ipv6_address _set(&ip_server, iface_index, & server _ip_address, 
                                     64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */     
    tx_thread_sleep(400);
    
    #endif
    
    /* Start the TELNET Server.  */
    status =  nx_telnet_server_start(&my_server);
    
    /* Check for errors.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Create a TELENT client instance.  */
    status =  nx_telnet_client_create(&my_client, "My TELNET Client", 
                                      &ip_client, 600);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    #ifdef FEATURE_NX_IPV6
    
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 
                                             TELNET_TIMEOUT);
    
    #else
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nx_telnet_client_connect(&my_client, SERVER_ADDRESS, 23,
                                            TELNET_TIMEOUT);
    #endif
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Allocate a packet.  */
    status =  nx_packet_allocate(&pool_client, &my_packet, NX_TCP_PACKET, 
                                  NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Build a simple 1-byte message.  */
    nx_packet_data_append(my_packet, "a", 1, &pool_client, NX_WAIT_FOREVER);
    
    /* Send the packet to the TELNET Server.  */
    status =  nx_telnet_client_packet_send(&my_client, my_packet, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Pickup the Server header.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the Server's banner
        message sent by the Server callback function below.  Just
        release it for this demo.  */
    nx_packet_release(my_packet);
    
    /* Pickup the Server echo of the character.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the character 'a' that
        we sent earlier.  Just release the packet for now.  */
    nx_packet_release(my_packet);
    
    /* Now disconnect form the TELNET Server.  */
    status =  nx_telnet_client_disconnect(&my_client, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Delete the TELNET Client.  */
    status =  nx_telnet_client_delete(&my_client);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
}

/* This routine is called by the NetX Telnet Server whenever a new Telnet client 
    connection is established.  */
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{

UINT        status;
NX_PACKET   *packet_ptr;

    /* Allocate a packet for client greeting. */
    status =  nx_packet_allocate(&pool_server, &packet_ptr, NX_TCP_PACKET, 
                                  NX_NO_WAIT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Build a banner message and a prompt.  */
    nx_packet_data_append(packet_ptr,"**** Welcome to NetX TELNET Server ****\r\n\r\n\r\n", 45,                            
                         &pool_server, NX_NO_WAIT);

    nx_packet_data_append(packet_ptr, "NETX> ", 6, &pool_server, NX_NO_WAIT);
    
    /* Send the packet to the client.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }
    return;
}

/* This routine is called by the NetX Telnet Server whenever data is present on a 
    Telnet client connection.  */          
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection,
                          NX_PACKET *packet_ptr)
{

UINT    status;
UCHAR   alpha;

    /* This demo echoes the character back; on <cr,lf> sends a new prompt back to 
        the client.  A real system would likely buffer the character(s) received in a 
        buffer associated with the supplied logical connection and process it.  */

    /* Just throw away carriage returns.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\r') && (packet_ptr -> nx_packet_length == 1))
    {
        printf("telnet server received just a CRLF\n");

        nx_packet_release(packet_ptr);
        return;
    }

    /* Setup new line on line feed.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\n') || (packet_ptr -> nx_packet_prepend_ptr[1] == '\n'))
    {
        /* Clean up the packet.  */
        packet_ptr -> nx_packet_length =  0;
        packet_ptr -> nx_packet_prepend_ptr =  packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;
        packet_ptr -> nx_packet_append_ptr =   packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;

        /* Build the next prompt.  */
        nx_packet_data_append(packet_ptr, "\r\nNETX> ", 8, &pool_server, 
                              NX_NO_WAIT);

        /* Send the packet to the client.  */
        status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                               packet_ptr, TELNET_TIMEOUT);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            nx_packet_release(packet_ptr);
        }
        return;
    }

    /* Pickup first character (usually only one from client).  */
    alpha =  packet_ptr -> nx_packet_prepend_ptr[0];

    /* Echo character.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }

    /* Check for a disconnection.  */
    if (alpha == 'q')
    {
        /* Initiate server disconnection.  */
        nx_telnet_server_disconnect(server_ptr, logical_connection);
    }
}


/* This routine is called by the NetX Telnet Server when the client disconnects.  */
void  telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{
    /* Cleanup any application specific connection or buffer information.  */
    return;
}
```

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa Telnet för NetX Duo. Dessa #defines kan anges av programmet innan *nxd_telnet_server. h*. och *nxd_telnet_client. h.*

Följande är en lista över alla alternativ, där var och en beskrivs i detalj:  
  
- **NX_DISABLE_ERROR_CHECKING**: det här alternativet tar bort den grundläggande Telnet-felkontrollen. Den används vanligt vis när programmet har felsökts.
- **NX_TELNET_MAX_CLIENTS**: det maximala antalet Telnet-klienter som stöds av Server tråden. Som standard definieras värdet som 4 för att ange högst 4 klienter i taget.
- **NX_TELNET_SERVER_PRIORITY**: Server Trådens prioritet. Som standard definieras värdet som 16 för att ange prioritet 16.
- **NX_TELNET_TOS**: typ av tjänst som krävs för Telnet TCP-begäranden. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera  
tjänsten för normala IP-paket.
- **NX_TELNET_FRAGMENT_OPTION**: fragment aktivera för Telnet TCP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera Telnet TCP-fragmentering.
- **NX_TELNET_SERVER_WINDOW_SIZE**: serverns socket-fönster storlek. Som standard är det här värdet 2048 byte.
- **NX_TELNET_TIME_TO_LIVE**: anger antalet routrar som det här paketet kan passera innan det tas bort. Standardvärdet är inställt på 0x80.
- **NX_TELNET_SERVER_TIMEOUT**: anger antalet ThreadX-Tick som interna tjänster ska pausas för. Standardvärdet är inställt på 10 sekunder.
- **NX_TELNET_ACTIVITY_TIMEOUT**: anger antalet sekunder som kan förflyta utan aktivitet innan servern kopplar från klient anslutningen. Standardvärdet är inställt på 600 sekunder.
- **NX_TELNET_TIMEOUT_PERIOD**: anger antalet sekunder mellan att söka efter klient aktivitetens timeout. Standardvärdet är inställt på 60 sekunder.
- **NX_TELNET_SERVER_OPTION_DISABLE**: har definierats är alternativ förhandlingen för Telnet inaktive rad. Som standard är det här alternativet inte definierat.
- **NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: om det här alternativet är definierat måste programpoolen för Telnet-servern skapas externt. Detta är endast meningsfullt om NX_TELNET_SERVER_OPTION_DISABLE inte har definierats. Som standard är det här alternativet inte definierat och Telnet Server-tråden skapar en egen modempool.
- **NX_TELNET_SERVER_PACKET_PAYLOAD**: definierar storleken på paketets nytto last som skapats av Telnet-servern för alternativ förhandling. Observera att Telnet-servern bara skapar den här poolen om NX_TELNET_SERVER _OPTION_DISABLE inte har definierats (Telnet-alternativ är aktiverade). Standardvärdet för det här alternativet är 300.
- **NX_TELNET_SERVER_PACKET_POOL_SIZE**: definierar storleken på den Telnet Server-adresspool som används för Telnet-förhandlingar. Observera att Telnet-servern bara skapar den här poolen om NX_TELNET_SERVER _OPTION_DISABLE inte har definierats (Telnet-alternativ är aktiverade). Standardvärdet för det här alternativet är 2048 ( \~ 5-6 paket).
