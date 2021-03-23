---
title: Kapitel 2 – installation och användning av Azure återställnings tider NetX Secure
description: Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av NetX Secure-komponenten.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3ef82bd113518b35105fb2eefe23bd3e755ca06
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826952"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a>Kapitel 2 – installation och användning av Azure återställnings tider NetX Secure

Det här kapitlet innehåller en beskrivning av olika problem som rör Installation, konfiguration och användning av Azure återställnings tider NetX Secure-komponenten.

## <a name="product-version-number"></a>Produkt versions nummer

Användaren kan kontrol lera produkt versions numret genom att söka efter följande symboler i nx_secure_tls. h:

***NETX_SECURE_MAJOR_VERSION***

***NETX_SECURE_MINOR_VERSION***

Service Pack-versionerna har följande symbol definierad för att ange service pack nummer:

***NETX_SECURE_SERVICE_PACK_VERSION***

## <a name="product-distribution"></a>Produkt distribution

NetX Secure finns på [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Paketet inkluderar källfiler, inkludera filer och en PDF-fil som innehåller det här dokumentet, enligt följande:

- **nx_secure_tls_api. h** Offentlig API-huvud fil för NetX Secure TLS
- **nx_secure_tls_user. h** Användaren definierar huvud filen för NetX Secure TLS
- **nx_secure_tls_port. h** Plattformsspecifika definitioner för NetX Secure
- **nx_secure_tls. h** Rubrik fil för NetX Secure TLS
- **nx_secure_tls&#42;. c/h** C/H-källfiler för NetX Secure TLS
- **nx_crypto&#42;. c/h** C/H-källfiler för NetX-säker kryptografi
- **nx_secure_x509&#42;. c/h** C/H källfiler för X. 509 digitala certifikat.
- **demo_netx_secure_tls. c** C-källfil för NetX Secure TLS-demo
- **NetX_Secure_User_Guide.pdf** PDF-Beskrivning av NetX säker produkt

> [!NOTE]
> Nx_crypto *-filer tillhandahålls för olika maskinvaruplattformar i en under katalog till den säkra överordnade katalogen NetX.

## <a name="netx-secure-installation"></a>NetX-säker installation

För att kunna använda NetX säker, ska hela distributionen som nämnts tidigare kopieras till samma katalog nivå där NetX har installerats. Om NetX till exempel är installerat i katalogen "*\threadx\arm7\NetX*" *, så nx_secure * *.* kataloger bör kopieras till "*\threadx\arm7\NetXSecure*".

## <a name="using-netx-secure"></a>Använda NetX Secure

Det är enkelt att använda NetX Secure TLS. I princip måste program koden innehålla *nx_secure_tls_api. h* när den innehåller *tx_api. h* och *nx_api. h* för att kunna använda ThreadX och netx. När *nx_secure_tls_api. h* ingår kan program koden sedan göra de netx-säkra funktions anrop som anges längre fram i den här hand boken. Programmet måste också importera *nx_secure * *.* filer till ett NetXSecure-bibliotek och den plattformsspecifik *nx_crypto * *.* filer till ett NetXCrypto-bibliotek.

## <a name="small-example-system-tls-client"></a>Litet exempel system (TLS-klient)

Ett exempel på hur enkelt det är att använda NetX Secure beskrivs i bild 1,1, som visas nedan. Detta visar en enkel TLS-klient med hjälp av moduler för program varu kryptografi (inte maskin varu information) för kryptering. Den är utformad för att fungera med OpenSSL-servern för omvänd-eko (OpenSSL s_server-rev).

Observera att du behöver ett X. 509 CA-certifikat för att autentisera mål serverns certifikat för att kunna köra det här exemplet. I OpenSSL-exemplet räcker det att använda enkel PKI på två nivåer (rot certifikat för certifikat utfärdare-> >Server certifikat). Du måste fylla i matrisen "trusted_ca_data" med en DER-kodad binär version av CA-certifikatet och uppdatera "trusted_ca_length"-variabeln för att avspegla certifikatets faktiska längd.

Du behöver också nätverks driv rutinen för maskin varan (Ersätt "nx_driver_xx"-parametern i nx_ip_create-anrop).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;
ULONG server_ipv4_address;

    /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

   /* Ensure the IP instance has been initialized.  */
   status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

**Figur 1,1 exempel på NetX säker användning med NetX**

## <a name="small-example-system-tls-web-server"></a>Litet exempel system (TLS-webbserver)

Ett exempel på hur enkelt det är att använda NetX Secure beskrivs i bild 1,1, som visas nedan och visar en enkel TLS-webbserver (HTTPS).

Observera att du behöver ett X. 509-certifikat för att identifiera servern för TLS-klienter för att kunna köra det här exemplet. För de flesta webb browers är ett enkelt självsignerat certifikat tillräckligt. Din webbläsare kommer klaga över att inte kunna autentisera servern och i vissa fall kan det hända att det inte går att upprätta en TLS/HTTPS-anslutning till Server<sup>3</sup>. Du måste fylla i matrisen "certificate_data" med en DER-kodad binär version av Server certifikatet och uppdatera "certificate_length"-variabeln för att avspegla certifikatets faktiska längd. Du måste också fylla i matrisen "private_key" med en DER-kodad version av certifikatets privata nyckel, formaterad med PKCS # 1 för RSA-nyckel och RFC 5915 för ECC-nycklar. Fyll i variabeln "private_key_length" med den faktiska längden för dina nyckel data.

> [!IMPORTANT]
> Vissa webbläsare (särskilt vissa versioner av Chrome-webbläsaren) kan avvisa självsignerade certifikat. I detta fall kan du skapa en PKI med två nivåer med ett rot certifikat för certifikat utfärdare som används för att signera Server certifikatet. I den här situationen installeras rot certifikat UTFÄRDARens certifikat som ett betrott rot certifikat i webbläsaren. !!! VIKTIGT – ta bort rot certifikat utfärdarens certifikat från webbläsaren när du är färdig och Använd det inte för några produktions program!!!

Du behöver också nätverks driv rutinen för maskin varan (Ersätt "nx_driver_xx"-parametern i nx_ip_create-anrop).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                    (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                    NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

**Figur 1,2 exempel på NetX säker användning med NetX**

## <a name="a-note-on-tls-session-error-recovery"></a>En anteckning om fel återställning av TLS-session

I de exempel system som beskrivs ovan visas de grundläggande prostrecken för en TLS-klient och-Server, men för tydlighetens skull utelämnas fel hanteringen. En del av TLS-TLS är dock beroende av korrekt hantering av fel villkor. I allmänhet hanteras de mest allvarliga möjliga problemen i själva TLS-stacken, men det är viktigt att TLS-programmet svarar korrekt på och återställer från TLS-fel som inte hanteras i TLS-implementeringen.

För att illustrera den nödvändiga logiken för korrekt fel hantering visar följande funktion en typisk samling API-tjänster som kan användas för att hantera TLS-fel och återställa TLS-tillståndet på rätt sätt när ett fel har uppstått. Förutom avsnittet som anges gäller logiken både TLS-klienten och TLS-Server instanser.

Observera att de viktigaste API-anropen i funktionen är till tjänst *nx_secure_tls_session_end*, vilket rensar TLS-sessionen eller hand skakningen, och *nx_secure_tls_session_reset*, vilket rensar TLS-sessionstillståndet så att tls_session kontroll struktur instans kan återanvändas för en ny TLS-session. Observera också att *nx_secure_tls_session_reset* inte tar bort användar konfigurations statusen, till exempel certifikat eller tilldelade buffertar, så att sessionen kan återanvändas utan att anropa *nx_secure_tls_session_create* igen. För att helt rensa alla TLS-sessionstillstånd kan tjänsten *nx_secure_tls_session_delete* användas i stället.

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a>Konfigurations alternativ

Det finns flera konfigurations alternativ för att skapa NetX säkra. Följande är en lista över alla alternativ, där var och en beskrivs i detalj:

| Definierar | Innebörd |
|----------------------|------------------------------------------------|
| **NX_SECURE_DISABLE_ERROR_CHECKING**                | Definierad tar det här alternativet bort den grundläggande NetX-säkra fel kontrollen. Den används vanligt vis när programmet har felsökts. |
| **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**                  | Det här alternativet ger den maximala RSA-modulen förväntat i bitar. Standardvärdet är 4096 för en 4096-bitars Modulus. Andra värden kan vara 3072, 2048 eller 1024 (rekommenderas inte). |
| **NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**        | Det här alternativet tillåter TLS att acceptera självsignerade certifikat från en fjärran sluten värd. Som standard kommer TLS att avvisa självsignerade Server certifikat som en säkerhets åtgärd. Om det här makrot är definierat måste självsignerade certifikat fortfarande läggas till i det betrodda arkivet för att godkännas. |
| **NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**      | Definierad aktiverar det här alternativet de valfria klient certifikat verifieringen X. 509 för TLS-servrar<sup>4</sup>.  |
| **NX_SECURE_ENABLE_PSK_CIPHERSUITES**               | Det här alternativet aktiverar funktionen i förväg delad nyckel (PSK). De inaktiverar inte digitala certifikat. |
| **NX_SECURE_TLS_CLIENT_DISABLED**                   | Definierad tar det här alternativet bort TLS-stacken som är relaterad till TLS-klient läge, vilket minskar kod och data användning. |
| **NX_SECURE_TLS_SERVER_DISABLED**                   | Definierad tar det här alternativet bort alla TLS-stackar som är relaterade till TLS-server läge, vilket minskar kod och data användning.  |
| **NX_SECURE_DISABLE_ECC_CIPHERSUITE**               | Definierad tar det här alternativet bort all TLS-logik för krypteringssviter (Elliptic Curve Cryptography). Dessa krypteringssviter är valfria i TLS 1,2 och tidigare och om du inaktiverar dem kan det leda till betydande kod och minskad data storlek.|
| **NX_SECURE_TLS_ENABLE_TLS_1_3**                    | Definierad, det här alternativet aktiverar TLSv 1.3-läge. TLS 1,3 är den senaste versionen av TLS och är inaktive rad som standard. |
| **NX_SECURE_TLS_ENABLE_TLS_1_0**                    | Definierad, det här alternativet aktiverar det äldre TLSv 1.0-läget. TLSv 1.0 anses vara föråldrat, så det bör bara aktive ras för bakåtkompatibilitet med äldre program. |
| **NX_SECURE_TLS_ENABLE_TLS_1_1**                    | Definierad, det här alternativet aktiverar det äldre TLSv 1.1-läget. TLSv 1.1 anses vara föråldrad, så det bör bara aktive ras för bakåtkompatibilitet med äldre program. |
| **NX_SECURE_TLS_DISABLE_TLS_1_1**                   | Definierad inaktiverar det här alternativet TLSv 1.1-läge. Den definieras som standard. TLSv 1.1 har inaktiverats för att endast använda den säkrare TLSv 1.2<sup>5</sup>.  |
| **NX_SECURE_X509_STRICT_NAME_COMPARE**              | Det här alternativet möjliggör en strikt unikt namn jämförelse för X. 509-certifikat för certifikats ökning och verifiering. Standardvärdet är att jämföra de gemensamma namn fälten med unika namn.|
| **NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES** | Definierat aktiverar det valfria fältet X. 509-unika namn vid kostnaden för extra minnes användning för X. 509-certifikat. |

4. Observera att det här alternativet endast gör det möjligt att länka koden till programmet. Funktionen måste vara aktive rad med API-tjänsten nx_secure_tls_session_client_verify_enable eller konfigureras med nx_secure_tls_session_x509_client_verify_configure för att kunna använda verifiering av klient certifikat.

5. Observera att det också är möjligt att inaktivera TLSv 1.2 om du endast använder TLS 1,0 eller TLS 1,1. Detta rekommenderas dock inte och stöds inte direkt.
