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
# <a name="chapter-2---installation-and-use-of-netx-http"></a>Kapitel 2 – installation och användning av NetX HTTP

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX HTTP-komponenten.

## <a name="product-distribution"></a>Produkt distribution

Azure återställnings tider-NetX kan hämtas från vår offentliga käll kods lagrings plats på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .

- **nx_http_client. h** Rubrik fil för HTTP-klient för NetX
- **nx_http_server. h** Rubrik fil för HTTP-server för NetX
- **nx_http_client. c** C-källfil för HTTP-klient för NetX
- **nx_http_server. c** C-källfil för HTTP-server för NetX
- **nx_md5. c** MD5 Digest-algoritmer
- **filex_stub. h** Stub-fil om FileX inte finns
- **nx_http.pdf** Beskrivning av HTTP för NetX
- **demo_netx_http. c** NetX HTTP-demonstration

## <a name="http-installation"></a>HTTP-installation

För att du ska kunna använda HTTP för NetX, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX har installerats. Om t. ex. NetX har installerats i katalogen "*\threadx\arm7\green*", används *nx_http_client. h* och *NX_HTTP_CLIENT. c* för NetX http-klientprogram och *nx_http_server. h* och *nx_http_server. c* för netx http-serverprogram. *nx_md5. c* ska kopieras till den här katalogen. För demonstrationen av "ram-drivrutinen" program NetX HTTP-klient och server filer ska kopieras till samma katalog.

## <a name="using-http"></a>Använda HTTP

Det är enkelt att använda HTTP för NetX. I princip måste program koden innehålla *nx_http_client. h* och/eller *nx_http_server. h* när den innehåller *tx_api. h, fx_api. h* och *nx_api. h*, för att kunna använda ThreadX, FileX och netx. När HTTP-huvudfilerna har inkluderats kan program koden göra HTTP-funktions anropen senare i den här hand boken. Programmet måste också innehålla *nx_http_client. c*, *nx_http_server. c* och *MD5. c* i build-processen. De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer. Detta är allt som krävs för att använda NetX HTTP.

>[!NOTE] 
> Om NX_HTTP_DIGEST_ENABLE inte anges i build-processen behöver inte *MD5. c* -filen läggas till i programmet. Om ingen HTTP-klient krävs, kan filen *nx_http_client. c* utelämnas.

>[!NOTE] 
> Eftersom HTTP använder sig av NetX TCP-tjänster måste TCP aktive ras med det *nx_tcp_enable* samtalet innan http används.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur enkelt det är att använda NetX HTTP beskrivs i bild 1,1 som visas nedan. I det här exemplet tas HTTP-filen *nx_http_client. h och nx_http_server. h* in på rad 8. Därefter skapas HTTP-servern i "*tx_application_define*" på rad 131.

>[!NOTE] 
> HTTP Server Control Block "*Server*" har definierats som en global variabel på rad 25 tidigare.

När den har skapats startas en HTTP-server på rad 136. På rad 149 har HTTP-klienten skapats. Slutligen skriver klienten filen på rad 157 och läser tillbaka filen på rad 195.

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

Figur 1,1 exempel på HTTP-användning med NetX

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa HTTP för NetX. Följande är en lista över alla alternativ, där var och en beskrivs i detalj. Standardvärdena visas, men kan omdefinieras innan du kan inkludera *nx_http_client. h och nx_http_server. h*:

- **NX_DISABLE_ERROR_CHECKING** Definierad tar det här alternativet bort grundläggande HTTP-felkontroll. Den används vanligt vis när programmet har felsökts.
- **NX_HTTP_SERVER_PRIORITY** Prioriteten för HTTP-serverns tråd. Som standard definieras värdet som 16 för att ange prioritet 16.
- **NX_HTTP_NO_FILEX** Definierad är det här alternativet en stub för FileX-beroenden. HTTP-klienten fungerar utan några ändringar om det här alternativet har definierats. HTTP-servern måste antingen ändras eller så måste användaren skapa en fåtal av FileX-tjänsterna för att fungera korrekt.
- **NX_HTTP_TYPE_OF_SERVICE** Typ av tjänst som krävs för HTTP TCP-begäranden. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.
- **NX_HTTP_SERVER_THREAD_TIME_SLICE** Antalet timer-Tick som server tråden får köra innan den tilldelas trådar av samma prioritet. Standardvärdet är 2.
- **NX_HTTP_FRAGMENT_OPTION** Fragment aktivera för HTTP TCP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera HTTP TCP-fragmentering.
- **NX_HTTP_SERVER_WINDOW_SIZE** Serverns socket Window-storlek. Som standard är det här värdet 2048 byte.
- **NX_HTTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan passera innan det tas bort. Standardvärdet är inställt på 0x80.
- **NX_HTTP_SERVER_TIMEOUT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för. Standardvärdet är inställt på 10 sekunder (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_ACCEPT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_server_socket_accept* -anrop. Standardvärdet är inställt på (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_disconnect* -anrop. Standardvärdet är inställt på 10 sekunder (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_RECEIVE** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_receive* -anrop. Standardvärdet är inställt på 10 sekunder (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_SEND** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_send* -anrop. Standardvärdet är inställt på 10 sekunder (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_MAX_HEADER_FIELD** Anger den maximala storleken för fältet HTTP-huvud. Standardvärdet är 256.
- **NX_HTTP_MULTIPART_ENABLE** Om det här alternativet har definierats kan HTTP-servern stödja multipart HTTP-begäranden.
- **NX_HTTP_SERVER_MAX_PENDING** Anger antalet anslutningar som kan köas för HTTP-servern. Standardvärdet är inställt på 5.
- **NX_HTTP_MAX_RESOURCE** Anger antalet byte som tillåts i ett klient *resurs namn* som anges. Standardvärdet är inställt på 40.
- **NX_HTTP_MAX_NAME** Anger antalet byte som tillåts i en klient som har angett *användar namn*. Standardvärdet är inställt på 20.
- **NX_HTTP_MAX_PASSWORD** Anger antalet byte som tillåts i ett *lösen ord* som anges av klienten. Standardvärdet är inställt på 20.
- **NX_HTTP_SERVER_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när servern skapas. Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket. Standardvärdet är inställt på 600.
- **NX_HTTP_CLIENT_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när klienten skapades. Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket. Standardvärdet är inställt på 300.
- **NX_HTTP_SERVER_RETRY_SECONDS** *Ange tids gränsen för återöverföring av Server-socket i sekunder.* Standardvärdet är inställt på 2.
- **NX_HTTP_SERVER_RETRY_MAX** Detta anger det maximala antalet återöverföringar på Server-socketen. Standardvärdet är inställt på 10.
- **NX_HTTP_SERVER_RETRY_SHIFT** Det här värdet används för att ange nästa timeout för återöverföring. Den aktuella tids gränsen multipliceras med antalet återöverföringar, vilket innebär att värdet för timeout-värdet för socketen flyttas. Standardvärdet är inställt på 1 för dubblerad tids gräns.
- **NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** Detta anger det maximala antalet paket som kan köas på återställnings kön för Server-socket. Om antalet paket som har placerats i kö når det här antalet kan inga fler paket skickas förrän ett eller flera köade paket släpps. Standardvärdet är inställt på 20.