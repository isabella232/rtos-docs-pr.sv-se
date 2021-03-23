---
title: Kapitel 2 – installation och användning av FTP
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo FTP-tjänster.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ac58658af93f59556d99d340ae38570908d63fc1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825977"
---
# <a name="chapter-2---installation-and-use-of-ftp"></a>Kapitel 2 – installation och användning av FTP

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo FTP-tjänster.

## <a name="product-distribution"></a>Produkt distribution

NetX Duo FTP finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller två källfiler och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nxd_ftp_client. h** Rubrik fil för NetX Duo FTP-klient
- **nxd_ftp_client. c** C-källfil för NetX Duo FTP client
- **nxd_ftp_server. h** Rubrik fil för NetX Duo FTP-Server
- **nxd_ftp_server. c** C-källfil för NetX Duo FTP-Server
- **filex_stub. h** Stub-fil om FileX inte finns
- **nxd_ftp.pdf** PDF-Beskrivning av FTP för NetX Duo
- **demo_netxduo_ftp. c** Demonstrations system för FTP

## <a name="netx-duo-ftp-installation"></a>NetX Duo FTP-installation

För att kunna använda NetX Duo FTP API, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat. Om t. ex. NetX Duo installeras i katalogen "*\threadx\arm7\green*" måste *nxd_ftp_client. h* och *nxd_ftp_client. c* kopieras till den här katalogen för FTP-klientprogram och *nxd_ftp_server. h* -och *nxd_ftp_server. c* -filer ska kopieras till den här katalogen för FTP-serverprogram.

## <a name="using-netx-duo-ftp"></a>Använda NetX Duo FTP

Det är enkelt att använda NetX Duo FTP API. Program koden måste i princip innehålla antingen *nxd_ftp_client. h* för FTP-klientprogram eller *nxd_ftp_server* för FTP-serverprogram när den innehåller *tx_api. h, fx_api. h* och *nx_api. h*, för att kunna använda ThreadX, FileX och netx Duo. Build-projektet måste innehålla FTP-källkoden och värd program filen, och naturligtvis ThreadX-och NetX-biblioteksfilerna. Detta är allt som krävs för att använda NetX Duo FTP.

Observera att eftersom FTP använder NetX Duo TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* samtalet innan FTP används.

Observera att NetX Duo-biblioteket kan aktive ras för IPv6 och fortfarande ha stöd för IPv4-nätverk. NetX Duo stöder dock inte IPv6 om den inte är aktive rad. För att inaktivera IPv6-bearbetning i NetX Duo måste **NX_DISABLE_IPV6** definieras i *nx_user. h* -filen och filen måste ingå i netx Duo Library-versionen genom att definiera **NX_INCLUDE_USER_DEFINE_FILE** i *nx_port. h* -filen. Som standard är **NX_DISABLE_IPV6** inte definierat (IPv6 är aktiverat). Detta skiljer sig från *nxd_ipv6_enable* -tjänsten som konfigurerar IPv6-protokoll och-tjänster för IP-aktiviteten och kräver att **NX_DISABLE_IPV6** inte har definierats.

## <a name="small-example-system-of-netx-duo-ftp"></a>Litet exempel system av NetX Duo FTP

Ett exempel på hur enkelt det är att använda NetX Duo FTP beskrivs i bild 1,1 som visas nedan. I det här exemplet skapas både en FTP-server och en FTP-klient. Både FTP inkluderar filerna *nxd_ftp_client. h och nxd_ftp_server. h* tas i rad 10 och 11. Därefter skapas FTP-servern i "*tx_application_define*" på rad 99. Observera att FTP-servern och klient kontroll block definieras som globala variabler på rad 26 tidigare.

Den här demon visar hur du använder de Duo-funktioner som är tillgängliga i NetX Duo FTP samt de äldre IPv4-begränsade FTP-tjänsterna. För att använda IPv6-funktionerna definierar demonstrationen USE_IPV6 på rad 16

På rad 162 skapas FTP-servern med ***nxd_ftp_server_create** _ om värd programmet definierar USE_IPV6 som stöder både IPv4 och IPv6. Om så inte är fallet skapas FTP-servern med _ *_nx_ftp_server_create_** på rad 166 med begränsad IPv4-tjänst. Observera att funktionen Duo använder olika inloggnings-och utloggnings funktions argument än IPv4-tjänsten, som båda definieras längst ned i filen på raderna 534-568.

FTP-servern måste sedan upprätta sin IPv6-adress (global och länk lokal) med NetX Duo, med början på rad 466 i kopplings funktionen för FTP-server. FTP-servern startas sedan på rad 518 och är klar för FTP-begäranden.

FTP-klienten skapas på rad 316 och går igenom samma process som FTP-servern för att få IP-uppgiften IPv6 aktive rad för FTP-klienter, och dess IPv6-adresser verifieras från och med rader 263-313.

Klienten ansluter sedan till FTP-servern med ***nxd_ftp_client_connect** _ på rad 334 om den har definierat USE_IPV6 eller rad 340 om den använder den begränsade IPv4-tjänsten _ *_nx_ftp_client_connect_* *. Under den tid som FTP-klienten trådas skriver den en fil till FTP-servern och läser den igen innan den kopplas från.

```C
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack.  This demo
   relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
   and then back to the server.  */



#include    "tx_api.h"
#include    "fx_api.h"
#include    "nx_api.h"
#include    "nxd_ftp_client.h"
#include    "nxd_ftp_server.h"

#define     DEMO_STACK_SIZE         4096

#ifdef FEATURE_NX_IPV6
#define USE_IPV6
#endif /* FEATURE_NX_IPV6 */


/* Define the ThreadX, NetX, and FileX object control blocks...  */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;


/* Define the NetX FTP object control blocks.  */

NX_FTP_CLIENT           ftp_client;
NX_FTP_SERVER           ftp_server;


/* Define the counters used in the demo application...  */

ULONG                   error_counter = 0;


/* Define the memory area for the FileX RAM disk.  */

UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];


#define FTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)

extern UINT  _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                        VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                        CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                        UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                        UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions.  */
VOID    _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);


void    client_thread_entry(ULONG thread_input);
void    thread_server_entry(ULONG thread_input);


#ifdef USE_IPV6
/* Define NetX Duo IP address for the NetX Duo FTP Server and Client. */
NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;
endif


/* Define server login/logout functions.  These are stubs for functions that would
   validate a client login request.   */

#ifdef USE_IPV6
UINT    server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
#else
UINT    server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
#endif


/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return(0);
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    UCHAR   *pointer;


    /* Setup the working pointer.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize NetX.  */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server.  */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool", 256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors.  */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server.  */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", FTP_SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance.  */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP.  */
    nx_tcp_enable(&server_ip);

#ifdef USE_IPV6

    /* Next set the NetX Duo FTP Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Create the FTP server.  */
    status =  nxd_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login6, server_logout6);
#else
    /* Create the FTP server.  */
    status =  nx_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login, server_logout);
#endif
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread.  */
    status = tx_thread_create(&client_thread, "FTP Client thread ", client_thread_entry, 0,
            pointer, DEMO_STACK_SIZE,
            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE ;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client.  */
    status =  nx_packet_pool_create(&client_pool, "NetX Client Packet Pool", 256, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the FTP client.  */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP.  */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance.  */
    nx_tcp_enable(&client_ip);

    return;

}

/* Define the FTP client thread.  */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;

#ifdef USE_IPV6
UINT        iface_index, address_index;
#endif


    /* Format the RAM disk - the memory for the RAM disk was defined above.  */
    status = _fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry                */
                            ram_disk_memory,                 /* RAM disk memory pointer     */
                            ram_disk_sector_cache,           /* Media buffer pointer        */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size           */
                            "MY_RAM_DISK",                   /* Volume Name                 */
                            1,                               /* Number of FATs              */
                            32,                              /* Directory Entries           */
                            0,                               /* Hidden sectors              */
                            256,                             /* Total sectors               */
                            128,                             /* Sector size                 */
                            1,                               /* Sectors per cluster         */
                            1,                               /* Heads                       */
                            1);                              /* Sectors per track           */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk.  */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
        ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Let the IP threads and driver initialize the system.    */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    status = nxd_icmp_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Set the Client link local and global addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Let NetX Duo validate the addresses. */
    tx_thread_sleep(400);

#endif  /* USE_IPV6 */

    /* Create an FTP client.  */
    status =  nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Created the FTP Client\n");

#ifdef USE_IPV6

    do
    {

        /* Now connect with the NetX Duo FTP (IPv6) server. */
        status =  nxd_ftp_client_connect(&ftp_client, &server_ip_address, "name", "password", 100);
    } while (status != NX_SUCCESS);

#else

    /* Now connect with the NetX FTP (IPv4) server. */
    status =  nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS, "name", "password", 100);

#endif  /* USE_IPV6 */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet.  */
    status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer.  */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt.  */
    status =  nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");


    /* Close the file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");


    /* Now open the same file for reading.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file.  */
    status =  nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
            printf("Reread the FTP client test.txt file\n");
            nx_packet_release(my_packet);
    }

    /* Close this file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server.  */
    status =  nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;


    /* Delete the FTP client.  */
    status =  nx_ftp_client_delete(&ftp_client);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
}


/* Define the helper FTP server thread.  */
void    thread_server_entry(ULONG thread_input)
{

    UINT            status;
#ifdef  USE_IPV6
    UINT            iface_index, address_index;
#endif

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP server IPv6 enabled. */
    status = nxd_ipv6_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    status = nxd_icmp_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);

#endif /* USE_IPV6 */

    /* OK to start the FTP Server.   */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute.    */
    tx_thread_relinquish();

    return;
}


#ifdef USE_IPV6
UINT  server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    NXD_ADDRESS *client_ipduo_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged in6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
                     UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#else
UINT  server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#endif  /* USE_IPV6 */
```

**Figur 1,1 exempel på NetX Duo FTP**

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa NetX FTP och NetX Duo FTP. Standardvärdena visas, men varje definierar kan anges av

program innan den angivna NetX Duo FTP-huvudfilen tas med. Om ingen rubrik fil anges är alternativet tillgängligt i både *nxd_ftp_client. h och nxd_ftp_server. h*. I följande lista beskrivs var och en i detalj:

- **NX_FTP_SERVER_PRIORITY** Prioriteten för FTP-serverns tråd. Som standard definieras värdet som 16 för att ange prioritet 16.
- **NX_FTP_MAX_CLIENTS** Det maximala antalet klienter som servern kan hantera på en och samma tidpunkt. Som standard är det här värdet 4 för att stödja 4 klienter på en gång.
- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD** Den minimala storleken på nytto lasten i byte för Server paketets pool, inklusive TCP-, IP-och nätverks ram-rubriker plus HTTP-data. Standardvärdet är 256 (den maximala längden på filename i FileX) + 12 byte för fil information och NX_PHYSICAL_TRAILER.
- **NX_FTP_SERVER_TIMEOUT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för. Standardvärdet är inställt på 1 sekund (1 * NX_IP_PERIODIC_RATE).
- **NX_FTP_ACTIVITY_TIMEOUT** Anger antalet sekunder som en klient anslutning upprätthålls om det inte finns någon aktivitet. Standardvärdet är inställt på 240.
- **NX_FTP_TIMEOUT_PERIOD** Anger de intervall i sekunder som servern söker efter klient aktivitet. Standardvärdet är inställt på 60.
- **NX_FTP_SERVER_RETRY_SECONDS** Anger den inledande tids gränsen i sekunder innan Server svaret skickas igen. Standardvärdet är 2.
- **NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH** Anger det maximala djupet för överförings paket i kö på Server-socket. Standardvärdet är 20.
- **NX_FTP_SERVER_RETRY_MAX** Anger högsta antal återförsök per paket. Standardvärdet är 10.
- **NX_FTP_SERVER_RETRY_SHIFT** Anger antalet bitar som ska skiftas i inställningen Timeout för återförsök. Standardvärdet är 2, t. ex. varje timeout för återförsök är två gånger så länge det föregående försöket.
- **NX_FTP_NO_FILEX** Definierad är det här alternativet en stub för FileX-beroenden. FTP-klienten fungerar utan några ändringar om det här alternativet har definierats. FTP-servern måste antingen ändras eller så måste användaren skapa en fåtal av FileX-tjänster för att fungera korrekt.
- **NX_FTP_CONTROL_TOS** Typ av tjänst som krävs för förfrågningar om FTP-kontroll. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.
- **NX_FTP_DATA_TOS** Typ av tjänst som krävs för förfrågningar om FTP-data. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.
- **NX_FTP_FRAGMENT_OPTION** Fragment aktivera för FTP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera FTP TCP-fragmentering.
- **NX_FTP_CONTROL_WINDOW_SIZE** Storlek på TCP-kontrollens socket-fönster. Som standard är det här värdet 400 byte.
- **NX_FTP_DATA_WINDOW_SIZE** Fönster storlek för TCP-datasocket. Som standard är det här värdet 2048 byte.
- **NX_FTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan passera innan det tas bort. Standardvärdet är inställt på 0x80.
- **NX_FTP_USERNAME_SIZE** Anger antalet byte som tillåts i en klient som har angett *användar namn*. Standardvärdet är inställt på 20 *.*
- **NX_FTP_PASSWORD_SIZE** Anger antalet byte som tillåts i ett *lösen ord* som anges av klienten. Standardvärdet är inställt på 20.
