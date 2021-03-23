---
title: Kapitel 2 – installation och användning av NetX Duo SMTP-klienten
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo SMTP-klient komponenten.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825785"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>Kapitel 2 – installation och användning av NetX Duo SMTP-klienten

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo SMTP-klient komponenten.

## <a name="netx-duo-smtp-client-installation"></a>NetX Duo SMTP-klient installation

NetX Duo SMTP-klienten finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller följande filer:

- **nxd_smtp_client. c** C-källfil för NetX Duo SMTP client API
- **nxd_smtp_client. h** C-huvud fil för NetX Duo SMTP-klient-API
- **demo_netxduo_smtp_client. c** Demo för NetX Duo SMTP-klient
- **nxd_smtp_client.pdf användar guide för** NetX Duo SMTP-klient-API

Om du vill använda NetX Duo SMTP client API, kan hela distributionen som tidigare har kopierats till samma katalog som NetX Duo är installerad på. Om t. ex. NetX Duo installeras i katalogen "c:*\myproject*" måste *nxd_smtp_client. h-och nxd_smtp_client. c-* filerna kopieras till den här katalogen.

## <a name="using-netx-duo-smtp-client"></a>Använda NetX Duo SMTP client

För att skapa NetX Duo SMTP-klientprogrammet måste du först skapa ThreadX-och NetX Duo-biblioteken och inkludera dem i build-projektet. Programmet måste sedan ta med TX-*_api. h* och *nx_api. h i programmets käll kod*. Detta aktiverar ThreadX-och NetX Duo-tjänster. Det måste också innehålla *nxd_smtp_client. c* och *nxd_smtp_client. h* efter *tx_api. h* och *nx_api. h för att använda SMTP-klienttjänster.*

Filerna måste kompileras på samma sätt som andra programfiler och objekt koden måste vara länkad tillsammans med programmets filer. Detta är allt som krävs för att skapa ett NetX Duo SMTP-klientprogram.

## <a name="small-example-system"></a>Litet exempel system

Ett exempel på hur du använder NetX Duo SMTP-klienten beskrivs i bild 1 som visas nedan. Paketets pool för IP-instansen skapas med hjälp av nx_packet_pool_create-tjänsten, på rad 68 och har en mycket liten paket nytto Last. Detta beror på att IP-instansen bara skickar kontroll paket som inte kräver mycket nytto Last. SMTP-klientcachen som skapats på rad 84 och används för att överföra SMTP-klient meddelanden till servern och meddelande data. Paketets nytto Last är mycket större. IP-instansen skapas på rad 118 med samma adresspool. TCP, som krävs för SMTP-protokollet, är aktiverat på IP-instansen på rad 130.

I program tråden skapas SMTP-klienten med hjälp av *nxd_smtp_client_create* -tjänsten, på rad 170. Tjänsten *nxd_smtp_client_create* stöder både IPv4-och IPv6 SMTP-server anslutningar, även om det här exemplet är begränsat till IPv4. Sedan skickas e-postmeddelandet till SMTP-klienten för överföring på rad 184 med hjälp av tjänsten *nx_smtp_mail_send* . Observera att ämnes raden med e-postmeddelandets innehålls rubrik skapas separat från meddelande texten. Observera också att skicka e-postbegäran endast accepterar en mottagares e-postadress som antas vara syntaktiskt korrekt.

Sedan avslutar programmet SMTP-klienten på rad 200. *Nx_smtp_client_deletes* tjänsten kontrollerar att socket-anslutningen är stängd och porten är obunden. Observera att det är upp till SMTP-klientprogrammet att ta bort poolen om den inte längre används för den.

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

**Bild 1. Exempel på SMTP-klient användning med NetX Duo**

## <a name="client-configuration-options"></a>Alternativ för klient konfiguration

Det finns flera konfigurations alternativ med NetX Duo SMTP client API. Nedan visas en lista över alla alternativ som beskrivs i detalj:

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE** Det här alternativet anger storleken på klientens TCP-mottagningsfönstret. Detta ska anges till under MTU-storleken för den underliggande Ethernet-maskinvaran och tillåta utrymme för IP-och TCP-huvuden. Standardvärdet för NetX Duo SMTP-klienten TCP Window är 1460.
- **NX_SMTP_CLIENT_PACKET_TIMEOUT** Det här alternativet anger tids gränsen för NetX-paket tilldelning. Standardvärdet för NetX Duo SMTP-klientprogrammet är 2 sekunder.
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT** Det här alternativet anger klientens timeout för TCP-socket Connect. Standardvärdet för NetX Duo SMTP Client Connect är 10 sekunder.
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** Det här alternativet anger timeout för klientens TCP-socket. Standardvärdet för NetX Duo SMTP client från koppling är 5 sekunder *. Observera att om SMTP-klienten påträffar ett internt fel, till exempel en bruten anslutning, kan det leda till att anslutningen avbryts med en timeout på noll vänte.
- **NX_SMTP_GREETING_TIMEOUT** Med det här alternativet anges timeout-värdet för klienten för att ta emot servern svar på dess hälsning. Standardvärdet för NetX Duo SMTP-klienten är 10 sekunder.
- **NX_SMTP_ENVELOPE_TIMEOUT** Med det här alternativet anges tids gränsen för klienten att ta emot servern svara på ett klient kommando. Standardvärdet för NetX Duo SMTP-klienten är 10 sekunder.
- **NX_SMTP_MESSAGE_TIMEOUT** Med det här alternativet anges tids gränsen för klienten att ta emot Server svaret för att ta emot e-postmeddelande data. Standardvärdet för NetX Duo SMTP-klienten är 30 sekunder.
- **NX_SMTP_CLIENT_SEND_TIMEOUT** Det här alternativet definierar vänte alternativet för bufferten för att lagra användar lösen ordet under SMTP-autentisering med-servern. Standardvärdet är 20 byte.
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING** Med det här alternativet definieras storleken på bufferten för extrahering av Server utmaningen under SMTP-autentisering. Standardvärdet är 200 byte. För inloggning och enkel autentisering kan SMTP-klienten förmodligen använda en mindre buffert.
- **NX_SMTP_CLIENT_MAX_PASSWORD** Med det här alternativet definieras storleken på bufferten för att lagra användar lösen ordet under SMTP-autentisering med-servern. Standardvärdet är 20 byte. 
- **NX_SMTP_CLIENT_MAX_USERNAME** Med det här alternativet definieras storleken på bufferten för att lagra värd användar namnet under SMTP-autentisering med-servern. Standardvärdet är 40 byte. 
