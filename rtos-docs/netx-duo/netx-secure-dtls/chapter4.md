---
title: Kapitel 4 – Beskrivning av Azure RTOS NetX Secure DTLS-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Secure DTLS-tjänster som anges i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 45966e7c8ea9be18bf294e8a7540e7226e803f29ae4f3ad3faaa29e4939c2ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801858"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>Kapitel 4: Beskrivning av Azure RTOS NetX Secure DTLS-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Secure DTLS-tjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas värden i **BOLD** inte av **NX_SECURE_DISABLE_ERROR_CHECKING-makrot** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- [nx_secure_dtls_client_session_start](#nx_secure_dtls_client_session_start)
- [nx_secure_dtls_packet_allocate](#nx_secure_dtls_packet_allocate)
- [nx_secure_dtls_psk_add](#nx_secure_dtls_psk_add)
- [nx_secure_dtls_server_create](#nx_secure_dtls_server_create)
- [nx_secure_dtls_server_delete](#nx_secure_dtls_server_delete)
- [nx_secure_dtls_server_local_certificate_add](#nx_secure_dtls_server_local_certificate_add)
- [nx_secure_dtls_server_local_certificate_remove](#nx_secure_dtls_server_local_certificate_remove)
- [nx_secure_dtls_server_notify_set](#nx_secure_dtls_server_notify_set)
- [nx_secure_dtls_server_psk_add](#nx_secure_dtls_server_psk_add)
- [nx_secure_dtls_server_session_send](#nx_secure_dtls_server_session_send)
- [nx_secure_dtls_server_session_start](#nx_secure_dtls_server_session_start)
- [nx_secure_dtls_server_start](#nx_secure_dtls_server_start)
- [nx_secure_dtls_server_stop](#nx_secure_dtls_server_stop)
- [nx_secure_dtls_server_trusted_certificate_add](#nx_secure_dtls_server_trusted_certificate_add)
- [nx_secure_dtls_server_trusted_certificate_remove](#nx_secure_dtls_server_trusted_certificate_remove)
- [nx_secure_dtls_server_x509_client_verify_configure](#nx_secure_dtls_server_x509_client_verify_configure)
- [nx_secure_dtls_server_x509_client_verify_disable](#nx_secure_dtls_server_x509_client_verify_disable)
- [nx_secure_dtls_session_client_info_get](#nx_secure_dtls_session_client_info_get)
- [nx_secure_dtls_session_create](#nx_secure_dtls_session_create)
- [nx_secure_dtls_session_delete](#nx_secure_dtls_session_delete)
- [nx_secure_dtls_session_end](#nx_secure_dtls_session_end)
- [nx_secure_dtls_session_local_certificate_add](#nx_secure_dtls_session_local_certificate_add)
- [nx_secure_dtls_session_local_certificate_remove](#nx_secure_dtls_session_local_certificate_remove)
- [nx_secure_dtls_session_receive](#nx_secure_dtls_session_receive)
- [nx_secure_dtls_session_reset](#nx_secure_dtls_session_reset)
- [nx_secure_dtls_ session_send](#nx_secure_dtls_-session_send)
- [nx_secure_dtls_session_trusted_certificate_add](#nx_secure_dtls_session_trusted_certificate_add)
- [nx_secure_dtls_session_trusted_certificate_remove](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a>nx_secure_dtls_client_session_start

Starta en NetX Secure DTLS-klientsession

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Description

Den här tjänsten startar en DTLS-klientsession och ansluter till servern på den angivna IP-adressen och UDP-porten med den angivna UDP-socketen för nätverkskommunikation.

DTLS-sessionskontrollblocket måste initieras innan den här tjänsten anropas med hjälp av nx_secure_dtls_session_create. Dessutom kräver DTLS-klienten att minst ett betrott CA-certifikat har lagts till i sessionen med hjälp nx_secure_dtls_session_trusted_certificate_add eller i förväg delade nycklar har aktiverats och konfigurerats.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS-sessionsstruktur som initierades tidigare.
- **udp_socket** Initierad UDP-socket som ska användas för att upprätta nätverkskommunikation med fjärr-DTLS-servern.
- **ip_address** Pekare till IP-adressstrukturen som innehåller DTLS-fjärrserverns adress.
- **port** Initierad UDP-socket som används för att upprätta nätverkskommunikation med fjärr-DTLS-servern.
- **wait_option** Alternativ för stängning för anslutningsförsök.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tilldelning av certifikat till session.
- **NX_NOT_CONNECTED** (0x38) Det går inte att nå servern på den angivna adressen och porten.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) En mottagen TLS/DTLS-meddelandetyp är felaktig.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Meddelandebearbetningen under TLS-handskakningen misslyckades.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett inkommande meddelande misslyckades med en hash-MAC-kontroll.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka underliggande TCP-socket.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Ett inkommande meddelande hade ett fält med ogiltig längd.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Ett inkommande ChangeCipherSpec-meddelande var felaktigt.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Ett inkommande TLS-certifikat kan inte användas för att identifiera DTLS-fjärrservern.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Chiffer med offentlig nyckel som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Fjärrvärden har inte angett några chiffer som stöds av NetX Secure DTLS-stacken.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget DTLS-meddelande hade en okänd DTLS-version i huvudet.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Ett mottaget DTLS-meddelande hade en känd DTLS-version som inte stöds i rubriken.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) En intern TLS-paketallokering misslyckades.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Fjärrvärden angav ett ogiltigt certifikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Fjärrvärden skickade en avisering som anger ett fel och avslutar TLS-sessionen.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) En post i chiffertabellen hade en NULL-funktionspekare.
- **NX_PTR_ERROR** (0x07) Ogiltig session, socket eller adress pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_session_receive, nx_secure_dtls_session_send,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_packet_allocate"></a>nx_secure_dtls_packet_allocate

Allokera ett paket för en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>Description

Den här tjänsten allokerar NX_PACKET för den angivna aktiva DTLS-sessionen från den angivna NX_PACKET_POOL. Den här tjänsten ska anropas av programmet för att allokera datapaket som ska skickas via en DTLS-anslutning. DTLS-sessionen måste initieras innan den här tjänsten anropas.

Det allokerade paketet initieras korrekt så att DTLS-sidhuvud- och sidfotsdata kan läggas till när paketdata har fyllts i. Beteendet är annars identiskt med *nx_packet_allocate*.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en DTLS-sessionsinstans.
- **pool_ptr** Pekare till NX_PACKET_POOL som paketet ska allokeras från.
- **packet_ptr** Utdata pekare till det nyligen allokerade paketet.
- **wait_option** Indragningsalternativ för paketallokering.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckat paket allokeras.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underliggande paketallokering misslyckades.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna DTLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_session_send, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_end, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

Lägga till en i förväg delad nyckel i en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en I förväg delad nyckel (PSK), dess identitetssträng och ett identitetstips i ett DTLS-sessionskontrollblock. PSK används i stället för ett digitalt certifikat när PSK-chiffer har aktiverats och används.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad DTLS-sessionsinstans.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** Längden på PSK-värdet.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** Längden på PSK-identiteten.
- **tips** En sträng som används för att ange vilken grupp av PSK:er som ska väljas på en TLS-server.
- **hint_length** Längden på tipssträngen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av PSK.
- **NX_PTR_ERROR** (0x07) Ogiltig DTLS-sessionspekare.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Det går inte att lägga till en annan PSK.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

Skapa en Säker NetX DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a>Description

Den här tjänsten skapar en instans av en DTLS-server för att hantera inkommande DTLS-begäranden på en viss UDP-port. Eftersom UDP är tillståndslöst kan DTLS-begäranden från flera klienter komma in på en enda port medan andra DTLS-sessioner är aktiva. Servern behövs därför för att underhålla aktiva sessioner och korrekt dirigera inkommande meddelanden till rätt hanterare.

Parametern ip_ptr pekar på en NX_IP-instans som ska användas för den interna UDP-socket som är associerad med DTLS-servern (och lagras i NX_SECURE_DTLS_SERVER kontrollblocket). IP-instansen och porten används för att definiera UDP-gränssnittet där servern instansieras med nx_secure_dtls_server_start tjänsten.

Sessionsbuffertparametern används för att hålla kontrollblocken för alla möjliga samtidiga DTLS-sessioner för DTLS-servern. Den bör allokeras med en storlek som är en till och med multipel av storleken på NX_SECURE_DTLS_SESSION för kontrollblockstrukturen.

För att beräkna den nödvändiga metadatastorleken kan API-nx_secure_tls_metadata_size_calculate användas.

Parametern packet_reassembly_buffer används av DTLS för att sätta ihop UDP-datagram i en fullständig DTLS-post för dekryptering och bör vara tillräckligt stor för att hantera den största förväntade DTLS-posten (16 kB är den maximala DTLS-poststorleken, men många program skickar inte så mycket data i en enda post).

Den connect_notify motringning anropas när en ny DTLS-klient ansluter till servern. Det är upp till programmet att sedan starta DTLS-sessionen med hjälp av tjänsten *nx_secure_dtls_server_session_start*. Sessionen kan startas i själva återanropet, men vi rekommenderar att återanropet endast används för att meddela programtråden (eller dedikerad DTLS-tråd som skapats av programmet) om anslutningen eftersom återanropet anropas av IP-tråden som används för att bearbeta all nätverksbearbetning på lägre nivå (t.ex. UDP). Det kan vara så enkelt som att spara DTLS-sessionsparametern (tillhandahålls som en parameter till motringningen) och anropa nx_secure_dtls_server_session_start i den andra tråden. Motringning connect_notify bör normalt returnera NX_SUCCESS.

Den receive_notify motringningsrutinen anropas när en DTLS-post tas emot som matchar en befintlig etablerad DTLS-session (fjärrvärdens IP-adress och port används för att identifiera en befintlig session). Detta representerar de "programdata" som krypteras och skickas via DTLS. Programmet måste anropa tjänst-nx_secure_dtls_session_receive *den angivna* DTLS-sessionen för att hämta mottagna data. Precis som connect_receive motringning rekommenderar vi att sessionen skickas till en annan tråd för att hantera meddelandebearbetningen eftersom motringningen anropas från IP-tråden. Motringning receive_notify bör normalt returnera NX_SUCCESS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **ip_ptr** Pekare till en initierad NX_IP som ska användas som nätverksgränssnitt för DTLS-servern.
- **port** Den lokala UDP-porten som DTLS-serverns UDP-socket är bunden till.
- **tidsgräns** Tidsgränsvärde som ska användas för nätverksåtgärder.
- **session_buffer** Buffertutrymme som ska innehålla kontrollblock för alla instanser av NX_SECURE_DTLS_SESSION tilldelas till den här DTLS-serverinstansen.
- **session_buffer_size** Sessionsbuffertens storlek. Detta avgör antalet DTLS-sessioner som tilldelats till DTLS-servern.
- **crypto_table** Pekare till en TLS/DTLS-krypteringstabellstruktur som används för alla kryptografiska åtgärder.
- **crypto_metadata_buffer** Buffertutrymme för beräkningar av kryptografiska uppgifter och tillståndsinformation.
- **crypto_metadata_size** Storlek på metadatabuffert.
- **packet_reassembly_buffer** Buffert som används av DTLS för att sätta ihop UDP-data i DTLS-poster för dekryptering.
- **packet_reassembly_buffer_size** Storlek på återmonterad buffert. Bör vanligtvis vara större än 16 kB, men kan vara mindre beroende på program.
- **connect_notify** Motringningsrutin anropas när en DTLS-fjärrklient försöker ansluta till den här DTLS-servern.
- **receive_notify** Återanrop anropas när programdata tas emot via en befintlig DTLS-session.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DTLS-servern har skapats.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0x4D) Det finns inte tillräckligt med buffertutrymme för sessioner, paket som återmonteras eller kryptografi.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

Frigöra resurser som används av en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten frigör de resurser som allokerats till en DTLS-serverinstans, inklusive den interna UDP-socketen som används av servern.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_STILL_BOUND** (0x42) UDP-socketen är fortfarande bunden.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

Lägga till ett lokalt serveridentitetscertifikat till en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten lägger till ett lokalt serveridentitetscertifikat till en DTLS-serverinstans. Minst ett identitetscertifikat krävs för att klienter ska kunna ansluta till en DTLS-server om inte en alternativ autentiseringsmekanism (t.ex. i förväg delade nycklar) används.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas om det finns flera identitetscertifikat med samma X.509-eget namn i DTLS-serverarkivet. Mer information om X.509-servercertifikat finns i användarhandboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **certifikat** Pekare till en tidigare initierad X.509-certifikatstruktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ett lyckat tillägg av certifikat till DTLS-servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0x4D) Ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

*Se referens för *nx_secure_dtls_server_create* för ett mer komplett exempel.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

Ta bort ett lokalt serveridentitetscertifikat från en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten tar bort ett lokalt serveridentitetscertifikat från en DTLS-serverinstans. Minst ett identitetscertifikat krävs för att klienter ska kunna ansluta till en DTLS-server, såvida inte en alternativ autentiseringsmetod (t.ex. i förväg delade nycklar) används.

Certifikatet som ska tas bort kan antingen identifieras med dess X.509-eget namn eller av det numeriska cert_id som tilldelades i anropet *till nx_secure_dtls_server_local_certificate_add*. Den cert_id används bara för att identifiera certifikatet och underhålls av programmet. Om eget namn används i stället för den numeriska certifikatidentifieraren ska cert_id parametern anges till 0.

> [!NOTE]
> Att ta bort ett certifikat medan en DTLS-handskakning bearbetas resulterar i oväntat beteende. Tjänstens *nx_secure_dtls_server_stop* anropas innan certifikat tas bort.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **common_name** X.509 CommonName för det certifikat som ska tas bort. Om detta används skickar du cert_id som noll.
- **common_name_length** Längden på common_name i byte.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern. Om detta används skickar du NX_NULL för den common_name parametern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av certifikat från DTLS-servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Inget certifikat som matchar cert_id eller common_name hittades på den angivna DTLS-servern.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

Tilldela valfria rutiner för återanrop av meddelanden till en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a>Description

Den här tjänsten kan användas för att lägga till valfria rutiner för återanrop av meddelanden till en DTLS-server. Någon av återanropsparametern kan skickas som NX_NULL om bara ett återanrop önskas.

Återanropet disconnect_notify anropas när en fjärrklient avslutar en DTLS-session. Parametern dtls_session är den sessionsinstans som stängdes. Motringning bör vanligtvis returnera NX_SUCCESS.

Motringningen error_notify anropas när ett DTLS-fel eller en timeout inträffar. Parametern dtls_session är sessionsinstansen där felet inträffade och error_code är den numeriska statuskoden för det fel som orsakade problemet (se bilaga A)

NetX Secure Return/Error Codes för en lista över felkoder som kan returneras). Motringning bör vanligtvis returnera NX_SUCCESS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **disconnect_notify** Återanropsrutinen anropas när en fjärrklientvärd stänger en DTLS-session.
- **error_notify** Återanropsrutinen anropas när DTLS påträffar ett fel eller en tidsgräns.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tilldelning av återanropsrutiner.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

Lägga till en i förväg delad nyckel till en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>Description

Den här tjänsten lägger till en I förväg delad nyckel (PSK), dess identitetssträng och en identitetstips till ett DTLS-serverkontrollblock. PSK används i stället för ett digitalt certifikat när PSK-chiffer har aktiverats och används.

Den PSK som läggs till replikeras över alla DTLS-sessioner som tilldelats till DTLS-servern (via sessionsbufferten som anges i anropet till nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** Längden på PSK-värdet.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** Längden på PSK-identiteten.
- **tips** En sträng som används för att ange vilken grupp av PSK:er som ska väljas på en TLS-server.
- **hint_length** Längden på tipssträngen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad addition av PSK.
- **NX_PTR_ERROR** (0x07) Ogiltig DTLS-serverpekare.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Det går inte att lägga till ytterligare en PSK.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_psk_add, nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

Skicka data via en DTLS-session som upprättats med en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Description

Den här tjänsten skickar ett datapaket via en etablerad DTLS-serversession till en fjärr-DTLS-klientvärd. Den session som används hämtas i den receive_notify motringning som tillhandahålls för nx_secure_dtls_session_create.

Data som anges i paketet, som måste allokeras med *hjälp av nx_secure_dtls_packet_allocate*, krypteras med kryptografiska parametrar och rutiner för DTLS-sessionen och skickas sedan till fjärrvärden via DTLS-serverns interna UDP-port till den anslutna klientens IP-adress och port (lagras i DTLS-sessionen).

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en DTLS-sessionsinstans som hämtas från receive_notify motringning som tillhandahålls av programmet.
- **packet_ptr** Pekare till en NX_PACKET-instans som allokerats tidigare och fyllts med programdata.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DTLS-servern har skapats.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Ett fel inträffade i den underliggande UDP-skicka-åtgärden.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,
- nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

Starta en DTLS-session från en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Description

Den här tjänsten startar en DTLS-serversession genom att utföra DTLS-handskakningen på serversidan när en DTLS-fjärrklient har anslutit till servern och begärt en DTLS-anslutning.

DTLS-sessionen hämtas i den connect_notify motringning som tillhandahålls för nx_secure_dtls_server_create.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en DTLS-sessionsinstans som hämtas från en DTLS-server connect_notify återanrop.
- **wait_option** ThreadX-väntevärde som ska användas för nätverksåtgärder.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DTLS-servern har skapats.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att allokera ett DTLS-handskakningspaket (paketpool tom).
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) Avlägsa data som inte var en giltig DTLS-post.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) En DTLS-post kunde inte hashas korrekt (krypteringsfel).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Det gick inte att utfyllnadskontrollen för kryptering.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Tog bort en avisering från fjärrvärden under DTLS-handskakningen.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Tog emot ett okänt meddelande under DTLS-handskakningen.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) tog bort en DTLS-post med en ogiltig längd.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) tog emot en ClientHello utan DTLS-chiffer som stöds.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) avlägset en ClientHello med en okänd komprimeringsmetod.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Allmänt (ospecificerat) handskakningsfel, vanligtvis på grund av problem med tilläggsbearbetning.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) En funktion som ännu inte stöds anropades under DTLS-handskakningen.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Ett okänt chiffer påträffades (indikerade ett internt kryptografifel).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) tog bort en DTLS-post med en felmatchad DTLS-version.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Det gick inte att verifiera DTLS-handskakningshashar, sessionen är ogiltig.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka intern UDP.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

Starta en NetX Secure DTLS-serverinstans som lyssnar på den konfigurerade UDP-porten

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Description

Den här tjänsten startar en DTLS-server. När anropet returneras är servern aktiv och börjar bearbeta inkommande begäranden från DTLS-klienter. Serverinstansen måste ha konfigurerats med tjänsten *nx_secure_dtls_server_create*.

> [!NOTE]
> Den här tjänsten binder den interna DTLS-serverns UDP-port till den konfigurerade lokala porten, så de flesta problem som uppstår har att göra med UDP-kommunikation och nätverkskonfiguration.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad start av servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **UDP NX_NOT_ENABLED** (0x14) inte aktiverat.
- **NX_NO_FREE_PORTS** (0x45) Inga tillgängliga UDP-portar.
- **NX_INVALID_PORT** (0x46) Ogiltig UDP-port.
- **NX_ALREADY_BOUND** (0x22) UDP-port som redan är bunden.
- **UDP NX_PORT_UNAVAILABLE porten** (0x23) är inte tillgänglig för användning.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_stop, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

Stoppa en aktiv NetX Secure DTLS-serverinstans

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar en DTLS-server från att lyssna på den konfigurerade UDP-porten och återställer alla associerade DTLS-sessioner, vilket stoppar pågående DTLS-kommunikation.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en aktiv DTLS-serverinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckat stopp av servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

Lägga till ett betrott certifikatutfärdarcertifikat till en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten lägger till ett betrott ca- eller mellanliggande CA-certifikat till en DTLS-serverinstans och tilldelas till alla interna DTLS-serversessioner. Detta är endast nödvändigt om autentisering med X.509-klientcertifikat har aktiverats med *hjälp av nx_secure_dtls_server_x509_client_verify_configure*. Det tillagda certifikatet används för att verifiera inkommande X.509-klientcertifikat.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas om det finns flera identitetscertifikat med samma X.509-eget namn i DTLS-serverarkivet. Mer information om X.509-servercertifikat finns i användarhandboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **certifikat** Pekare till en tidigare initierad X.509-certifikatstruktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat till DTLS-servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0x4D) Ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

*Se referens för *nx_secure_dtls_server_create* för ett mer komplett exempel.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_server_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

Ta bort ett certifikat för betrodd certifikatutfärdare från en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten tar bort ett certifikat från en DTLS-serverinstans. Betrodda CA-certifikat krävs endast för en DTLS-server där X.509-klientcertifikatverifiering har aktiverats genom att *anropa nx_secure_dtls_server_x509_client_verify_configure*.

Certifikatet som ska tas bort kan antingen identifieras med dess X.509-eget namn eller med det numeriska cert_id som tilldelades i anropet *till nx_secure_dtls_server_trusted_certificate_add*. Den cert_id används bara för att identifiera certifikatet och underhålls av programmet. Om eget namn används i stället för den numeriska certifikatidentifieraren ska cert_id vara inställd på 0.

> [!NOTE]
> Att ta bort ett certifikat medan en DTLS-handskakning bearbetas kan resultera i oväntat beteende. Tjänstens *nx_secure_dtls_server_stop anropas* innan certifikat tas bort.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **common_name** X.509 CommonName för det certifikat som ska tas bort. Om detta används skickar du cert_id noll.
- **common_name_length** Längden på common_name sträng i byte.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern. Om detta används skickar du NX_NULL för common_name parametern.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av certifikat från DTLS-servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Inget certifikat som matchar cert_id eller common_name hittades på den angivna DTLS-servern.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

Konfigurera en NetX Secure DTLS-server för att begära och verifiera klientcertifikat

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Description

Den här tjänsten konfigurerar en DTLS-server för att begära och verifiera DTLS-klientcertifikat. Den här valfria funktionen används när X.509-certifikat önskas för klientautentisering i stället för andra mekanismer (t.ex. en i förväg delad nyckel).

> [!IMPORTANT]
> *När en DTLS-server har konfigurerats för att verifiera klientcertifikat med den här tjänsten måste minst ett betrott CA-certifikat läggas till på servern med hjälp av nx_secure_dtls_server_trusted_certificate_add. Annars avvisar servern alla inkommande klientanslutningar eftersom den inte kan verifiera klientcertifikat mot det betrodda arkivet.*

När den här tjänsten anropas begär DTLS-serverinstansen (när den startats) klientcertifikat som en del av DTLS-handskakningen. Förutsatt att klienten är korrekt konfigurerad med ett identitetscertifikat (och associerad certifikatkedja i förekommande fall), kräver DTLS-servern att minne allokeras för att bearbeta klientcertifikatdata. Det här minnet skickas som *certs_buffer* parametern.

Den certs_buffer måste anpassas efter den största förväntade certifikatkedjan från en DTLS-klient, gånger antalet *DTLS-serversessioner.* Bufferten delas mellan de tillgängliga sessionerna med *hjälp certs_per_session* parametern som representerar det maximala förväntade antalet certifikat i en klientcertifikatkedja. Bufferten måste också ge utrymme för NX_SECURE_X509_CERT datastruktur som används för att parsa certifikatdata.

Du kan beräkna rätt buffertstorlek med följande formel:

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- Antalet DTLS-sessioner bestäms av storleken på sessionsbufferten som skickas till nx_secure_dtls_server_create.
- certs_per_session ska ställas in på det maximala förväntade antalet certifikat i en klientcertifikatkedja.
- Den maximala förväntade certifikatstorleken beror på programmet, nyckelstorlekarna och andra faktorer, men 2 kB är vanligtvis tillräckligt.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **certs_per_session** Antal certifikat som ska allokeras till varje DTLS-serversession.
- **certs_buffer** Buffertutrymme för inkommande certifikatdata.
- **buffer_size** Certifikatbuffertens storlek.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad konfiguration av X.509-klientverifiering.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0x4D) Ogiltigt certifikatarkiv (DTLSserverinstansen är inte initaliserad?).

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_x509_client_verify_disable,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

Inaktiverar X.509-klientcertifikatverifiering för en NetX Secure DTLS-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar verifiering av X.509-klientcertifikat på en DTLS-server. Tjänsten har ingen effekt om verifiering av X.509-klientcertifikat inte har aktiverats.

> [!NOTE]
> Om du inaktiverar klientautentisering på en aktiv DTLS-serverinstans kan det leda till oförutsägbart beteende. Tjänsten nx_secure_dtls_server_stop anropas innan du ändrar servertillståndet.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad inaktivering av X.509-klientautentisering.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_x509_client_verify_configure,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

Hämta fjärrklientinformation från en DTLS-serversession

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Description

Den här tjänsten returnerar nätverksinformation om en DTLS-klient som är ansluten till en viss DTLS-serversession. Informationen som returneras består av fjärrklientens IP-adress och UDP-port, samt den lokala serverporten som klienten är ansluten till.

I allmänhet är DTLS-sessionsinstansen den som erhålls vid anropet av en av rutinerna för återanrop av DTLS-meddelanden (t.ex. de connect_notify- eller receive_notify-återanrop som skickas till nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en aktiv DTLS-serversessionsinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av servern.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_INVALID_SOCKET** (0x13) Den associerade UDP-socketen är inte giltig (sessionen initieras inte?).
- **NX_NOT_CONNECTED** (0x38) UDP-socketen är inte ansluten – klientanslutningen har tagits bort eller har ännu inte upprättats.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_server_start, nx_secure_dtls_server_stop,
- nx_secure_dtls_server_create, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_session_create"></a>nx_secure_dtls_session_create

Skapa och konfigurera en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a>Description

Den här tjänsten skapar och konfigurerar en DTLS-session. I allmänhet används detta för att skapa DTLS-klientsessioner eftersom DTLS-serversessioner hanteras med DTLS-servermekanismen (se *nx_secure_dtls_server_create*), men det kan finnas instanser där ett program behöver skapa en enda fristående DTLS-serversessionsinstans, i vilket fall den här tjänsten kan användas <sup>7.</sup>

Parametrarna konfigurerar den information och minnesallokering som behövs för att instansiera en DTLS-session. Parametern crypto_table TLS-tabell som innehåller alla kryptografiska rutiner som behövs för TLS/DTLS-kryptering och autentisering. Den metadata_buffer används för krypterings-caclulationer (se nx_secure_tls_metadata_size_calculate i användarhandboken för NetX Secure TLS) och packet_reassembly_buffer används för att sätta ihop UDP-datagram till en fullständig DTLS-post för dekryptering.

Den certs_number och remote_certificate_buffer krävs för DTLS-klienter som behöver utrymme för att lagra och bearbeta den inkommande DTLS-servercertifikatkedjan. Bufferten måste kunna hantera den maximala förväntade storleken på certifikatkedjan för alla servrar som den ska ansluta till. Bufferten delas upp med antalet förväntade certifikat (certs_number parameter) och måste också vara tillräckligt stor för att innehålla en NX_SECURE_X509_CERT struktur per certifikat. Buffertstorleken kan fastställas med hjälp av följande formel:

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number är det förväntade maximala antalet certifikat i serverns certifikatkedja
- Den maximala certifikatstorleken beror på storleken på nycklarna som används och informationen i certifikatet, men 2 kB är vanligtvis tillräckligt.

**7** Att skapa DTLS-serversessioner med den här rutinen rekommenderas inte och levereras med vissa begränsningar. Det primära problemet är att sessionen inte hanterar ytterligare klientanslutningar på ett smidigt sätt – eftersom UDP är anslutningslös kan en andra klient juridiskt skicka data till serverns UDP-port när en tidigare DTLS-session fortfarande är aktiv, vilket skulle leda till att serversessionen avslutas med ett fel.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en oiniterad DTLS-sessionsstruktur.
- **crypto_table** Pekare till en TLS/DTLS-krypteringstabellstruktur som används för alla kryptografiska åtgärder.
- **crypto_metadata_buffer** Buffertutrymme för beräkningar av kryptografiska uppgifter och tillståndsinformation.
- **crypto_metadata_size** Storlek på metadatabuffert.
- **packet_reassembly_buffer** Buffert som används av DTLS för att sätta ihop UDP-data i DTLS-poster för dekryptering.
- **packet_reassembly_buffer_size** Storlek på återmonterad buffert. Bör vanligtvis vara större än 16 kB, men kan vara mindre beroende på program.
- **certs_number** Maximalt förväntat antal certifikat i fjärrserverns certifikatkedja.
- **remote_certificate_buffer** Buffertutrymme för inkommande certifikatdata.
- **remote_certificate_buffer_size** Certifikatbuffertens storlek.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Session har skapats.
- **NX_PTR_ERROR** (0x07) Ogiltig session eller buffertpekare.
- **NX_INVALID_PARAMETERS** (0x4D) Det finns inte tillräckligt med buffertutrymme för paket som återmonteras, certifikat eller kryptografi.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

Frigöra resurser som används av en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Description

Den här tjänsten tar bort en DTLS-session och frigör alla resurser som allokerades när den skapades.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS-sessionsstruktur som initierades tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av sessionen.
- **NX_PTR_ERROR** (0x07) Ogiltig session eller buffertpekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

Stänga av en aktiv NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Description

Den här tjänsten avslutar en aktiv DTLS-session genom att skicka en TLS/DTLS CloseNotify-avisering till fjärrvärden. IP-adressen och porten som används är de som användes i föregående anrop till nx_secure_dtls_session_send.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS-sessionsstruktur som initierades tidigare.
- **wait_option** ThreadX-väntevärde som ska användas för nätverksåtgärder.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av sessionen.
- **NX_PTR_ERROR** (0x07) Ogiltig session eller buffertpekare.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att allokera paket för CloseNotify-aviseringen.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Sannolikt internt fel – kryptografirutin känns inte igen.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka underliggande UDP.
- **NX_IP_ADDRESS_ERROR** (0x21) Fel med fjärrvärds-IP-adress.
- **NX_NOT_BOUND** (0x24) Underliggande UDP-socket som inte är bunden till porten.
- **NX_INVALID_PORT** (0x46) Ogiltig UDP-port.
- **UDP NX_PORT_UNAVAILABLE porten** (0x23) är inte tillgänglig för användning.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

Lägga till ett lokalt identitetscertifikat i en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten lägger till ett lokalt identitetscertifikat till en DTLS-sessionsinstans. I allmänhet används den här tjänsten när en DTLS-klientsession måste tillhandahålla ett identitetscertifikat till en fjärrservervärd. Detta är en valfri konfiguration för DTLS, så ett certifikat krävs vanligtvis inte för DTLS-klienter. Ett identitetscertifikat kräver en associerad privat nyckel.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas om det finns flera identitetscertifikat med samma X.509-eget namn i DTLS-certifikatarkivet. Mer information om X.509-certifikat finns i användarhandboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad DTLS-sessionsinstans.
- **certifikat** Pekare till en tidigare initierad X.509-certifikatstruktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat till DTLS-session.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0x4D) Ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

*Se referens för *nx_secure_dtls_session_create* för ett mer komplett exempel.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

Ta bort ett lokalt identitetscertifikat från en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten tar bort ett lokalt identitetscertifikat från en DTLS-sessionsinstans med hjälp av antingen ett certifikat-ID-nummer (tilldelades när certifikatet lades till med nx_secure_dtls_session_local_certificate_add) eller fältet X.509 CommonName.

Om common_name används för att matcha certifikatet ska cert_id parametern anges till 0. Om cert_id används ska common_name skickas ett värde på NX_NULL.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas om det finns flera identitetscertifikat med samma X.509-eget namn i DTLS-certifikatarkivet. Mer information om X.509-certifikat finns i användarhandboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad DTLS-sessionsinstans.
- **common_name** Pekar på den CommonName-sträng som ska matchas.
- **common_name_length** Längden på common_name strängen.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av certifikat från DTLS-sessionen.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Inget certifikat som matchar cert_id eller common_name hittades i den angivna DTLS-sessionen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

*Se referens för *nx_secure_dtls_session_create* för ett mer komplett exempel.

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

Ta emot programdata via en etablerad NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Description

Den här tjänsten returnerar programdata som tas emot av en aktiv DTLS-session. DTLS-sessionen kan vara antingen en DTLS-serversession (som hanteras av en DTLS-serverinstans) eller en DTLS-klientsession. Det returnerade paketet kan bearbetas med någon av NX_PACKET API-tjänsterna (mer information finns i NetX-dokumentationen).

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS-sessionsstruktur som initierades tidigare.
- **packet_ptr_ptr** Pekare till NX_PACKET pekare för returpaketet.
- **wait_option** ThreadX-väntevärde som ska användas för nätverksåtgärder.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad mottagning av programdatapaket.
- **NX_PTR_ERROR** (0x07) Ogiltig session eller paket pekare.
- **UDP NX_NOT_ENABLED** (0x14) är inte aktiverat.
- **NX_NOT_BOUND** (0x24) UDP-socket som inte är bunden till porten.
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) Avlägsa data som inte var en giltig DTLS-post.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) En DTLS-post kunde inte hashas korrekt (krypteringsfel).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Det gick inte att utfyllnadskontrollen för kryptering.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Avlägsa en avisering från fjärrvärden.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Tog emot ett okänt meddelande.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) tog bort en DTLS-post med en ogiltig längd.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Ett okänt chiffer påträffades (anger internt kryptografifel).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) avlägset en DTLS-post med en felmatchad DTLS-version.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

Rensa data i en NetX Secure DTLS-sessionsinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Description

Den här tjänsten återställer en DTLS-session, rensar alla tillfälliga kryptografiska data och tillåter att strukturen används på nytt för en ny session. Beständiga data (t.ex. certifikatarkiv) bevaras så att nx_secure_dtls_session_create inte anropas upprepade gånger.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS-sessionsstruktur som initierades tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad återställning av sessionen.
- **NX_PTR_ERROR** (0x07) Ogiltig session eller buffert pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

Skicka data via en DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>Description

Den här tjänsten skickar ett datapaket via en etablerad DTLS-session till en fjärransluten DTLS-värd på den angivna IP-adressen och porten. Den session som används är en aktiv DTLS-klientsession. Observera att IP-adressen och porten anges på grund av UDP:s tillståndslösa natur, men bör vanligtvis matcha den adress och port som användes för att starta sessionen i nx_secure_dtls_session_start.

De data som anges i paketet, som måste allokeras med *hjälp av nx_secure_dtls_packet_allocate*, krypteras med hjälp av DTLS-sessionens kryptografiska parametrar och rutiner och skickas sedan till fjärrvärden via DTLS-sessionens UDP-socket.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en aktiv DTLS-klientsessionsinstans.
- **packet_ptr** Pekare till en NX_PACKET-instans som allokerats tidigare och fyllts med programdata.
- **ip_address** Pekare till NXD_ADDRESS struktur som innehåller fjärrvärdens IP-adress.
- **port** UDP-port på fjärrvärden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad paketsändning.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Ett fel inträffade i den underliggande UDP-skicka-åtgärden.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

Lägga till ett betrott CA-certifikat i en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten lägger till en betrodd certifikatutfärdare eller mellanliggande CA X.509-certifikat till en DTLS-sessionsinstans. En DTLS-klient kräver minst ett betrott certifikat för att verifiera fjärrservercertifikat om inte en alternativ autentiseringsmekanism används (t.ex. i förväg delade nycklar). Ett betrott certifikat har vanligtvis ingen privat nyckel.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas om det finns flera identitetscertifikat med samma X.509-eget namn i DTLS-certifikatarkivet. Mer information om X.509-certifikat finns i Användarhandbok för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad DTLS-sessionsinstans.
- **certifikat** Pekare till en tidigare initierad X.509-certifikatstruktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat till DTLS-session.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0x4D) Ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

*Se referens för *nx_secure_dtls_session_create* för ett mer komplett exempel.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

Ta bort ett betrott CA-certifikat från en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Description

Den här tjänsten tar bort ett betrott CA-certifikat från en DTLS-sessionsinstans med hjälp av antingen ett certifikat-ID-nummer (tilldelades när certifikatet lades till med nx_secure_dtls_session_trusted_certificate_add) eller fältet X.509 CommonName.

Om common_name används för att matcha certifikatet ska cert_id parametern anges till 0. Om cert_id används ska common_name skickas ett värde på NX_NULL.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas om det finns flera identitetscertifikat med samma X.509-eget namn i DTLS-certifikatarkivet. Mer information om X.509-certifikat finns i Användarhandbok för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad DTLS-sessionsinstans.
- **common_name** Pekare till Den CommonName-sträng som ska matchas.
- **common_name_length** Längden på common_name strängen.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av certifikat från DTLS-sessionen.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Inget certifikat som matchar cert_id eller common_name hittades i den angivna DTLS-sessionen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

*Se referens för *nx_secure_dtls_session_create* för ett mer komplett exempel.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>Se även

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_x509_certificate_initialize
