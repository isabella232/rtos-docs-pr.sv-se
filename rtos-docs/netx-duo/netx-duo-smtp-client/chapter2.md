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
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a><span data-ttu-id="24875-103">Kapitel 2 – installation och användning av NetX Duo SMTP-klienten</span><span class="sxs-lookup"><span data-stu-id="24875-103">Chapter 2 - Installation and use of NetX Duo SMTP client</span></span>

<span data-ttu-id="24875-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Duo SMTP-klient komponenten.</span><span class="sxs-lookup"><span data-stu-id="24875-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo SMTP Client component.</span></span>

## <a name="netx-duo-smtp-client-installation"></a><span data-ttu-id="24875-105">NetX Duo SMTP-klient installation</span><span class="sxs-lookup"><span data-stu-id="24875-105">NetX Duo SMTP Client Installation</span></span>

<span data-ttu-id="24875-106">NetX Duo SMTP-klienten finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="24875-106">The NetX Duo SMTP Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="24875-107">Paketet innehåller följande filer:</span><span class="sxs-lookup"><span data-stu-id="24875-107">The package includes the following files:</span></span>

- <span data-ttu-id="24875-108">**nxd_smtp_client. c** C-källfil för NetX Duo SMTP client API</span><span class="sxs-lookup"><span data-stu-id="24875-108">**nxd_smtp_client.c** C Source file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="24875-109">**nxd_smtp_client. h** C-huvud fil för NetX Duo SMTP-klient-API</span><span class="sxs-lookup"><span data-stu-id="24875-109">**nxd_smtp_client.h** C Header file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="24875-110">**demo_netxduo_smtp_client. c** Demo för NetX Duo SMTP-klient</span><span class="sxs-lookup"><span data-stu-id="24875-110">**demo_netxduo_smtp_client.c** Demo for NetX Duo SMTP Client</span></span>
- <span data-ttu-id="24875-111">**nxd_smtp_client.pdf användar guide för** NetX Duo SMTP-klient-API</span><span class="sxs-lookup"><span data-stu-id="24875-111">**nxd_smtp_client.pdf User Guide for** NetX Duo SMTP Client API</span></span>

<span data-ttu-id="24875-112">Om du vill använda NetX Duo SMTP client API, kan hela distributionen som tidigare har kopierats till samma katalog som NetX Duo är installerad på.</span><span class="sxs-lookup"><span data-stu-id="24875-112">To use the NetX Duo SMTP Client API, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="24875-113">Om t. ex. NetX Duo installeras i katalogen "c:*\myproject*" måste *nxd_smtp_client. h-och nxd_smtp_client. c-* filerna kopieras till den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="24875-113">For example, if NetX Duo is installed in the directory “c:*\myproject*” then the *nxd_smtp_client.h, and nxd_smtp_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-smtp-client"></a><span data-ttu-id="24875-114">Använda NetX Duo SMTP client</span><span class="sxs-lookup"><span data-stu-id="24875-114">Using NetX Duo SMTP Client</span></span>

<span data-ttu-id="24875-115">För att skapa NetX Duo SMTP-klientprogrammet måste du först skapa ThreadX-och NetX Duo-biblioteken och inkludera dem i build-projektet.</span><span class="sxs-lookup"><span data-stu-id="24875-115">To create the NetX Duo SMTP Client application, it must first build the ThreadX and NetX Duo libraries and include them in the build project.</span></span> <span data-ttu-id="24875-116">Programmet måste sedan ta med TX-*_api. h* och *nx_api. h i programmets käll kod*.</span><span class="sxs-lookup"><span data-stu-id="24875-116">The application must then include tx *_api.h* and *nx_api.h in its application source code*.</span></span> <span data-ttu-id="24875-117">Detta aktiverar ThreadX-och NetX Duo-tjänster.</span><span class="sxs-lookup"><span data-stu-id="24875-117">This will enable ThreadX and NetX Duo services.</span></span> <span data-ttu-id="24875-118">Det måste också innehålla *nxd_smtp_client. c* och *nxd_smtp_client. h* efter *tx_api. h* och *nx_api. h för att använda SMTP-klienttjänster.*</span><span class="sxs-lookup"><span data-stu-id="24875-118">It must also include *nxd_smtp_client.c* and *nxd_smtp_client.h* after *tx_api.h* and *nx_api.h to use SMTP Client services.*</span></span>

<span data-ttu-id="24875-119">Filerna måste kompileras på samma sätt som andra programfiler och objekt koden måste vara länkad tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="24875-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="24875-120">Detta är allt som krävs för att skapa ett NetX Duo SMTP-klientprogram.</span><span class="sxs-lookup"><span data-stu-id="24875-120">This is all that is required to create a NetX Duo SMTP Client application.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="24875-121">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="24875-121">Small Example System</span></span>

<span data-ttu-id="24875-122">Ett exempel på hur du använder NetX Duo SMTP-klienten beskrivs i bild 1 som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="24875-122">An example of using the NetX Duo SMTP Client is described in Figure 1 that appears below.</span></span> <span data-ttu-id="24875-123">Paketets pool för IP-instansen skapas med hjälp av nx_packet_pool_create-tjänsten, på rad 68 och har en mycket liten paket nytto Last.</span><span class="sxs-lookup"><span data-stu-id="24875-123">The packet pool for the IP instance is created using the nx_packet_pool_create service, on line 68 and has a very small packet payload.</span></span> <span data-ttu-id="24875-124">Detta beror på att IP-instansen bara skickar kontroll paket som inte kräver mycket nytto Last.</span><span class="sxs-lookup"><span data-stu-id="24875-124">This is because the IP instance only sends control packets which don’t require much payload.</span></span> <span data-ttu-id="24875-125">SMTP-klientcachen som skapats på rad 84 och används för att överföra SMTP-klient meddelanden till servern och meddelande data.</span><span class="sxs-lookup"><span data-stu-id="24875-125">The SMTP Client packet pool created on line 84 and is used for transmitting SMTP Client messages to the server and message data.</span></span> <span data-ttu-id="24875-126">Paketets nytto Last är mycket större.</span><span class="sxs-lookup"><span data-stu-id="24875-126">Its packet payload is much larger.</span></span> <span data-ttu-id="24875-127">IP-instansen skapas på rad 118 med samma adresspool.</span><span class="sxs-lookup"><span data-stu-id="24875-127">The IP instance is created in line 118 using the same packet pool.</span></span> <span data-ttu-id="24875-128">TCP, som krävs för SMTP-protokollet, är aktiverat på IP-instansen på rad 130.</span><span class="sxs-lookup"><span data-stu-id="24875-128">TCP, required for the SMTP protocol, is enabled on the IP instance in line 130.</span></span>

<span data-ttu-id="24875-129">I program tråden skapas SMTP-klienten med hjälp av *nxd_smtp_client_create* -tjänsten, på rad 170.</span><span class="sxs-lookup"><span data-stu-id="24875-129">In the application thread, the SMTP Client is created using the *nxd_smtp_client_create* service, in line 170.</span></span> <span data-ttu-id="24875-130">Tjänsten *nxd_smtp_client_create* stöder både IPv4-och IPv6 SMTP-server anslutningar, även om det här exemplet är begränsat till IPv4.</span><span class="sxs-lookup"><span data-stu-id="24875-130">The *nxd_smtp_client_create* service supports both IPv4 and IPv6 SMTP server connections although this example is limited to IPv4.</span></span> <span data-ttu-id="24875-131">Sedan skickas e-postmeddelandet till SMTP-klienten för överföring på rad 184 med hjälp av tjänsten *nx_smtp_mail_send* .</span><span class="sxs-lookup"><span data-stu-id="24875-131">Then the mail message is submitted to the SMTP Client for transmission on line 184 using the *nx_smtp_mail_send* service.</span></span> <span data-ttu-id="24875-132">Observera att ämnes raden med e-postmeddelandets innehålls rubrik skapas separat från meddelande texten.</span><span class="sxs-lookup"><span data-stu-id="24875-132">Note that the subject line with the mail content header is created separately from the message body.</span></span> <span data-ttu-id="24875-133">Observera också att skicka e-postbegäran endast accepterar en mottagares e-postadress som antas vara syntaktiskt korrekt.</span><span class="sxs-lookup"><span data-stu-id="24875-133">Also note that the send mail request accepts only one recipient mail address which is assumed to be syntactically correct.</span></span>

<span data-ttu-id="24875-134">Sedan avslutar programmet SMTP-klienten på rad 200.</span><span class="sxs-lookup"><span data-stu-id="24875-134">Then the application terminates the SMTP Client on line 200.</span></span> <span data-ttu-id="24875-135">*Nx_smtp_client_deletes* tjänsten kontrollerar att socket-anslutningen är stängd och porten är obunden.</span><span class="sxs-lookup"><span data-stu-id="24875-135">The *nx_smtp_client_delete* service checks that the socket connection is closed and the port is unbound.</span></span> <span data-ttu-id="24875-136">Observera att det är upp till SMTP-klientprogrammet att ta bort poolen om den inte längre används för den.</span><span class="sxs-lookup"><span data-stu-id="24875-136">Note that it is up to the SMTP Client application to delete the packet pool if it no longer has use for it.</span></span>

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

<span data-ttu-id="24875-137">**Bild 1. Exempel på SMTP-klient användning med NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="24875-137">**Figure 1. Example of SMTP Client use with NetX Duo**</span></span>

## <a name="client-configuration-options"></a><span data-ttu-id="24875-138">Alternativ för klient konfiguration</span><span class="sxs-lookup"><span data-stu-id="24875-138">Client Configuration Options</span></span>

<span data-ttu-id="24875-139">Det finns flera konfigurations alternativ med NetX Duo SMTP client API.</span><span class="sxs-lookup"><span data-stu-id="24875-139">There are several configuration options with the NetX Duo SMTP Client API.</span></span> <span data-ttu-id="24875-140">Nedan visas en lista över alla alternativ som beskrivs i detalj:</span><span class="sxs-lookup"><span data-stu-id="24875-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="24875-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** Det här alternativet anger storleken på klientens TCP-mottagningsfönstret.</span><span class="sxs-lookup"><span data-stu-id="24875-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="24875-142">Detta ska anges till under MTU-storleken för den underliggande Ethernet-maskinvaran och tillåta utrymme för IP-och TCP-huvuden.</span><span class="sxs-lookup"><span data-stu-id="24875-142">This should be set to below the MTU size of the underlying Ethernet hardware and allow room for IP and TCP headers.</span></span> <span data-ttu-id="24875-143">Standardvärdet för NetX Duo SMTP-klienten TCP Window är 1460.</span><span class="sxs-lookup"><span data-stu-id="24875-143">The default NetX Duo SMTP Client TCP window size is 1460.</span></span>
- <span data-ttu-id="24875-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** Det här alternativet anger tids gränsen för NetX-paket tilldelning.</span><span class="sxs-lookup"><span data-stu-id="24875-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** This option sets the timeout on NetX packet allocation.</span></span> <span data-ttu-id="24875-145">Standardvärdet för NetX Duo SMTP-klientprogrammet är 2 sekunder.</span><span class="sxs-lookup"><span data-stu-id="24875-145">The default NetX Duo SMTP Client packet timeout is 2 seconds.</span></span>
- <span data-ttu-id="24875-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** Det här alternativet anger klientens timeout för TCP-socket Connect.</span><span class="sxs-lookup"><span data-stu-id="24875-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** This option sets the Client TCP socket connect timeout.</span></span> <span data-ttu-id="24875-147">Standardvärdet för NetX Duo SMTP Client Connect är 10 sekunder.</span><span class="sxs-lookup"><span data-stu-id="24875-147">The default NetX Duo SMTP Client connect timeout is 10 seconds.</span></span>
- <span data-ttu-id="24875-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** Det här alternativet anger timeout för klientens TCP-socket.</span><span class="sxs-lookup"><span data-stu-id="24875-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** This option sets the Client TCP socket disconnect timeout.</span></span> <span data-ttu-id="24875-149">Standardvärdet för NetX Duo SMTP client från koppling är 5 sekunder \*.</span><span class="sxs-lookup"><span data-stu-id="24875-149">The default NetX Duo SMTP Client disconnect timeout is 5 seconds\*.</span></span> <span data-ttu-id="24875-150">Observera att om SMTP-klienten påträffar ett internt fel, till exempel en bruten anslutning, kan det leda till att anslutningen avbryts med en timeout på noll vänte.</span><span class="sxs-lookup"><span data-stu-id="24875-150">Note that if the SMTP Client encounters an internal error such as a broken connection it may terminate the connection with a zero wait timeout.</span></span>
- <span data-ttu-id="24875-151">**NX_SMTP_GREETING_TIMEOUT** Med det här alternativet anges timeout-värdet för klienten för att ta emot servern svar på dess hälsning.</span><span class="sxs-lookup"><span data-stu-id="24875-151">**NX_SMTP_GREETING_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to its greeting.</span></span> <span data-ttu-id="24875-152">Standardvärdet för NetX Duo SMTP-klienten är 10 sekunder.</span><span class="sxs-lookup"><span data-stu-id="24875-152">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="24875-153">**NX_SMTP_ENVELOPE_TIMEOUT** Med det här alternativet anges tids gränsen för klienten att ta emot servern svara på ett klient kommando.</span><span class="sxs-lookup"><span data-stu-id="24875-153">**NX_SMTP_ENVELOPE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to a Client command.</span></span> <span data-ttu-id="24875-154">Standardvärdet för NetX Duo SMTP-klienten är 10 sekunder.</span><span class="sxs-lookup"><span data-stu-id="24875-154">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="24875-155">**NX_SMTP_MESSAGE_TIMEOUT** Med det här alternativet anges tids gränsen för klienten att ta emot Server svaret för att ta emot e-postmeddelande data.</span><span class="sxs-lookup"><span data-stu-id="24875-155">**NX_SMTP_MESSAGE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to receiving the mail message data.</span></span> <span data-ttu-id="24875-156">Standardvärdet för NetX Duo SMTP-klienten är 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="24875-156">The default NetX Duo SMTP Client value is 30 seconds.</span></span>
- <span data-ttu-id="24875-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** Det här alternativet definierar vänte alternativet för bufferten för att lagra användar lösen ordet under SMTP-autentisering med-servern.</span><span class="sxs-lookup"><span data-stu-id="24875-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** This option defines the wait option of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="24875-158">Standardvärdet är 20 byte.</span><span class="sxs-lookup"><span data-stu-id="24875-158">The default value is 20 bytes.</span></span>
- <span data-ttu-id="24875-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** Med det här alternativet definieras storleken på bufferten för extrahering av Server utmaningen under SMTP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="24875-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** This option defines the size of the buffer for extracting the Server challenge during SMTP authentication.</span></span> <span data-ttu-id="24875-160">Standardvärdet är 200 byte.</span><span class="sxs-lookup"><span data-stu-id="24875-160">The default value is 200 bytes.</span></span> <span data-ttu-id="24875-161">För inloggning och enkel autentisering kan SMTP-klienten förmodligen använda en mindre buffert.</span><span class="sxs-lookup"><span data-stu-id="24875-161">For LOGIN and PLAIN authentication, the SMTP Client can probably use a smaller buffer.</span></span>
- <span data-ttu-id="24875-162">**NX_SMTP_CLIENT_MAX_PASSWORD** Med det här alternativet definieras storleken på bufferten för att lagra användar lösen ordet under SMTP-autentisering med-servern.</span><span class="sxs-lookup"><span data-stu-id="24875-162">**NX_SMTP_CLIENT_MAX_PASSWORD** This option defines the size of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="24875-163">Standardvärdet är 20 byte.</span><span class="sxs-lookup"><span data-stu-id="24875-163">The default value is 20 bytes.</span></span> 
- <span data-ttu-id="24875-164">**NX_SMTP_CLIENT_MAX_USERNAME** Med det här alternativet definieras storleken på bufferten för att lagra värd användar namnet under SMTP-autentisering med-servern.</span><span class="sxs-lookup"><span data-stu-id="24875-164">**NX_SMTP_CLIENT_MAX_USERNAME** This option defines the size of the buffer to store the host username during SMTP authentication with the Server.</span></span> <span data-ttu-id="24875-165">Standardvärdet är 40 byte.</span><span class="sxs-lookup"><span data-stu-id="24875-165">The default value is 40 bytes.</span></span> 
