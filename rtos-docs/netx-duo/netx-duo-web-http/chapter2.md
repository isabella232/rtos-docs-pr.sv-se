---
title: Kapitel 2 – Installation och användning av HTTP och HTTPS
description: Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Web HTTP-komponenten.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fd8ab093d15c5413b0d5dac6d35b080674c3a332ec7a028fc462237135880d34
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783432"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a>Kapitel 2 – Installation och användning av HTTP och HTTPS

Det här kapitlet innehåller en beskrivning av olika problem som rör installation, installation och användning av NetX Web HTTP-komponenten.

## <a name="product-distribution"></a>Produktdistribution

HTTP för NetX finns på [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Paketet innehåller tre källfiler, två inkluderar filer och en fil som innehåller det här dokumentet, enligt följande:

- **nx_web_http_common.h** Gemensam rubrikfil för NetX Web HTTP
- **nx_web_http_client.h** Huvudfil för HTTP-klient för NetX Web
- **nx_web_http_server.h** Huvudfil för HTTP Server för NetX Web
- **nx_web_http_client.c** C-källfil för HTTP-klient för NetX Web
- **nx_web_http_server.c** C-källfil för HTTP Server för NetX Web
- **nx_tcpserver.c** C-källfil för flera TCP-sockets
- **nx_tcpserver.h** Rubrikfil för att definiera HTTPS-serversymboler
- **nx_md5.c** MD5-sammanfattande algoritmer
- **filex_stub.h** Stub-fil om FileX inte finns
- **nx_web_http.pdf** Beskrivning av HTTP för NetX Web
- **demo_netx_web_http.c** Demonstration av NetX Web HTTP

## <a name="http-installation"></a>HTTP-installation

För att kunna använda NetX Web HTTP bör hela distributionen som nämns ovan kopieras till samma katalog där NetX Duo är installerat. Om NetX Duo till exempel är installerat i katalogen "*\threadx\arm7\green*" så är *nx_web_http_client.h* och *nx_web_http_client.c för NetX Web HTTP-klientprogram och nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c och nx_tcpserver.h för NetX-webb-HTTP Server-program. För både klient- och serverprogram måste nx_web_http_common.h också finnas i den här katalogen. nx_md5.c* bör också kopieras till den här katalogen om sammanfattad autentisering används. För demonstrationen ska HTTP-klient- och serverfilerna för RAM-drivrutinsprogrammet kopieras till samma katalog.

Om du använder TLS bör du ha en separat NetX Secure-katalog som innehåller TLS-källfilerna.

## <a name="using-http"></a>Använda HTTP

Det är enkelt att använda NetX Web HTTP. I princip måste programkoden innehålla *nx_web_http_client.h* och/eller *nx_web_http_server.h* när den *innehåller tx_api.h, fx_api.h* och *nx_api.h* (*nx_web_http_common.h* ingår automatiskt). Dessa huvuden gör det möjligt för programmet att använda ThreadX, FileX respektive NetX Duo. För HTTPS-stöd måste huvudena inkluderas när *filen nx_secure_tls.h* har inkluderats för att få TLS-stöd.

När HTTP-huvudfilerna har inkluderats kan programkoden sedan göra HTTP-funktionsanrop som anges senare i den här guiden. Programmet måste också länka till *nx_web_http_client.c för HTTP(S)-klienter*, *nx_web_http_server.c och nx_tcpserver.c för HTTP(S)-servrar* och *nx_md5.c (för* sammanfattad autentisering) i byggprocessen. Dessa filer måste kompileras på samma sätt som andra programfiler och dess objektformulär måste länkas tillsammans med programmets filer. Det här är allt som krävs för att använda NetX Web HTTP.

> [!NOTE]
> Om NX_WEB_HTTP_DIGEST_ENABLE inte har angetts i byggprocessen behöver *filen md5.c* inte läggas till i programmet. Om inga HTTP-klientfunktioner krävs kan filen *nx_web_http_client.c* utelämnas och om inga HTTP-serverfunktioner krävs *kan nx_web_http_server.c* utelämnas.
>
> Om NX_WEB_HTTPS_ENABLE inte definieras för att aktivera HTTPS (i stället för att endast använda HTTP i klartext) behöver NetX Secure TLS inte finnas i bygget.
>
> Eftersom HTTP använder NetX TCP-tjänster måste TCP aktiveras med *nx_tcp_enable()-anropet* innan HTTP används.
>
> När du använder HTTPS med NetX Secure TLS måste TLS initieras *med nx_secure_tls_initialize()* innan HTTPS-rutiner anropas.

## <a name="small-example-system"></a>Litet exempelsystem

Ett exempel på hur du använder NetX Web HTTP beskrivs i bild 1.1 nedan.

> [!CAUTION]
> Detta tillhandahålls endast i demonstrationssyfte och är inte garanterat att kompileras och köras som det är.
>
> Se NetX Duo HTTPS-versionens koddistribution för demokällkodfiler som kommer att byggas korrekt i den inbyggda Express Logic-miljön.  Tänk också på att dessa demonstrationer avsiktligt hålls mycket enkla eftersom de är avsedda att introducera HTTPS och/eller NetX Duo HTTPS-program för nya användare.

I det här exemplet hämtas *HTTP-indelningsfilen nx_web_http_client.h och nx_web_http_server.h* (*netx_web_http_common.h* inkluderas automatiskt). Därefter skapas HTTP-servern i "*tx_application_define*". Observera att HTTP-serverkontrollblocket "*Server*" definierades som en global variabel tidigare. NÄR HTTPS-servern har skapats startas den. HTTPS-klienten skapas sedan. Den skriver filen och läser tillbaka filen.

> [!NOTE]
> NX_WEB_HTTPS_ENABLE definieras i det här systemet.

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

**Bild 1.1 Exempel på HTTPS-användning med NetX och NetX Secure TLS**

## <a name="configuration-options"></a>Konfigurationsalternativ

Det finns flera konfigurationsalternativ för att skapa HTTP för NetX. Nedan följer en lista över alla alternativ, där vart och ett beskrivs i detalj. Standardvärdena visas men kan definieras om innan du tar med *nx_web_http_client.h och nx_web_http_server.h:*

- **NX_DISABLE_ERROR_CHECKING** Det här alternativet tar bort den grundläggande HTTP-felkontrollen. Det används vanligtvis när programmet har felsökts.
- **NX_WEB_HTTP_DIGEST_ENABLE** Om autentisering med MD5-sammanfattningen har definierats är det aktiverat på HTTPS-servern. Som standard definieras den inte.
- **NX_WEB_HTTP_SERVER_PRIORITY** Https-servertrådens prioritet. Som standard definieras det här värdet som 16 för att ange prioritet 16.
- **NX_WEB_HTTP_NO_FILEX** Det här alternativet har definierats och tillhandahåller en stub för FileX-beroenden. HTTPS-klienten fungerar utan ändringar om det här alternativet har definierats. HTTPS-servern måste antingen ändras eller så måste användaren skapa ett fåtal FileX-tjänster för att fungera korrekt.
- **NX_WEB_HTTP_TYPE_OF_SERVICE** Typ av tjänst som krävs för HTTPS TCP-begäranden. Som standard definieras det här värdet som NX_IP_NORMAL för att indikera normal IP-pakettjänst.
- **NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** Antalet timer tick som Server-tråden tillåts köra innan den ger till trådar med samma prioritet. Standardvärdet är 2. Observera att det här alternativet är inaktuellt.
- **NX_WEB_HTTP_FRAGMENT_OPTION** Aktivera fragment för HTTP TCP-begäranden. Som standard är det här värdet NX_DONT_FRAGMENT inaktivera HTTP TCP-fragmentering.
- **NX_WEB_HTTP_SERVER_WINDOW_SIZE** Fönsterstorlek för serversocket. Som standard är det här värdet 2 048 byte.
- **NX_WEB_HTTP_TIME_TO_LIVE** Anger antalet routrar som det här paketet kan skicka innan det tas bort. Standardvärdet är inställt på 0x80.
- **NX_WEB_HTTP_SERVER_TIMEOUT** Anger antalet ThreadX-tick som interna tjänster ska pausas för. Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Anger antalet ThreadX-tick som interna tjänster pausar för i interna *nx_tcp_server_socket_accept()-anrop.* Standardvärdet är inställt på (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Anger antalet ThreadX-tick som interna tjänster pausar för i interna *nx_tcp_socket_disconnect()-anrop.* Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Anger antalet ThreadX-tick som interna tjänster pausar för i interna *nx_tcp_socket_receive()-anrop.* Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Anger antalet ThreadX-tick som interna tjänster ska pausa för i interna *nx_tcp_socket_send()-anrop.* Standardvärdet är inställt på 10 sekunder (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_MAX_HEADER_FIELD** **Anger den maximala storleken för HTTP-rubrikfältet. Standardvärdet är 256.**
- **NX_WEB_HTTP_MULTIPART_ENABLE ** **Om https-servern har definierats kan den ge stöd för HTTP-begäranden med flera delar. **
- **NX_WEB_HTTP_SERVER_MAX_PENDING** Anger antalet anslutningar som kan köas för HTTPS-servern. Standardvärdet är inställt på två gånger det maximala antalet serversessioner.
- **NX_WEB_HTTP_MAX_RESOURCE** Anger antalet byte som tillåts i ett resursnamn som tillhandahålls *av en klient.* Standardvärdet är inställt på 40.
- **NX_WEB_HTTP_MAX_NAME** Anger antalet byte som tillåts i ett användarnamn som tillhandahålls av *en klient.* Standardvärdet är inställt på 20.
- **NX_WEB_HTTP_MAX_PASSWORD** Anger antalet byte som tillåts i ett lösenord som anges av *klienten.* Standardvärdet är inställt på 20.
- **NX_WEB_HTTP_SERVER_SESSION_MAX** Anger antalet samtidiga sessioner för en HTTP- eller HTTPS-server. En TCP-socket och en TLS-session (om HTTPS är aktiverat) allokeras för varje session. Standardvärdet är inställt på 2.
- **NX_WEB_HTTPS_ENABLE** Om det här makrot definieras aktiveras TLS och HTTPS. Lämna odefinierat för att frigöra resurser om du bara vill använda HTTP i klartext. Som standard definieras inte det här makrot.
- **NX_WEB_HTTPS_KEEPALIVE_DISABLE** Om det här makrot har definierats inaktiveras HTTP keep-alive-funktionen. Som standard definieras inte det här makrot.
- **NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Anger den minsta storleken på paketen i poolen som angavs när servern skapades. Den minsta storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket. Standardvärdet är inställt på 600.
- **NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Anger den minsta storleken på paketen i poolen som angavs när klienten skapades. Den minsta storleken krävs för att säkerställa att det fullständiga HTTP-huvudet kan finnas i ett paket. Standardvärdet är inställt på 600.
- **NX_WEB_HTTP_SERVER_RETRY_SECONDS** Ange tidsgränsen för återöverföring av serversocket i sekunder. Standardvärdet är inställt på 2.
- **NX_WEB_HTTP_ SERVER_RETRY_MAX** Detta anger det maximala antalet återöverföringar på serversocketen. Standardvärdet är inställt på 10.
- **NX_WEB_HTTP_ SERVER_RETRY_SHIFT** Det här värdet används för att ange nästa tidsgräns för återöverföring. Den aktuella tidsgränsen multipliceras med antalet återöverföringar hittills, skiftat med värdet för socket-timeout-skiftet. Standardvärdet är inställt på 1 för att dubblera tidsgränsen.
- **NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** Detta anger det maximala antalet paket som kan finnas i kö för återöverföring av serversocket. Om antalet paket som tas iqueued når det här antalet kan inga fler paket skickas förrän ett eller flera paket i rad släpps. Standardvärdet är inställt på 20.
