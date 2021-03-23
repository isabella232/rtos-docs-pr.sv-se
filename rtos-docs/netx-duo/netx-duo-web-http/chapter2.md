---
title: Kapitel 2 – installation och användning av HTTP och HTTPS
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX-webb-HTTP-komponenten.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99e649781588b56e72b509c2aa077c38423379d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825704"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a><span data-ttu-id="3fc96-103">Kapitel 2 – installation och användning av HTTP och HTTPS</span><span class="sxs-lookup"><span data-stu-id="3fc96-103">Chapter 2 - Installation and use of HTTP and HTTPS</span></span>

<span data-ttu-id="3fc96-104">Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX-webb-HTTP-komponenten.</span><span class="sxs-lookup"><span data-stu-id="3fc96-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Web HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="3fc96-105">Produkt distribution</span><span class="sxs-lookup"><span data-stu-id="3fc96-105">Product Distribution</span></span>

<span data-ttu-id="3fc96-106">HTTP för NetX finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="3fc96-106">HTTP for NetX is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="3fc96-107">Paketet innehåller tre källfiler, två inkludera filer och en fil som innehåller det här dokumentet, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="3fc96-107">The package includes three source files, two include files, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="3fc96-108">**nx_web_http_common. h** Gemensam huvud fil för NetX-webb-HTTP</span><span class="sxs-lookup"><span data-stu-id="3fc96-108">**nx_web_http_common.h** Common header file for NetX Web HTTP</span></span>
- <span data-ttu-id="3fc96-109">**nx_web_http_client. h** Rubrik fil för HTTP-klient för NetX-webben</span><span class="sxs-lookup"><span data-stu-id="3fc96-109">**nx_web_http_client.h** Header file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="3fc96-110">**nx_web_http_server. h** Rubrik fil för HTTP-server för NetX-webben</span><span class="sxs-lookup"><span data-stu-id="3fc96-110">**nx_web_http_server.h** Header file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="3fc96-111">**nx_web_http_client. c** C-källfil för HTTP-klient för NetX-webben</span><span class="sxs-lookup"><span data-stu-id="3fc96-111">**nx_web_http_client.c** C Source file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="3fc96-112">**nx_web_http_server. c** C-källfil för HTTP-server för NetX-webben</span><span class="sxs-lookup"><span data-stu-id="3fc96-112">**nx_web_http_server.c** C Source file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="3fc96-113">**nx_tcpserver. c** C-källfil för flera TCP-Sockets</span><span class="sxs-lookup"><span data-stu-id="3fc96-113">**nx_tcpserver.c** C Source file for multiple TCP sockets</span></span>
- <span data-ttu-id="3fc96-114">**nx_tcpserver. h** Rubrik fil för definition av HTTPS-server symboler</span><span class="sxs-lookup"><span data-stu-id="3fc96-114">**nx_tcpserver.h** Header file for defining HTTPS Server symbols</span></span>
- <span data-ttu-id="3fc96-115">**nx_md5. c** MD5 Digest-algoritmer</span><span class="sxs-lookup"><span data-stu-id="3fc96-115">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="3fc96-116">**filex_stub. h** Stub-fil om FileX inte finns</span><span class="sxs-lookup"><span data-stu-id="3fc96-116">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="3fc96-117">**nx_web_http.pdf** Beskrivning av HTTP för NetX-webben</span><span class="sxs-lookup"><span data-stu-id="3fc96-117">**nx_web_http.pdf** Description of HTTP for NetX Web</span></span>
- <span data-ttu-id="3fc96-118">**demo_netx_web_http. c** NetX webb-HTTP-demonstration</span><span class="sxs-lookup"><span data-stu-id="3fc96-118">**demo_netx_web_http.c** NetX Web HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="3fc96-119">HTTP-installation</span><span class="sxs-lookup"><span data-stu-id="3fc96-119">HTTP Installation</span></span>

<span data-ttu-id="3fc96-120">För att du ska kunna använda NetX Web HTTP, ska hela distributionen som nämnts tidigare kopieras till samma katalog där NetX Duo är installerat.</span><span class="sxs-lookup"><span data-stu-id="3fc96-120">In order to use NetX Web HTTP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="3fc96-121">Om t. ex. NetX Duo är installerat i katalogen "*\threadx\arm7\green*", så *nx_web_http_client. h* och *Nx_web_http_client. c för netx webb-http-klientprogram och nx_web_http_server. h*, *nx_web_http_server. c, nx_tcpserver. c och nx_tcpserver. h för netx webb-http-serverprogram. För både klient-och serverprogram måste nx_web_http_common. h vara i den här katalogen också. nx_md5. c* bör också kopieras till den här katalogen om Digest-autentisering används.</span><span class="sxs-lookup"><span data-stu-id="3fc96-121">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nx_web_http_client.h* and *nx_web_http_client.c for NetX Web HTTP Client applications, and nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c and nx_tcpserver.h for NetX Web HTTP Server applications. For both client and server applications, nx_web_http_common.h must be in this directory as well. nx_md5.c* should also be copied into this directory if digest authentication is being used.</span></span> <span data-ttu-id="3fc96-122">För demonstrationen av "ram-drivrutinen" program HTTP-klient och server filer bör kopieras till samma katalog.</span><span class="sxs-lookup"><span data-stu-id="3fc96-122">For the demo ‘ram driver’ application HTTP Client and Server files should be copied into the same directory.</span></span>

<span data-ttu-id="3fc96-123">Om du använder TLS bör du ha en separat NetX-säker katalog som innehåller TLS-källfilerna.</span><span class="sxs-lookup"><span data-stu-id="3fc96-123">If using TLS, you should have a separate NetX Secure directory containing the TLS source files.</span></span>

## <a name="using-http"></a><span data-ttu-id="3fc96-124">Använda HTTP</span><span class="sxs-lookup"><span data-stu-id="3fc96-124">Using HTTP</span></span>

<span data-ttu-id="3fc96-125">Det är enkelt att använda NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="3fc96-125">Using NetX Web HTTP is easy.</span></span> <span data-ttu-id="3fc96-126">I princip måste program koden innehålla *nx_web_http_client. h* och/eller *nx_web_http_server. h* när den innehåller *tx_api. h, fx_api. h* och *nx_api. h* (*nx_web_http_common. h* ingår automatiskt).</span><span class="sxs-lookup"><span data-stu-id="3fc96-126">Basically, the application code must include *nx_web_http_client.h* and/or *nx_web_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h* (*nx_web_http_common.h* is automatically included).</span></span> <span data-ttu-id="3fc96-127">Dessa huvuden gör att programmet kan använda ThreadX, FileX och NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3fc96-127">Those headers enable the application to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="3fc96-128">För HTTPS-stöd måste huvudena ingå efter att filen *nx_secure_tls. h* ingår i TLS-stöd.</span><span class="sxs-lookup"><span data-stu-id="3fc96-128">For HTTPS support, the headers must be included after the *nx_secure_tls.h* file is included to bring in TLS support.</span></span>

<span data-ttu-id="3fc96-129">När HTTP-huvudfilerna har inkluderats kan program koden göra HTTP-funktions anropen senare i den här hand boken.</span><span class="sxs-lookup"><span data-stu-id="3fc96-129">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="3fc96-130">Programmet måste också länka till *nx_web_http_client. c för http (s)-klienter*, *nx_web_http_server. c och nx_tcpserver. c för HTTP-servrar* och *nx_md5. c (för sammanfattad autentisering)* i build-processen.</span><span class="sxs-lookup"><span data-stu-id="3fc96-130">The application must also link with *nx_web_http_client.c for HTTP(S) clients*, *nx_web_http_server.c and nx_tcpserver.c for HTTP(S) servers*, and *nx_md5.c (for digest authentication)* in the build process.</span></span> <span data-ttu-id="3fc96-131">De här filerna måste kompileras på samma sätt som andra programfiler och dess objekt formulär måste vara länkade tillsammans med programmets filer.</span><span class="sxs-lookup"><span data-stu-id="3fc96-131">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="3fc96-132">Detta är allt som krävs för att använda NetX webb-HTTP.</span><span class="sxs-lookup"><span data-stu-id="3fc96-132">This is all that is required to use NetX Web HTTP.</span></span>

> [!NOTE]
> <span data-ttu-id="3fc96-133">Om NX_WEB_HTTP_DIGEST_ENABLE inte anges i build-processen behöver inte *MD5. c* -filen läggas till i programmet.</span><span class="sxs-lookup"><span data-stu-id="3fc96-133">If NX_WEB_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="3fc96-134">Om ingen HTTP-klient krävs, kan *nx_web_http_client. c* -filen utelämnas och om ingen http-server krävs, kan *nx_web_http_server. c* utelämnas.</span><span class="sxs-lookup"><span data-stu-id="3fc96-134">Similarly, if no HTTP Client capabilities are required, the *nx_web_http_client.c* file may be omitted and if no HTTP Server capabilities are required, *nx_web_http_server.c* may be omitted.</span></span>
>
> <span data-ttu-id="3fc96-135">Om inte NX_WEB_HTTPS_ENABLE har definierats för att aktivera HTTPS (i stället för att bara använda klartext HTTP) behöver NetX Secure TLS inte finnas i versionen.</span><span class="sxs-lookup"><span data-stu-id="3fc96-135">Unless NX_WEB_HTTPS_ENABLE is defined in order to enable HTTPS (instead of using only plaintext HTTP) then NetX Secure TLS does not need to be in the build.</span></span>
>
> <span data-ttu-id="3fc96-136">Eftersom HTTP använder sig av NetX TCP-tjänster måste TCP aktive ras med *nx_tcp_enable ()* -anropet innan http.</span><span class="sxs-lookup"><span data-stu-id="3fc96-136">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable()* call prior to using HTTP.</span></span>
>
> <span data-ttu-id="3fc96-137">När du använder HTTPS med NetX Secure TLS måste TLS initieras med *nx_secure_tls_initialize ()* innan du anropar https-rutiner.</span><span class="sxs-lookup"><span data-stu-id="3fc96-137">When using HTTPS with NetX Secure TLS, TLS must be initialized with *nx_secure_tls_initialize()* prior to calling HTTPS routines.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="3fc96-138">Litet exempel system</span><span class="sxs-lookup"><span data-stu-id="3fc96-138">Small Example System</span></span>

<span data-ttu-id="3fc96-139">Ett exempel på hur du använder NetX webb-HTTP beskrivs i bild 1,1 nedan.</span><span class="sxs-lookup"><span data-stu-id="3fc96-139">An example of how to use NetX Web HTTP is described in Figure 1.1 below.</span></span>

> [!CAUTION]
> <span data-ttu-id="3fc96-140">Detta tillhandahålls endast i demonstrations syfte och är inte garanterat att kompilera och köra i befintligt skick.</span><span class="sxs-lookup"><span data-stu-id="3fc96-140">This is provided for demonstration purposes only and is not guaranteed to compile and run as is.</span></span>
>
> <span data-ttu-id="3fc96-141">Se NetX Duo HTTPS release Code-distributionen för demo-källfiler som kommer att bygga i den inbyggda Express Logic-miljön.</span><span class="sxs-lookup"><span data-stu-id="3fc96-141">Please refer to the NetX Duo HTTPS release code distribution for  demo source code file(s) that will properly build in the native Express Logic environment.</span></span>  <span data-ttu-id="3fc96-142">Tänk också på att dessa demonstrationer avsiktligt hålls enkla eftersom de är avsedda att introducera HTTPS och/eller NetX Duo HTTPS-program för nya användare.</span><span class="sxs-lookup"><span data-stu-id="3fc96-142">Also be aware that these demos are intentionally kept very simple as they are intended to introduce HTTPS and/or NetX Duo HTTPS application to new users.</span></span>

<span data-ttu-id="3fc96-143">I det här exemplet tas HTTP include-filen *nx_web_http_client. h och nx_web_http_server. h* in (*netx_web_http_common. h* ingår automatiskt).</span><span class="sxs-lookup"><span data-stu-id="3fc96-143">In this example, the HTTP include file *nx_web_http_client.h and nx_web_http_server.h are* brought in (*netx_web_http_common.h* is included automatically).</span></span> <span data-ttu-id="3fc96-144">Därefter skapas HTTP-servern i "*tx_application_define*".</span><span class="sxs-lookup"><span data-stu-id="3fc96-144">Next, the HTTP Server is created in “*tx_application_define*”.</span></span> <span data-ttu-id="3fc96-145">Observera att HTTP Server Control Block "*Server*" har definierats som en global variabel tidigare.</span><span class="sxs-lookup"><span data-stu-id="3fc96-145">Note that the HTTP Server control block “*Server*” was defined as a global variable previously.</span></span> <span data-ttu-id="3fc96-146">HTTPS-servern startas när den har skapats.</span><span class="sxs-lookup"><span data-stu-id="3fc96-146">After successful creation, the HTTPS Server is started.</span></span> <span data-ttu-id="3fc96-147">HTTPS-klienten skapas sedan.</span><span class="sxs-lookup"><span data-stu-id="3fc96-147">The HTTPS Client is then created.</span></span> <span data-ttu-id="3fc96-148">Filen skrivs och filen läses tillbaka.</span><span class="sxs-lookup"><span data-stu-id="3fc96-148">It writes the file and reads the file back.</span></span>

> [!NOTE]
> <span data-ttu-id="3fc96-149">NX_WEB_HTTPS_ENABLE har definierats i det här systemet.</span><span class="sxs-lookup"><span data-stu-id="3fc96-149">NX_WEB_HTTPS_ENABLE is defined on this system.</span></span>

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
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

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

<span data-ttu-id="3fc96-150">**Figur 1,1 exempel på HTTPS-användning med NetX och NetX Secure TLS**</span><span class="sxs-lookup"><span data-stu-id="3fc96-150">**Figure 1.1 Example of HTTPS use with NetX and NetX Secure TLS**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="3fc96-151">Konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="3fc96-151">Configuration Options</span></span>

<span data-ttu-id="3fc96-152">Det finns flera konfigurations alternativ för att skapa HTTP för NetX.</span><span class="sxs-lookup"><span data-stu-id="3fc96-152">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="3fc96-153">Följande är en lista över alla alternativ, där var och en beskrivs i detalj.</span><span class="sxs-lookup"><span data-stu-id="3fc96-153">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="3fc96-154">Standardvärdena visas men kan omdefinieras innan du kan inkludera *nx_web_http_client. h och nx_web_http_server. h*:</span><span class="sxs-lookup"><span data-stu-id="3fc96-154">The default values are listed but can be redefined prior to inclusion of *nx_web_http_client.h and nx_web_http_server.h*:</span></span>

- <span data-ttu-id="3fc96-155">**NX_DISABLE_ERROR_CHECKING** Definierad tar det här alternativet bort grundläggande HTTP-felkontroll.</span><span class="sxs-lookup"><span data-stu-id="3fc96-155">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="3fc96-156">Den används vanligt vis när programmet har felsökts.</span><span class="sxs-lookup"><span data-stu-id="3fc96-156">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="3fc96-157">**NX_WEB_HTTP_DIGEST_ENABLE** Om det här alternativet definieras används autentisering med MD5 Digest på HTTPS-servern.</span><span class="sxs-lookup"><span data-stu-id="3fc96-157">**NX_WEB_HTTP_DIGEST_ENABLE** If defined, authentication using the MD5 digest is enabled on the HTTPS Server.</span></span> <span data-ttu-id="3fc96-158">Som standard är den inte definierad.</span><span class="sxs-lookup"><span data-stu-id="3fc96-158">By default it is not defined.</span></span>
- <span data-ttu-id="3fc96-159">**NX_WEB_HTTP_SERVER_PRIORITY** Prioriteten för HTTPS-serverns tråd.</span><span class="sxs-lookup"><span data-stu-id="3fc96-159">**NX_WEB_HTTP_SERVER_PRIORITY** The priority of the HTTPS Server thread.</span></span> <span data-ttu-id="3fc96-160">Som standard definieras värdet som 16 för att ange prioritet 16.</span><span class="sxs-lookup"><span data-stu-id="3fc96-160">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="3fc96-161">**NX_WEB_HTTP_NO_FILEX** Definierad är det här alternativet en stub för FileX-beroenden.</span><span class="sxs-lookup"><span data-stu-id="3fc96-161">**NX_WEB_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="3fc96-162">HTTPS-klienten fungerar utan några ändringar om det här alternativet har definierats.</span><span class="sxs-lookup"><span data-stu-id="3fc96-162">The HTTPS Client will function without any change if this option is defined.</span></span> <span data-ttu-id="3fc96-163">HTTPS-servern måste antingen ändras eller så måste användaren skapa en fåtal av FileX-tjänsterna för att fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="3fc96-163">The HTTPS Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="3fc96-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Typ av tjänst som krävs för HTTPS TCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="3fc96-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTPS TCP requests.</span></span> <span data-ttu-id="3fc96-165">Som standard definieras det här värdet som NX_IP_NORMAL för att indikera den normala IP-paketfiltrering.</span><span class="sxs-lookup"><span data-stu-id="3fc96-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="3fc96-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** Antalet timer-Tick som server tråden får köra innan den tilldelas trådar av samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="3fc96-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="3fc96-167">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="3fc96-167">The default value is 2.</span></span> <span data-ttu-id="3fc96-168">Observera att det här alternativet är föråldrat.</span><span class="sxs-lookup"><span data-stu-id="3fc96-168">Note this option is deprecated.</span></span>
- <span data-ttu-id="3fc96-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragment aktivera för HTTP TCP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="3fc96-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="3fc96-170">Som standard är det här värdet NX_DONT_FRAGMENT för att inaktivera HTTP TCP-fragmentering.</span><span class="sxs-lookup"><span data-stu-id="3fc96-170">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="3fc96-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Serverns socket Window-storlek.</span><span class="sxs-lookup"><span data-stu-id="3fc96-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="3fc96-172">Som standard är det här värdet 2048 byte.</span><span class="sxs-lookup"><span data-stu-id="3fc96-172">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="3fc96-173">**NX_WEB_HTTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan passera innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="3fc96-173">**NX_WEB_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="3fc96-174">Standardvärdet är inställt på 0x80.</span><span class="sxs-lookup"><span data-stu-id="3fc96-174">The default value is set to 0x80.</span></span>
- <span data-ttu-id="3fc96-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för.</span><span class="sxs-lookup"><span data-stu-id="3fc96-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="3fc96-176">Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="3fc96-176">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="3fc96-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_server_socket_accept ()-* anrop.</span><span class="sxs-lookup"><span data-stu-id="3fc96-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept()* calls.</span></span> <span data-ttu-id="3fc96-178">Standardvärdet är inställt på (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="3fc96-178">The default value is set to (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="3fc96-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_disconnect ()-* anrop.</span><span class="sxs-lookup"><span data-stu-id="3fc96-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect()* calls.</span></span> <span data-ttu-id="3fc96-180">Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="3fc96-180">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="3fc96-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_receive ()-* anrop.</span><span class="sxs-lookup"><span data-stu-id="3fc96-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive()* calls.</span></span> <span data-ttu-id="3fc96-182">Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="3fc96-182">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="3fc96-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Anger antalet ThreadX-Tick som interna tjänster ska pausas för i interna *nx_tcp_socket_send ()-* anrop.</span><span class="sxs-lookup"><span data-stu-id="3fc96-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send()* calls.</span></span> <span data-ttu-id="3fc96-184">Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="3fc96-184">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="3fc96-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **anger den maximala storleken för fältet http-huvud. Standardvärdet är 256.**</span><span class="sxs-lookup"><span data-stu-id="3fc96-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **Specifies the maximum size of the HTTP header field. The default value is 256.**</span></span>
- <span data-ttu-id="3fc96-186">\* \* NX_WEB_HTTP_MULTIPART_ENABLE \* \* \* \* om det är definierat aktiverar HTTPS-servern stöd för multipart HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="3fc96-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*If defined, enables HTTPS Server to support multipart HTTP requests.</span></span> **
- <span data-ttu-id="3fc96-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Anger antalet anslutningar som kan köas för HTTPS-servern.</span><span class="sxs-lookup"><span data-stu-id="3fc96-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTPS Server.</span></span> <span data-ttu-id="3fc96-188">Standardvärdet har angetts till två gånger det maximala antalet serversessioner.</span><span class="sxs-lookup"><span data-stu-id="3fc96-188">The default value is set to twice the maximum number of server sessions.</span></span>
- <span data-ttu-id="3fc96-189">**NX_WEB_HTTP_MAX_RESOURCE** Anger antalet byte som tillåts i ett klient *resurs namn* som anges.</span><span class="sxs-lookup"><span data-stu-id="3fc96-189">**NX_WEB_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="3fc96-190">Standardvärdet är inställt på 40.</span><span class="sxs-lookup"><span data-stu-id="3fc96-190">The default value is set to 40.</span></span>
- <span data-ttu-id="3fc96-191">**NX_WEB_HTTP_MAX_NAME** Anger antalet byte som tillåts i en klient som har angett *användar namn*.</span><span class="sxs-lookup"><span data-stu-id="3fc96-191">**NX_WEB_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="3fc96-192">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="3fc96-192">The default value is set to 20.</span></span>
- <span data-ttu-id="3fc96-193">**NX_WEB_HTTP_MAX_PASSWORD** Anger antalet byte som tillåts i ett *lösen ord* som anges av klienten.</span><span class="sxs-lookup"><span data-stu-id="3fc96-193">**NX_WEB_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="3fc96-194">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="3fc96-194">The default value is set to 20.</span></span>
- <span data-ttu-id="3fc96-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Anger antalet samtidiga sessioner för en HTTP-eller HTTPS-server.</span><span class="sxs-lookup"><span data-stu-id="3fc96-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Specifies the number of simultaneous sessions for an HTTP or HTTPS Server.</span></span> <span data-ttu-id="3fc96-196">En TCP-socket och en TLS-session (om HTTPS har Aktiver ATS) allokeras för varje session.</span><span class="sxs-lookup"><span data-stu-id="3fc96-196">A TCP socket and a TLS session (if HTTPS is enabled) are allocated for each session.</span></span> <span data-ttu-id="3fc96-197">Standardvärdet är inställt på 2.</span><span class="sxs-lookup"><span data-stu-id="3fc96-197">The default value is set to 2.</span></span>
- <span data-ttu-id="3fc96-198">**NX_WEB_HTTPS_ENABLE** Det här makrot aktiverar TLS och HTTPS om det har definierats.</span><span class="sxs-lookup"><span data-stu-id="3fc96-198">**NX_WEB_HTTPS_ENABLE** If defined, this macro enables TLS and HTTPS.</span></span> <span data-ttu-id="3fc96-199">Lämna undefined för att frigöra resurser om bara HTTP i klartext önskas.</span><span class="sxs-lookup"><span data-stu-id="3fc96-199">Leave undefined to free up resources if only plaintext HTTP is desired.</span></span> <span data-ttu-id="3fc96-200">Som standard är det här makrot inte definierat.</span><span class="sxs-lookup"><span data-stu-id="3fc96-200">By default, this macro is not defined.</span></span>
- <span data-ttu-id="3fc96-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** Om det här makrot är definierat inaktive ras HTTP Keep-Alive-funktionen.</span><span class="sxs-lookup"><span data-stu-id="3fc96-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** If defined, this macro disables HTTP keep-alive feature.</span></span> <span data-ttu-id="3fc96-202">Som standard är det här makrot inte definierat.</span><span class="sxs-lookup"><span data-stu-id="3fc96-202">By default, this macro is not defined.</span></span>
- <span data-ttu-id="3fc96-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när servern skapas.</span><span class="sxs-lookup"><span data-stu-id="3fc96-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at server creation.</span></span> <span data-ttu-id="3fc96-204">Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket.</span><span class="sxs-lookup"><span data-stu-id="3fc96-204">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="3fc96-205">Standardvärdet är inställt på 600.</span><span class="sxs-lookup"><span data-stu-id="3fc96-205">The default value is set to 600.</span></span>
- <span data-ttu-id="3fc96-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Anger minimi storleken på paketen i poolen som anges när klienten skapades.</span><span class="sxs-lookup"><span data-stu-id="3fc96-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="3fc96-207">Minimi storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket.</span><span class="sxs-lookup"><span data-stu-id="3fc96-207">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="3fc96-208">Standardvärdet är inställt på 600.</span><span class="sxs-lookup"><span data-stu-id="3fc96-208">The default value is set to 600.</span></span>
- <span data-ttu-id="3fc96-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Ange tids gränsen för återöverföring av Server-socket i sekunder.</span><span class="sxs-lookup"><span data-stu-id="3fc96-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Set the Server socket retransmission timeout in seconds.</span></span> <span data-ttu-id="3fc96-210">Standardvärdet är inställt på 2.</span><span class="sxs-lookup"><span data-stu-id="3fc96-210">The default value is set to 2.</span></span>
- <span data-ttu-id="3fc96-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** Detta anger det maximala antalet återöverföringar på Server-socketen.</span><span class="sxs-lookup"><span data-stu-id="3fc96-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="3fc96-212">Standardvärdet är inställt på 10.</span><span class="sxs-lookup"><span data-stu-id="3fc96-212">The default value is set to 10.</span></span>
- <span data-ttu-id="3fc96-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** Det här värdet används för att ange nästa timeout för återöverföring.</span><span class="sxs-lookup"><span data-stu-id="3fc96-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="3fc96-214">Den aktuella tids gränsen multipliceras med antalet återöverföringar, vilket innebär att värdet för timeout-värdet för socketen flyttas.</span><span class="sxs-lookup"><span data-stu-id="3fc96-214">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="3fc96-215">Standardvärdet är inställt på 1 för dubblerad tids gräns.</span><span class="sxs-lookup"><span data-stu-id="3fc96-215">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="3fc96-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** Detta anger det maximala antalet paket som kan köas på återställnings kön för Server-socket.</span><span class="sxs-lookup"><span data-stu-id="3fc96-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="3fc96-217">Om antalet paket som har placerats i kö når det här antalet kan inga fler paket skickas förrän ett eller flera köade paket släpps.</span><span class="sxs-lookup"><span data-stu-id="3fc96-217">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="3fc96-218">Standardvärdet är inställt på 20.</span><span class="sxs-lookup"><span data-stu-id="3fc96-218">The default value is set to 20.</span></span>
