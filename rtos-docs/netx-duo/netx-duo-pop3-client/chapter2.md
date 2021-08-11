---
title: Kapitel 2 – Installation och användning av NetX Duo POP3-klient
description: NetX Duo POP3-klienten innehåller en källfil, en rubrikfil och en demofil.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5a3cbded6224617571941f58ffb6a08bde9575eba8791544182fb8499c14bf43
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797202"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-pop3-client"></a>Kapitel 2 – Installation och användning av NetX Duo POP3-klient

NetX POP3 Client innehåller en källfil, en rubrikfil och en demofil. Det finns ytterligare två filer för MD5-sammanfattande tjänster. Det finns också en PDF-fil med användarhandboken (det här dokumentet).

- **nxd_pop3_client.c** C-källfil för NetX Duo POP3-klient-API
- **nxd_pop3_client.h** C-rubrikfil för NetX Duo POP3-klient-API
- **demo_netxduo_pop3_client.c** Demofil för skapande av POP3-klient och sessionsinitiering
- **nx_md5.c** C-källfil som definierar MD5-sammanfattande tjänster
- **nx_md5.h** C-rubrikfil som definierar MD5-sammanfattande tjänster
- **nxd_pop3_client.pdf** Användarhandbok för NetX Duo POP3-klient

Om du vill använda NetX Duo POP3-klienten kan hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\mcf5272\green*" ska filerna *nx_md5.h*, *nx_md5.c,* *nxd_pop3_client.h och nxd_pop3_client.c* kopieras till den här katalogen.

## <a name="using-netx-duo-pop3-client"></a>Använda NetX Duo POP3-klient

Om du vill använda NetX Duo POP3-klienttjänsten måste programmet *lägga till nxd_pop3_client.c i* sitt byggprojekt. Programkoden måste innehålla *nx_md5.h och nxd_pop3_client.h* *efter tx_api.h* *och nx_api.h* för att kunna använda ThreadX och NetX Duo.

De här filerna måste kompileras på samma sätt som andra programfiler och objektkoden måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX Duo POP3-klienten.

## <a name="small-example-of-the-netx-duo-pop3-client"></a>Litet exempel på NetX Duo POP3-klienten

Ett exempel på hur du använder NetX Duo POP3-klienttjänster beskrivs i bild 1 som visas nedan. I den här demonstrationen konfigureras de två återanropen för meddelanden om nedladdning av e-post och slutförande av sessioner på raderna 37 och 38. POP3-klientpaketpoolen skapas på rad 76. IP-trådaktiviteten skapas på rad 88. Observera att den här paketpoolen också används för POP3-klientpaketpoolen. TCP är aktiverat för IP-aktiviteten på rad 107.

POP3-klienten skapas på rad 133 i programtrådens postfunktion, *demo_thread_entry*. Det beror på att *nx_pop3_client_create* också försöker upprätta en TCP-anslutning med POP3-servern. Om det lyckas frågar programmet POP3-servern efter antalet objekt i sin maildrop på rad 149 med *hjälp av nx_pop3_client_mail_items_get tjänsten.*

Om det finns ett eller flera objekt itererar programmet genom while-loopen för varje e-postobjekt för att ladda ned e-postmeddelandet. RETR-begäran görs på rad 149 i *det nx_pop3_client_mail_item_get anropet.* Om det lyckas laddar programmet ned paket med *hjälp av nx_pop3_client_mail_item_message_get-tjänsten* på rad 177 tills det upptäcker att det sista paketet i meddelandet har tagits emot på rad 196. Slutligen tar programmet bort e-postobjektet, förutsatt att en lyckad nedladdning har gjorts på rad 199 *i nx_pop3_client_mail_item_delete anropet.* RFC 1939 rekommenderar att POP3-klienter instruerar servern att ta bort nedladdade e-postobjekt för att förhindra att e-post ackumuleras i klientens maildrop. Servern kan göra det ändå automatiskt.

När alla e-postobjekt har laddats ned, eller om ett POP3-klienttjänstanrop misslyckas, avslutas loopen och POP3-klienten tas bort på rad 217 *med hjälp av nx_pop3_client_delete tjänsten.*

```C
/*
   demo_netxduo_pop3.c

   This is a small demo of POP3 Client on the NetX Duo TCP/IP stack.
   This demo relies on Thread, NetX Duo and POP3 Client API to conduct
   a POP3 mail session.
 */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_pop3_client.h"

#define DEMO_STACK_SIZE             4096
#define CLIENT_ADDRESS              IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS              IP_ADDRESS(192,2,2,89)
#define SERVER_PORT                 110

/* Replace the 'ram' driver with your own Ethernet driver. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client.  */

TX_THREAD           demo_client_thread;
NX_POP3_CLIENT      demo_client;
NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void    demo_thread_entry(ULONG info);


  /* Shared secret is the same as password. */

#define LOCALHOST                               "recipient@domain.com"
#define LOCALHOST_PASSWORD                      "testpwd"

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT     status;
    UCHAR    *free_memory_pointer;


    /* Setup the working pointer.  */
    free_memory_pointer =  first_unused_memory;

    /* Create a client thread.  */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                     free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                     TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer =  free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                                    PAYLOAD_SIZE, free_memory_pointer,
                                    (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);


    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                          CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                          _nx_ram_network_driver, free_memory_pointer,
                          2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}



/* Define the application thread entry function. */

void    demo_thread_entry(ULONG info)
{

    UINT        status;
    UINT        mail_item, number_mail_items;
    UINT        bytes_downloaded = 0;
    UINT        final_packet = NX_FALSE;
    ULONG       total_size, mail_item_size, bytes_retrieved;
    NX_PACKET   *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);


    /* Create a NetX POP3 Client instance with no byte or block memory pools.
       Note that it uses its password for its APOP shared secret. */
    status =  nx_pop3_client_create(&demo_client,
                                    NX_TRUE,
                                    &client_ip, &client_packet_pool, SERVER_ADDRESS,
                                    SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox.  */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items,
                                            &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {

        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items.  */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {


        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item,
                                               &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely
           downloaded. */
        while((final_packet ==  NX_FALSE) && (status == NX_SUCCESS))
        {

            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {

                break;
            }

            if (bytes_retrieved != 0)
            {

                printf("Received %d bytes of data for item %d: %s\n",
                        packet_ptr -> nx_packet_length,
                        mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);

    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client.  This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

**Bild 1. Exempel på ett NetX Duo POP3-klientprogram**

## <a name="pop3-client-configuration-options"></a>Konfigurationsalternativ för POP3-klient

Det finns flera konfigurationsalternativ med NetX Duo POP3-klienten. Här följer en lista över alla alternativ som beskrivs i detalj:

- **NX_POP3_CLIENT_PACKET_TIMEOUT** Detta definierar väntealternativet i sekunder för POP3-klienten att allokera ett paket. Standardvärdet är 1 sekund.
- **NX_POP3_CLIENT_CONNECTION_TIMEOUT** Detta definierar väntealternativet i sekunder för ATT POP3-klienten ska ansluta till POP3-servern. Standardvärdet är 30 sekunder.
- **NX_POP3_CLIENT_DISCONNECT_TIMEOUT** Detta definierar väntealternativet i sekunder för ATT POP3-klienten ska koppla från POP3-servern. Standardvärdet är 2 sekunder.
- **NX_POP3_TCP_SOCKET_SEND_WAIT** Det här alternativet anger väntealternativet i sekunder i *nx_tcp_socket_send tjänstsamtal.* Standardvärdet är 2 sekunder.
- **NX_POP3_SERVER_REPLY_TIMEOUT** Det här alternativet anger väntealternativet *i nx_tcp_socket_receive* för serversvar på en klientbegäran. Standardvärdet är 10 sekunder.
- **NX_POP3_CLIENT_TCP_WINDOW_SIZE** Det här alternativet anger storleken på klientens TCP-mottagningsfönster. Detta ska anges till MTU-storleken för IP-instansen minus IP- och TCP-huvudet. Standardvärdet är 1460. Detta bör vara mindre om programmet skickar POP3-paket över IPv6 (1 440 byte) för att ta hänsyn till det större IPv6-huvudet.
- **NX_POP3_MAX_USERNAME** Det här alternativet anger storleken på bufferten för POP3-klientens användarnamn. Standardvärdet är 40 byte.
- **NX_POP3_MAX_PASSWORD** Det här alternativet anger storleken på bufferten för POP3-klientlösenordet. Standardvärdet är 20 byte.
