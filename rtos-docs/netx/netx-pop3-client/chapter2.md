---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX POP3-klienten
description: NetX POP3-klienten innehåller en källfil, en rubrik fil och en demonstrations fil. Det finns två ytterligare filer för MD5 Digest-tjänster.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24de396c69d458866f9423fd995bcb8d905f29c8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826664"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX POP3-klienten

NetX POP3-klienten innehåller en källfil, en rubrik fil och en demonstrations fil. Det finns två ytterligare filer för MD5 Digest-tjänster. Det finns också en PDF-fil för användar guiden (det här dokumentet).

- **nx_pop3_client. c**: c-källfil för netx POP3-klient-API
- **nx_pop3_client. h**: C-huvud fil för netx POP3-klient-API
- **demo_netxduo_pop3_client. c**: demo filen för skapande av POP3-klienten och initiering av session
- **nx_md5. c**: c-källfil som definierar MD5 Digest-tjänster
- **nx_md5. h**: C-rubrik fil som definierar MD5 Digest-tjänster
- **nx_pop3_client.pdf**: netx POP3-klient Användar handbok

Om du vill använda NetX POP3-klienten kan hela distributionen som du tidigare kopiera till samma katalog som NetX är installerad på. Om NetX till exempel är installerat i katalogen "*\threadx\mcf5272\green*", ska *nx_md5. h*, *nx_md5. c,* *nx_pop3_client. h och nx_pop3_client. c* -filer kopieras till den här katalogen.

## <a name="using-netx-pop3-client"></a>Använda NetX POP3-klienten

Om du vill använda NetX POP3-klient tjänsten måste programmet lägga till *nx_pop3_client. c* i sitt build-projekt. Program koden måste innehålla *nx_md5. h, nx_pop3. h och nx_pop3_client. h* efter *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx.

Filerna måste kompileras på samma sätt som andra programfiler och objekt koden måste vara länkad tillsammans med programmets filer. Detta är allt som krävs för att använda NetX POP3-klienten.

## <a name="small-example-of-the-netx-pop3-client"></a>Litet exempel på POP3-klienten för NetX

Ett exempel på hur du använder NetX POP3-klient tjänster beskrivs i bild 1 som visas nedan. Den här demon konfigurerar de två återanropen för att skicka meddelanden om hämtning av e-post och slut för ande av sessioner på raderna 37 och 38. POP3-klientens adresspool skapas på rad 76. Aktiviteten IP-tråd skapas på rad 88. Observera att denna adresspool också används för POP3-klientens adresspool. TCP är aktiverat på IP-uppgiften på rad 107.

POP3-klienten skapas på rad 133 i funktionen för tråd inmatning i programmet *demo_thread_entry*. Detta beror på att *nx_pop3_client_creates* tjänsten även försöker upprätta en TCP-anslutning till POP3-servern. Om det lyckas frågar programmet POP3-servern efter antalet objekt i dess maildrop på rad 149 med hjälp av tjänsten *nx_pop3_client_mail_items_get* .

Om det finns ett eller flera objekt itererar programmet igenom slingan för varje e-postobjekt för att hämta e-postmeddelandet. RETR-begäran görs på rad 149 i *nx_pop3_client_mail_item_get* -anropet. Om det lyckas laddar programmet ned paket med hjälp av *nx_pop3_client_mail_item_message_get* tjänsten på rad 177 till den identifierar det sista paketet i meddelandet har tagits emot på rad 196. Slutligen tar programmet bort e-postobjektet, förutsatt att en lyckad nedladdning har skett på rad 199 i *nx_pop3_client_mail_item_delete* -anropet. RFC 1939 rekommenderar att POP3-klienter instruerar servern att ta bort hämtade e-postobjekt för att förhindra att e-post ackumuleras i klientens maildrop. Servern kan ändå göra det automatiskt.

När alla e-postobjekt har laddats ned, eller om ett anrop till POP3-klienten Miss lyckas, avslutar programmet och tar bort POP3-klienten på rad 217 med hjälp av tjänsten *nx_pop3_client_delete* .

```c
/*
    demo_netxduo_pop3.c

    This is a small demo of POP3 Client on the NetX TCP/IP stack.
    This demo relies on Thread, NetX and POP3 Client API to conduct
    a POP3 mail session.
*/

#include "tx_api.h"
#include "nx_api.h"
#include "nx_pop3_client.h"

#define DEMO_STACK_SIZE        4096
#define CLIENT_ADDRESS         IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS         IP_ADDRESS(192,2,2,89)
#define SERVER_PORT            110

/* Replace the 'ram' driver with your own Ethernet driver. */
void _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client. */

TX_THREAD          demo_client_thread;
NX_POP3_CLIENT     demo_client;
NX_PACKET_POOL     client_packet_pool;
NX_IP              client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void     demo_thread_entry(ULONG info);

/* Shared secret is the same as password. */

#define LOCALHOST              "recipient@domain.com"
#define LOCALHOST_PASSWORD     "testpwd"

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *free_memory_pointer;

    /* Setup the working pointer. */
    free_memory_pointer = first_unused_memory;

    /* Create a client thread. */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                    free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer = free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* The demo client username and password is the authentication
    data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status = nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                        PAYLOAD_SIZE, free_memory_pointer, (PAYLOAD_SIZE * 10));
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
    free_memory_pointer = free_memory_pointer + 2048;

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

void demo_thread_entry(ULONG info)
{

UINT          status;
UINT          mail_item, number_mail_items;
UINT          bytes_downloaded = 0;
UINT          final_packet = NX_FALSE;
ULONG         total_size, mail_item_size, bytes_retrieved;
NX_PACKET     *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);

    /* Create a NetX POP3 Client instance with no byte or block memory pools.
    Note that it uses its password for its APOP shared secret. */
    status = nx_pop3_client_create(&demo_client,
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

    /* Find out how many items are in our mailbox. */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items, &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {
        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items. */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {

        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item, &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely downloaded. */

        while((final_packet == NX_FALSE) && (status == NX_SUCCESS))
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

    /* Delete the POP3 Client. This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

Bild 1. Exempel på ett NetX POP3-klient program

## <a name="pop3-client-configuration-options"></a>Konfigurations alternativ för POP3-klienten

Det finns flera konfigurations alternativ med NetX POP3-klienten. Nedan visas en lista över alla alternativ som beskrivs i detalj:

- **NX_POP3_CLIENT_PACKET_TIMEOUT**: Detta definierar vänte alternativet i sekunder för POP3-klienten för att allokera ett paket. Standardvärdet är 1 sekund.

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT**: Detta definierar vänte alternativet i sekunder för POP3-klienten att ansluta till POP3-servern. Standardvärdet är 30 sekunder.

- **NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: Detta definierar vänte alternativet i sekunder för att POP3-klienten ska koppla från POP3-servern. Standardvärdet är 2 sekunder.

- **NX_POP3_TCP_SOCKET_SEND_WAIT**: det här alternativet anger vänte alternativet i sekunder i *nx_tcp_socket_send* tjänst anrop. Standardvärdet är 2 sekunder.

- **NX_POP3_SERVER_REPLY_TIMEOUT**: det här alternativet anger vänte alternativet i *nx_tcp_socket_receive* tjänst anrop för att servern ska svara på en klientbegäran. Standardvärdet är 10 sekunder.

- **NX_POP3_CLIENT_TCP_WINDOW_SIZE**: det här alternativet anger storleken på KLIENTens TCP-mottagningsfönstret. Detta ska vara inställt på IP-instansens MTU-storlek minus IP-och TCP-huvud. Standardvärdet är 1460.

- **NX_POP3_MAX_USERNAME**: det här alternativet anger storleken på bufferten för POP3-klientens användar namn. Standardvärdet är 40 byte.

- **NX_POP3_MAX_PASSWORD**: det här alternativet anger storleken på bufferten för POP3-klientens lösen ord. Standardvärdet är 20 byte.