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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a><span data-ttu-id="e3b34-104">Kapitel 2 – installation och användning av Azure återställnings tider NetX POP3-klienten</span><span class="sxs-lookup"><span data-stu-id="e3b34-104">Chapter 2 - Installation and use of Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="e3b34-105">NetX POP3-klienten innehåller en källfil, en rubrik fil och en demonstrations fil.</span><span class="sxs-lookup"><span data-stu-id="e3b34-105">NetX POP3 Client includes one source file, one header file, and a demo file.</span></span> <span data-ttu-id="e3b34-106">Det finns två ytterligare filer för MD5 Digest-tjänster.</span><span class="sxs-lookup"><span data-stu-id="e3b34-106">There are two additional files for MD5 digest services.</span></span> <span data-ttu-id="e3b34-107">Det finns också en PDF-fil för användar guiden (det här dokumentet).</span><span class="sxs-lookup"><span data-stu-id="e3b34-107">There is also a User Guide PDF file (this document).</span></span>

- <span data-ttu-id="e3b34-108">**nx_pop3_client. c**: c-källfil för netx POP3-klient-API</span><span class="sxs-lookup"><span data-stu-id="e3b34-108">**nx_pop3_client.c**: C Source file for NetX POP3 Client API</span></span>
- <span data-ttu-id="e3b34-109">**nx_pop3_client. h**: C-huvud fil för netx POP3-klient-API</span><span class="sxs-lookup"><span data-stu-id="e3b34-109">**nx_pop3_client.h**: C Header file for NetX POP3 Client API</span></span>
- <span data-ttu-id="e3b34-110">**demo_netxduo_pop3_client. c**: demo filen för skapande av POP3-klienten och initiering av session</span><span class="sxs-lookup"><span data-stu-id="e3b34-110">**demo_netxduo_pop3_client.c**: Demo file for POP3 Client creation and session initiation</span></span>
- <span data-ttu-id="e3b34-111">**nx_md5. c**: c-källfil som definierar MD5 Digest-tjänster</span><span class="sxs-lookup"><span data-stu-id="e3b34-111">**nx_md5.c**: C Source file defining MD5 digest services</span></span>
- <span data-ttu-id="e3b34-112">**nx_md5. h**: C-rubrik fil som definierar MD5 Digest-tjänster</span><span class="sxs-lookup"><span data-stu-id="e3b34-112">**nx_md5.h**: C Header file defining MD5 digest services</span></span>
- <span data-ttu-id="e3b34-113">**nx_pop3_client.pdf**: netx POP3-klient Användar handbok</span><span class="sxs-lookup"><span data-stu-id="e3b34-113">**nx_pop3_client.pdf**: NetX POP3 Client User Guide</span></span>

<span data-ttu-id="e3b34-114">Om du vill använda NetX POP3-klienten kan hela distributionen som du tidigare kopiera till samma katalog som NetX är installerad på.</span><span class="sxs-lookup"><span data-stu-id="e3b34-114">To use NetX POP3 Client, the entire distribution mentioned previously can be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="e3b34-115">Om NetX till exempel är installerat i katalogen "*\threadx\mcf5272\green*", ska *nx_md5. h*, *nx_md5. c,* *nx_pop3_client. h och nx_pop3_client. c* -filer kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="e3b34-115">For example, if NetX is installed in the directory "*\threadx\mcf5272\green*" then the *nx_md5.h*, *nx_md5.c,* *nx_pop3_client.h, and nx_pop3_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-pop3-client"></a><span data-ttu-id="e3b34-116">Använda NetX POP3-klienten</span><span class="sxs-lookup"><span data-stu-id="e3b34-116">Using NetX POP3 Client</span></span>

<span data-ttu-id="e3b34-117">Om du vill använda NetX POP3-klient tjänsten måste programmet lägga till *nx_pop3_client. c* i sitt build-projekt.</span><span class="sxs-lookup"><span data-stu-id="e3b34-117">To use the NetX POP3 Client service, the application must add *nx_pop3_client.c* to its build project.</span></span> <span data-ttu-id="e3b34-118">Program koden måste innehålla *nx_md5. h, nx_pop3. h och nx_pop3_client. h* efter *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx.</span><span class="sxs-lookup"><span data-stu-id="e3b34-118">The application code must include *nx_md5.h, nx_pop3.h and nx_pop3_client.h* after *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span>

<span data-ttu-id="e3b34-119">Filerna måste kompileras på samma sätt som andra programfiler och objekt koden måste vara länkad tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="e3b34-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="e3b34-120">Detta är allt som krävs för att använda NetX POP3-klienten.</span><span class="sxs-lookup"><span data-stu-id="e3b34-120">This is all that is required to use the NetX POP3 Client.</span></span>

## <a name="small-example-of-the-netx-pop3-client"></a><span data-ttu-id="e3b34-121">Litet exempel på POP3-klienten för NetX</span><span class="sxs-lookup"><span data-stu-id="e3b34-121">Small Example of the NetX POP3 Client</span></span>

<span data-ttu-id="e3b34-122">Ett exempel på hur du använder NetX POP3-klient tjänster beskrivs i bild 1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="e3b34-122">An example of how to use NetX POP3 Client services is described in Figure 1 that appears below.</span></span> <span data-ttu-id="e3b34-123">Den här demon konfigurerar de två återanropen för att skicka meddelanden om hämtning av e-post och slut för ande av sessioner på raderna 37 och 38.</span><span class="sxs-lookup"><span data-stu-id="e3b34-123">This demo sets up the two callbacks for notification of mail download and session completion on lines 37 and 38.</span></span> <span data-ttu-id="e3b34-124">POP3-klientens adresspool skapas på rad 76.</span><span class="sxs-lookup"><span data-stu-id="e3b34-124">The POP3 Client packet pool is created on line 76.</span></span> <span data-ttu-id="e3b34-125">Aktiviteten IP-tråd skapas på rad 88.</span><span class="sxs-lookup"><span data-stu-id="e3b34-125">The IP thread task is created on line 88.</span></span> <span data-ttu-id="e3b34-126">Observera att denna adresspool också används för POP3-klientens adresspool.</span><span class="sxs-lookup"><span data-stu-id="e3b34-126">Note that this packet pool is also used for the POP3 Client packet pool.</span></span> <span data-ttu-id="e3b34-127">TCP är aktiverat på IP-uppgiften på rad 107.</span><span class="sxs-lookup"><span data-stu-id="e3b34-127">TCP is enabled on the IP task in line 107.</span></span>

<span data-ttu-id="e3b34-128">POP3-klienten skapas på rad 133 i funktionen för tråd inmatning i programmet *demo_thread_entry*.</span><span class="sxs-lookup"><span data-stu-id="e3b34-128">The POP3 Client is created on line 133 inside the application thread entry function, *demo_thread_entry*.</span></span> <span data-ttu-id="e3b34-129">Detta beror på att *nx_pop3_client_creates* tjänsten även försöker upprätta en TCP-anslutning till POP3-servern.</span><span class="sxs-lookup"><span data-stu-id="e3b34-129">This is because the *nx_pop3_client_create* service also attempts to make a TCP connection with the POP3 server.</span></span> <span data-ttu-id="e3b34-130">Om det lyckas frågar programmet POP3-servern efter antalet objekt i dess maildrop på rad 149 med hjälp av tjänsten *nx_pop3_client_mail_items_get* .</span><span class="sxs-lookup"><span data-stu-id="e3b34-130">If successful, the application queries the POP3 server for the number of items in its maildrop on line 149 using the *nx_pop3_client_mail_items_get* service.</span></span>

<span data-ttu-id="e3b34-131">Om det finns ett eller flera objekt itererar programmet igenom slingan för varje e-postobjekt för att hämta e-postmeddelandet.</span><span class="sxs-lookup"><span data-stu-id="e3b34-131">If there are one or more items, the application iterates through the while loop for each mail item to download the mail message.</span></span> <span data-ttu-id="e3b34-132">RETR-begäran görs på rad 149 i *nx_pop3_client_mail_item_get* -anropet.</span><span class="sxs-lookup"><span data-stu-id="e3b34-132">The RETR request is made on line 149 in the *nx_pop3_client_mail_item_get* call.</span></span> <span data-ttu-id="e3b34-133">Om det lyckas laddar programmet ned paket med hjälp av *nx_pop3_client_mail_item_message_get* tjänsten på rad 177 till den identifierar det sista paketet i meddelandet har tagits emot på rad 196.</span><span class="sxs-lookup"><span data-stu-id="e3b34-133">If successful, the application downloads packets using the *nx_pop3_client_mail_item_message_get* service on line 177 till it detects the last packet in the message has been received on line 196.</span></span> <span data-ttu-id="e3b34-134">Slutligen tar programmet bort e-postobjektet, förutsatt att en lyckad nedladdning har skett på rad 199 i *nx_pop3_client_mail_item_delete* -anropet.</span><span class="sxs-lookup"><span data-stu-id="e3b34-134">Lastly, the application deletes the mail item, assuming a successful download has occurred on line 199 in *the nx_pop3_client_mail_item_delete* call.</span></span> <span data-ttu-id="e3b34-135">RFC 1939 rekommenderar att POP3-klienter instruerar servern att ta bort hämtade e-postobjekt för att förhindra att e-post ackumuleras i klientens maildrop.</span><span class="sxs-lookup"><span data-stu-id="e3b34-135">The RFC 1939 recommends that POP3 Clients instruct the Server to delete downloaded mail items to prevent mail accumulating in the Client's maildrop.</span></span> <span data-ttu-id="e3b34-136">Servern kan ändå göra det automatiskt.</span><span class="sxs-lookup"><span data-stu-id="e3b34-136">The Server may automatically do so anyway.</span></span>

<span data-ttu-id="e3b34-137">När alla e-postobjekt har laddats ned, eller om ett anrop till POP3-klienten Miss lyckas, avslutar programmet och tar bort POP3-klienten på rad 217 med hjälp av tjänsten *nx_pop3_client_delete* .</span><span class="sxs-lookup"><span data-stu-id="e3b34-137">Once all the mail items are downloaded, or if a POP3 Client service call fails, the application exits of the loop and deletes the POP3 Client on line 217 using the *nx_pop3_client_delete* service.</span></span>

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

<span data-ttu-id="e3b34-138">Bild 1.</span><span class="sxs-lookup"><span data-stu-id="e3b34-138">Figure 1.</span></span> <span data-ttu-id="e3b34-139">Exempel på ett NetX POP3-klient program</span><span class="sxs-lookup"><span data-stu-id="e3b34-139">Example of a NetX POP3 Client application</span></span>

## <a name="pop3-client-configuration-options"></a><span data-ttu-id="e3b34-140">Konfigurations alternativ för POP3-klienten</span><span class="sxs-lookup"><span data-stu-id="e3b34-140">POP3 Client Configuration Options</span></span>

<span data-ttu-id="e3b34-141">Det finns flera konfigurations alternativ med NetX POP3-klienten.</span><span class="sxs-lookup"><span data-stu-id="e3b34-141">There are several configuration options with the NetX POP3 Client.</span></span> <span data-ttu-id="e3b34-142">Nedan visas en lista över alla alternativ som beskrivs i detalj:</span><span class="sxs-lookup"><span data-stu-id="e3b34-142">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="e3b34-143">**NX_POP3_CLIENT_PACKET_TIMEOUT**: Detta definierar vänte alternativet i sekunder för POP3-klienten för att allokera ett paket.</span><span class="sxs-lookup"><span data-stu-id="e3b34-143">**NX_POP3_CLIENT_PACKET_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to allocate a packet.</span></span> <span data-ttu-id="e3b34-144">Standardvärdet är 1 sekund.</span><span class="sxs-lookup"><span data-stu-id="e3b34-144">The default value is 1 second.</span></span>

- <span data-ttu-id="e3b34-145">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: Detta definierar vänte alternativet i sekunder för POP3-klienten att ansluta till POP3-servern.</span><span class="sxs-lookup"><span data-stu-id="e3b34-145">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to connect with the POP3 Server.</span></span> <span data-ttu-id="e3b34-146">Standardvärdet är 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="e3b34-146">The default value is 30 seconds.</span></span>

- <span data-ttu-id="e3b34-147">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: Detta definierar vänte alternativet i sekunder för att POP3-klienten ska koppla från POP3-servern.</span><span class="sxs-lookup"><span data-stu-id="e3b34-147">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to disconnect from the POP3 Server.</span></span> <span data-ttu-id="e3b34-148">Standardvärdet är 2 sekunder.</span><span class="sxs-lookup"><span data-stu-id="e3b34-148">The default value is 2 seconds.</span></span>

- <span data-ttu-id="e3b34-149">**NX_POP3_TCP_SOCKET_SEND_WAIT**: det här alternativet anger vänte alternativet i sekunder i *nx_tcp_socket_send* tjänst anrop.</span><span class="sxs-lookup"><span data-stu-id="e3b34-149">**NX_POP3_TCP_SOCKET_SEND_WAIT**: This option sets the wait option in seconds in *nx_tcp_socket_send* service calls.</span></span> <span data-ttu-id="e3b34-150">Standardvärdet är 2 sekunder.</span><span class="sxs-lookup"><span data-stu-id="e3b34-150">The default value is 2 seconds.</span></span>

- <span data-ttu-id="e3b34-151">**NX_POP3_SERVER_REPLY_TIMEOUT**: det här alternativet anger vänte alternativet i *nx_tcp_socket_receive* tjänst anrop för att servern ska svara på en klientbegäran.</span><span class="sxs-lookup"><span data-stu-id="e3b34-151">**NX_POP3_SERVER_REPLY_TIMEOUT**: This option sets the wait option in *nx_tcp_socket_receive* service calls for the Server reply to a Client request.</span></span> <span data-ttu-id="e3b34-152">Standardvärdet är 10 sekunder.</span><span class="sxs-lookup"><span data-stu-id="e3b34-152">The default value is 10 seconds.</span></span>

- <span data-ttu-id="e3b34-153">**NX_POP3_CLIENT_TCP_WINDOW_SIZE**: det här alternativet anger storleken på KLIENTens TCP-mottagningsfönstret.</span><span class="sxs-lookup"><span data-stu-id="e3b34-153">**NX_POP3_CLIENT_TCP_WINDOW_SIZE**: This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="e3b34-154">Detta ska vara inställt på IP-instansens MTU-storlek minus IP-och TCP-huvud.</span><span class="sxs-lookup"><span data-stu-id="e3b34-154">This should be set to the IP instance MTU size minus the IP and TCP header.</span></span> <span data-ttu-id="e3b34-155">Standardvärdet är 1460.</span><span class="sxs-lookup"><span data-stu-id="e3b34-155">The default value is 1460.</span></span>

- <span data-ttu-id="e3b34-156">**NX_POP3_MAX_USERNAME**: det här alternativet anger storleken på bufferten för POP3-klientens användar namn.</span><span class="sxs-lookup"><span data-stu-id="e3b34-156">**NX_POP3_MAX_USERNAME**: This option sets the size of the buffer of the POP3 Client user name.</span></span> <span data-ttu-id="e3b34-157">Standardvärdet är 40 byte.</span><span class="sxs-lookup"><span data-stu-id="e3b34-157">The default value is 40 bytes.</span></span>

- <span data-ttu-id="e3b34-158">**NX_POP3_MAX_PASSWORD**: det här alternativet anger storleken på bufferten för POP3-klientens lösen ord.</span><span class="sxs-lookup"><span data-stu-id="e3b34-158">**NX_POP3_MAX_PASSWORD**: This option sets the size of the buffer of the POP3 Client password.</span></span> <span data-ttu-id="e3b34-159">Standardvärdet är 20 byte.</span><span class="sxs-lookup"><span data-stu-id="e3b34-159">The default value is 20 bytes.</span></span>