---
title: Kapitel 2 – Installation och användning av NetX Duo SMTP-klient
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Duo SMTP-klientkomponenten.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ba4d50048adba4ac992f6bbe90d236445546a5929ace74899833c686a90dadd9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797848"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>Kapitel 2 – Installation och användning av NetX Duo SMTP-klient

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Duo SMTP-klientkomponenten.

## <a name="netx-duo-smtp-client-installation"></a>Installation av NetX Duo SMTP-klient

NetX Duo SMTP-klienten finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller följande filer:

- **nxd_smtp_client.c** C-källfil för NetX Duo SMTP-klient-API
- **nxd_smtp_client.h** C-rubrikfil för NetX Duo SMTP-klient-API
- **demo_netxduo_smtp_client.c** Demo för NetX Duo SMTP-klient
- **nxd_smtp_client.pdf användarhandbok för** NetX Duo SMTP-klient-API

Om du vill använda NetX Duo SMTP-klient-API:et kan hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "c:*\myproject"* ska *filerna nxd_smtp_client.h och nxd_smtp_client.c* kopieras till den här katalogen.

## <a name="using-netx-duo-smtp-client"></a>Använda NetX Duo SMTP-klient

För att kunna skapa NETX Duo SMTP-klientprogrammet måste det först bygga Biblioteken ThreadX och NetX Duo och inkludera dem i byggprojektet. Programmet måste sedan inkludera tx *_api.h* *och nx_api.h i programmets källkod*. Detta aktiverar ThreadX- och NetX Duo-tjänster. Den måste också innehålla *nxd_smtp_client.c* *och nxd_smtp_client.h* *efter tx_api.h* och nx_api.h för att *kunna använda SMTP-klienttjänster.*

Dessa filer måste kompileras på samma sätt som andra programfiler och objektkoden måste länkas tillsammans med programmets filer. Det här är allt som krävs för att skapa ett NetX Duo SMTP-klientprogram.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur du använder NetX Duo SMTP-klienten beskrivs i bild 1 som visas nedan. Paketpoolen för IP-instansen skapas med hjälp nx_packet_pool_create tjänst på rad 68 och har en mycket liten paketnyttolast. Det beror på att IP-instansen endast skickar kontrollpaket som inte kräver mycket nyttolast. SMTP-klientens paketpool som skapades på rad 84 och används för att överföra SMTP-klientmeddelanden till servern och meddelandedata. Paketnyttolasten är mycket större. IP-instansen skapas på rad 118 med samma paketpool. TCP, som krävs för SMTP-protokollet, är aktiverat på IP-instansen på rad 130.

I programtråden skapas SMTP-klienten med tjänsten *nxd_smtp_client_create,* på rad 170. Tjänsten nxd_smtp_client_create stöder både IPv4- och IPv6 SMTP-serveranslutningar, även om det här *exemplet* är begränsat till IPv4. Sedan skickas e-postmeddelandet till SMTP-klienten för överföring på  rad 184 med nx_smtp_mail_send tjänsten. Observera att ämnesraden med rubriken för e-postinnehåll skapas separat från meddelandetexten. Observera också att begäran om att skicka e-post endast accepterar en mottagares e-postadress som antas vara syntaktiskt korrekt.

Sedan avslutar programmet SMTP-klienten på rad 200. Tjänsten *nx_smtp_client_delete* kontrollerar att socketanslutningen är stängd och porten är obunden. Observera att det är upp till SMTP-klientprogrammet att ta bort paketpoolen om den inte längre används för den.

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

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
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

**Bild 1. Exempel på användning av SMTP-klienten med NetX Duo**

## <a name="client-configuration-options"></a>Klientkonfigurationsalternativ

Det finns flera konfigurationsalternativ med NetX Duo SMTP-klient-API:et. Här följer en lista över alla alternativ som beskrivs i detalj:

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE** Det här alternativet anger storleken på klientens TCP-mottagningsfönster. Detta ska vara inställt på under MTU-storleken för den underliggande Ethernet-maskinvaran och ge utrymme för IP- och TCP-huvuden. Standardstorleken för TCP-fönstret för NetX Duo SMTP-klienten är 1460.
- **NX_SMTP_CLIENT_PACKET_TIMEOUT** Det här alternativet anger tidsgränsen för NetX-paketallokering. Standardvärdet för NetX Duo SMTP-klientpakets timeout är 2 sekunder.
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT** Det här alternativet anger tidsgränsen för klient-TCP-socketanslutning. Standardvärdet för NetX Duo SMTP-klientens anslutningstid är 10 sekunder.
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** Det här alternativet anger tidsgränsen för frånkoppling av klient-TCP-socket. Standardtids gränsen för frånkoppling för NetX Duo SMTP-klienten är 5 sekunder*. Observera att om SMTP-klienten stöter på ett internt fel, till exempel en bruten anslutning, kan anslutningen avslutas med en timeout på noll.
- **NX_SMTP_GREETING_TIMEOUT** Det här alternativet anger tidsgränsen för att klienten ska få servern att svara på sin hälsning. Standardvärdet för NetX Duo SMTP-klienten är 10 sekunder.
- **NX_SMTP_ENVELOPE_TIMEOUT** Det här alternativet anger tidsgränsen för klienten att ta emot serversvaret till ett klientkommando. Standardvärdet för NetX Duo SMTP-klienten är 10 sekunder.
- **NX_SMTP_MESSAGE_TIMEOUT** Det här alternativet anger tidsgränsen för klienten att ta emot serverns svar på att ta emot e-postdata. Standardvärdet för NetX Duo SMTP-klienten är 30 sekunder.
- **NX_SMTP_CLIENT_SEND_TIMEOUT** Det här alternativet definierar väntealternativet för bufferten för att lagra användarlösenordet under SMTP-autentisering med servern. Standardvärdet är 20 byte.
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING** Det här alternativet definierar storleken på bufferten för att extrahera serverutmaningen under SMTP-autentisering. Standardvärdet är 200 byte. För INLOGGNING och PLAIN-autentisering kan SMTP-klienten förmodligen använda en mindre buffert.
- **NX_SMTP_CLIENT_MAX_PASSWORD** Det här alternativet definierar storleken på bufferten för att lagra användarlösenordet under SMTP-autentisering med servern. Standardvärdet är 20 byte. 
- **NX_SMTP_CLIENT_MAX_USERNAME** Det här alternativet definierar storleken på bufferten för att lagra värdens användarnamn under SMTP-autentisering med servern. Standardvärdet är 40 byte. 
