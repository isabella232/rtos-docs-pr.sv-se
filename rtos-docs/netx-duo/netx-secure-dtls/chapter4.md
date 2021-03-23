---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX Secure DTLS Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-säkra DTLS-tjänster som anges i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825689"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>Kapitel 4: Beskrivning av Azure återställnings tider NetX Secure DTLS Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-säkra DTLS-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "returnera värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_SECURE_DISABLE_ERROR_CHECKING** makro som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

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

Starta en NetX säker DTLS-klientsession

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en DTLS-klientsession som ansluter till servern med den angivna IP-adressen och UDP-porten, med den tillhandahållna UDP-socketen för nätverkskommunikation.

DTLS måste initieras innan den här tjänsten anropas med hjälp av nx_secure_dtls_session_create. Dessutom kräver DTLS-klienten att minst ett certifikat för betrodd certifikat utfärdare har lagts till i sessionen med nx_secure_dtls_session_trusted_certificate_add eller i förväg delade nycklar har Aktiver ATS och kon figurer ATS.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS som initierades tidigare.
- **udp_socket** Initierad UDP-socket som ska användas för att upprätta nätverkskommunikation med den fjärranslutna DTLS-servern.
- **ip_address** Pekare till IP-adress strukturen som innehåller adressen till DTLS-servern.
- **port** Initierad UDP-socket som ska användas för att upprätta nätverkskommunikation med den fjärranslutna DTLS-servern.
- **wait_option** Uppehålls alternativ för anslutnings försök.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har slutfört tilldelningen av certifikat till sessionen.
- **NX_NOT_CONNECTED** (0x38) servern kan inte nås på den adress och port som anges.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) en mottagen TLS/DTLS meddelande typ är felaktig.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) ett chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Det gick inte att bearbeta meddelande bearbetningen under TLS-handskakningen.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett inkommande meddelande misslyckades med en hash Mac-kontroll.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka en underliggande TCP-socket.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) ett inkommande meddelande hade ett ogiltigt längd fält.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) ett inkommande ChangeCipherSpec-meddelande var felaktigt.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0X10C) ett inkommande TLS-certifikat kan inte användas för att identifiera fjärran SLUTen DTLS-servern.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0X10D) den offentliga nyckel chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) fjärrvärden har indikerat Inga krypteringssviter som stöds av stacken netx Secure DTLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett MOTTAGet DTLS-meddelande hade en okänd DTLS-version i huvudet.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) ett MOTTAGet DTLS-meddelande hade en känd men DTLS-version som inte stöds i rubriken.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att tilldela en intern TLS-paket.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) fjärrvärden tillhandahöll ett ogiltigt certifikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) den fjärranslutna värden skickade en avisering som indikerar ett fel och att TLS-sessionen avslutas.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0X13B) en post i ciphersuite-tabellen hade en funktion pekare till null.
- **NX_PTR_ERROR** (0X07) ogiltig session, socket eller adress pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_session_receive nx_secure_dtls_session_send,
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

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar en NX_PACKET för den angivna aktiva DTLS-sessionen från den angivna NX_PACKET_POOL. Den här tjänsten ska anropas av programmet för att allokera data paket som ska skickas via en DTLS-anslutning. DTLS-sessionen måste initieras innan den här tjänsten anropas.

Det allokerade paketet initieras korrekt så att DTLS huvud-och sid fots data kan läggas till efter att paket data har fyllts i. Beteendet är annars identiskt med *nx_packet_allocate*.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en DTLS.
- **pool_ptr** Pekar till en NX_PACKET_POOL som paketet ska allokeras från.
- **packet_ptr** Utmatnings pekare till det nyligen allokerade paketet.
- **wait_option** Uppehålls alternativ för paket tilldelning.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket tilldelningen lyckades.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) den underliggande paket tilldelningen misslyckades.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna DTLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_x509_certificate_initialize nx_secure_dtls_session_create,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_session_send nx_secure_dtls_session_receive,
- nx_secure_dtls_session_end nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

Lägga till en i förväg delad nyckel till en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett DTLS. PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekar till en tidigare skapad DTLS-session.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** PSK-värdets längd.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** PSK-identitetens längd.
- **tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.
- **hint_length** Längden på tips strängen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av PSK lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig DTLS.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_psk_add nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

Skapa en säker DTLS-Server för NetX

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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en instans av en DTLS-Server för att hantera inkommande DTLS-begäranden på en viss UDP-port. På grund av det faktum att UDP är tillstånds löst kan DTLS-begäranden från flera klienter komma in på en enda port medan andra DTLS-sessioner är aktiva. Därför behövs servern för att underhålla aktiva sessioner och dirigera inkommande meddelanden korrekt till rätt hanterare.

Ip_ptr-parametern pekar på en NX_IP-instans som ska användas för den interna UDP-socket som är associerad med DTLS-servern (och lagras i NX_SECURE_DTLS_SERVER kontroll block). IP-instansen och porten används för att definiera UDP-gränssnittet då servern instansieras med nx_secure_dtls_server_start tjänsten.

Parametern session buffer används för att hålla kontroll blocken för alla möjliga samtidiga DTLS-sessioner för DTLS-servern. Den bör tilldelas en storlek som är jämnt delbar med storleken på den NX_SECURE_DTLS_SESSION kontroll block strukturen.

Om du vill beräkna nödvändig metadata-storlek kan API-nx_secure_tls_metadata_size_calculate användas.

Parametern packet_reassembly_buffer används av DTLS för att ommontera UDP-datagram till en fullständig DTLS-post för dekryptering och bör vara tillräckligt stor för att rymma den största förväntade DTLS-posten (16 KB är den DTLS maximala post storleken, men många program skickar inte samma data i samma post).

Rutinen för connect_notify motringning anropas när en ny DTLS-klient ansluter till servern. Det är upp till programmet att starta DTLS-sessionen med hjälp av tjänsten *nx_secure_dtls_server_session_start*. Även om sessionen kan startas i själva återanropet rekommenderar vi att återanropet endast används för att meddela program tråden (eller dedikerade DTLS-tråden som skapats av programmet) för anslutningen när motringningen anropas av IP-tråden som används för att bearbeta all nätverks bearbetning på lägre nivå (t. ex. UDP). Detta kan vara lika enkelt som att spara DTLS (anges som en parameter till återanropet) och anropa nx_secure_dtls_server_session_start i den andra tråden. Connect_notify motringning bör normalt returnera NX_SUCCESS.

Rutinen för receive_notify motringning anropas när en DTLS-post tas emot som matchar en befintlig upprättad DTLS-session (IP-adress och port för fjärrvärden används för att identifiera en befintlig session). Detta representerar de "program data" som krypteras och skickas via DTLS. Programmet måste anropa tjänsten *nx_secure_dtls_session_receive* på den angivna DTLS-sessionen för att hämta mottagna data. Precis som med connect_receive motringning rekommenderar vi att sessionen skickas till en annan tråd för att hantera meddelande bearbetningen när återanropet anropas från IP-tråden. Receive_notify motringning bör normalt returnera NX_SUCCESS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **ip_ptr** Pekar mot ett initierat NX_IP kontroll block som ska användas som nätverks gränssnitt för DTLS-servern.
- **port** Den lokala UDP-porten som DTLS-serverns UDP-socket är kopplad till.
- **tids gräns** Tids gräns värde som ska användas för nätverks åtgärder.
- **session_buffer** Buffertutrymme som innehåller kontroll block för alla instanser av NX_SECURE_DTLS_SESSION som tilldelats den här DTLS-serverinstansen.
- **session_buffer_size** Storlek på bufferten för session. Detta avgör antalet DTLS-sessioner som tilldelats DTLS-servern.
- **crypto_table** Pekare till en TLS/DTLS krypterings tabell struktur som används för alla kryptografiska åtgärder.
- **crypto_metadata_buffer** Buffertutrymme för kryptografiska åtgärds beräkningar och statusinformation.
- **crypto_metadata_size** Storlek på buffert för metadata.
- **packet_reassembly_buffer** Buffert som används av DTLS för att ommontera UDP-data i DTLS-poster för dekryptering.
- **packet_reassembly_buffer_size** Storlek på omassembly buffer. Bör normalt vara större än 16 KB, men kan vara mindre beroende på program.
- **connect_notify** Callback-rutin som anropas när en fjärran sluten DTLS-klient försöker ansluta till den här DTLS-servern.
- **receive_notify** Motringning anropades när program data tas emot över en befintlig DTLS-session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skapandet av DTLS-servern.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0X4D) det finns inte tillräckligt med buffertutrymme för sessioner, paket omsammansättning eller kryptografi.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

Frigör resurser som används av en säker DTLS-server med NetX

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör de resurser som har allokerats till en DTLS-serverinstans, inklusive den interna UDP-socket som används av servern.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) borttagning av server lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_STILL_BOUND** (0X42) UDP-socket är fortfarande kopplad.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

Lägga till ett lokalt Server identitets certifikat till en säker DTLS-server med NetX

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till ett lokalt Server identitets certifikat till en DTLS-Server instans. Minst ett identitets certifikat krävs för att klienter ska kunna ansluta till en DTLS-Server, om inte en annan autentiseringsmekanism (t. ex. i förväg delade nycklar) används.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i DTLS-serverns arkiv. Mer information om X. 509-servercertifikat finns i användar handboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av certifikat till DTLS-servern har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

* Se referens för *nx_secure_dtls_server_create* ett mer komplett exempel.

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

- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

Ta bort ett lokalt Server identitets certifikat från en NetX säker DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett lokalt Server identitets certifikat från en DTLS-Server instans. Minst ett identitets certifikat krävs för att klienter ska kunna ansluta till en DTLS-Server, om inte en annan autentiseringsmekanism (t. ex. i förväg delade nycklar) används.

Det certifikat som ska tas bort kan identifieras antingen av sitt unika X. 509-namn eller av det numeriska cert_id som tilldelades i anropet till *nx_secure_dtls_server_local_certificate_add*. Cert_id används bara för att identifiera certifikatet och underhålls av programmet. Om det egna namnet används i stället för det numeriska certifikat-ID: n ska parametern cert_id anges till 0.

> [!NOTE]
> Att ta bort ett certifikat medan en DTLS-handskakning bearbetas resulterar i ett oväntat beteende. Tjänst *nx_secure_dtls_server_stop* ska anropas innan certifikat tas bort.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **common_name** X. 509-CommonName för det certifikat som ska tas bort. Om det används skickar cert_id som noll.
- **common_name_length** Längden på common_name sträng i byte.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern. Om detta används kan du skicka NX_NULL för common_name-parametern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-servern har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name på den aktuella DTLS-servern.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

Tilldela en säker NetX DTLS-Server för valfria meddelanden

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

### <a name="description"></a>Beskrivning

Den här tjänsten kan användas för att lägga till valfria rutiner för återuppringning av meddelanden på en DTLS-Server. Antingen kan callback-parametern skickas som NX_NULL om bara ett återanrop önskas.

Disconnect_notify motringning anropas när en fjärrklient avslutar en DTLS-session. Parametern dtls_session är den instans som stängdes. Återanropet bör normalt returnera NX_SUCCESS.

Error_notify motringning anropas när ett DTLS-fel eller en timeout inträffar. Parametern dtls_session är den session som felet inträffat för och error_code är den numeriska status koden för det fel som orsakade problemet (se bilaga A)

NetX Secure Return/Error Codes för en lista över felkoder som kan returneras). Återanropet bör normalt returnera NX_SUCCESS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **disconnect_notify** Callback-rutin som anropas när en fjärran sluten klient värd stänger en DTLS-session.
- **error_notify** Callback-rutin anropas när DTLS påträffar ett fel eller en timeout.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har slutfört tilldelning av återkallnings rutiner.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

Lägga till en i förväg delad nyckel till en NetX säker DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett DTLS Server Control Block. PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.

PSK som läggs till replikeras över alla DTLS-sessioner som tilldelats DTLS-servern (via den session-buffert som anges i anropet till nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** PSK-värdets längd.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** PSK-identitetens längd.
- **tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.
- **hint_length** Längden på tips strängen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av PSK lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig DTLS-Server pekare.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_psk_add nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

Skicka data via en DTLS-session som upprättats med en NetX-säker DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett data paket över en etablerad DTLS-server till en fjärran sluten DTLS-klient värd. Den använda sessionen hämtas i receive_notify callback-rutinen som nx_secure_dtls_session_create.

Data som anges i paketet, som måste allokeras med hjälp av *nx_secure_dtls_packet_allocate*, krypteras med hjälp av DTLS-sessionens kryptografiska parametrar och rutiner och skickas sedan till fjärrvärden via DTLS-serverns interna UDP-port till den anslutna klientens IP-adress och port (lagras i DTLS-sessionen).

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en DTLS-instans som hämtats från den receive_notify återanrops rutinen som tillhandahålls av programmet.
- **packet_ptr** Pekare till en NX_PACKET instans som har allokerats tidigare och fyllts med program data.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skapandet av DTLS-servern.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) ett fel uppstod i den underliggande UDP-åtgärden för att skicka.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive nx_secure_dtls_server_session_create,
- nx_secure_dtls_server_session_start nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

Starta en DTLS-session från en NetX-säker DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en DTLS-Server genom att utföra DTLS-handskakningen på Server sidan när en fjärran sluten DTLS-klient har anslutit till servern och begärt en DTLS-anslutning.

DTLS-sessionen hämtas i connect_notify callback-rutinen som nx_secure_dtls_server_create.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en DTLS-instans som hämtats från en DTLS-Server connect_notify motringning.
- **wait_option** ThreadX vänte värde som ska användas för nätverks åtgärder.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skapandet av DTLS-servern.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0X111) Det gick inte att ALLOKERA ett DTLS-handskaknings paket (Packet bassäng Empty).
- **NX_SECURE_TLS_INVALID_PACKET** (0X104) emot data som inte var giltiga DTLS-poster.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) en DTLS-post kunde inte hashas korrekt (krypterings fel).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) kontroll av krypterings utfyllnad har misslyckats.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) emot en avisering från fjärrvärden under DTLS-handskakningen.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) fick ett okänt meddelande under DTLS-handskakningen.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) emot en DTLS-post med ogiltig längd.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) tog emot en sitt hälsnings som inte har stöd för DTLS krypteringssviter.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118) emot en sitt hälsnings med en okänd komprimerings metod.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0X107) allmänt (ospecificerad) hand skaknings fel, vanligt vis på grund av problem med förlängnings bearbetning.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0X130) en funktion som ännu inte stöds anropades under DTLS-handskakningen.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0X105) en okänd CIPHERSUITE påträffades (angivet internt kryptografi fel).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) emot en DTLS post med en felmatchad DTLS-version.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115) Det gick inte att verifiera DTLS-hand skaknings-hashen, sessionen är ogiltig.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) intern UDP-sändning misslyckades.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_create nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

Starta en NetX säker DTLS-serverinstans som lyssnar på den konfigurerade UDP-porten

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en DTLS-Server. När anropet har returnerats är servern aktiv och kommer att börja bearbeta inkommande begär Anden från DTLS-klienter. Server instansen måste ha kon figurer ATS med tjänsten *nx_secure_dtls_server_create*.

> [!NOTE]
> Den här tjänsten binder den interna DTLS-serverns UDP-port till den konfigurerade lokala porten så att de flesta problem som påträffas kan utföras med UDP-kommunikation och nätverks konfiguration.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) starten av servern har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_NOT_ENABLED** (0X14) UDP är inte aktiverat.
- **NX_NO_FREE_PORTS** (0X45) inga tillgängliga UDP-portar.
- **NX_INVALID_PORT** (0X46) ogiltig UDP-port.
- **NX_ALREADY_BOUND** (0X22) UDP-porten är redan kopplad.
- **NX_PORT_UNAVAILABLE** (0X23) UDP-porten är inte tillgänglig för användning.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_stop nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

Stoppa en aktiv NetX säker DTLS-serverinstans

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar en DTLS-Server från att lyssna på konfigurationen av UDP-porten och återställer alla tillhör ande DTLS-sessioner, vilket stoppar all pågående DTLS kommunikation.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekar mot en aktiv DTLS-serverinstans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har stoppats på servern.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

Lägga till ett certifikat för betrodd certifikat utfärdare på en NetX säker DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en betrodd certifikat utfärdare eller ett mellanliggande CA-certifikat till en DTLS-serverinstans och tilldelas till alla interna DTLS-serversessioner. Detta krävs endast om X. 509-autentisering med klient certifikat är aktiverat med *nx_secure_dtls_server_x509_client_verify_configure*. Det tillagda certifikatet kommer att användas för att verifiera inkommande klient X. 509-certifikat.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i DTLS-serverns arkiv. Mer information om X. 509-servercertifikat finns i användar handboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av certifikat till DTLS-servern har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

* Se referens för *nx_secure_dtls_server_create* ett mer komplett exempel.

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

- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_server_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

Ta bort ett certifikat för betrodd certifikat utfärdare från en NetX säker DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett certifikat för betrodd certifikat utfärdare från en DTLS-Server instans. Certifikat från betrodda certifikat utfärdare krävs bara för en DTLS-server där X. 509-klient certifikat verifiering har Aktiver ATS genom att anropa *nx_secure_dtls_server_x509_client_verify_configure*.

Det certifikat som ska tas bort kan identifieras antingen av sitt unika X. 509-namn eller av det numeriska cert_id som tilldelades i anropet till *nx_secure_dtls_server_trusted_certificate_add*. Cert_id används bara för att identifiera certifikatet och underhålls av programmet. Om det egna namnet används i stället för det numeriska certifikat-ID: n ska parametern cert_id anges till 0.

> [!NOTE]
> Att ta bort ett certifikat medan en DTLS-handskakning bearbetas kan resultera i oväntat beteende. Tjänst *nx_secure_dtls_server_stop* ska anropas innan certifikat tas bort.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **common_name** X. 509-CommonName för det certifikat som ska tas bort. Om det används skickar cert_id som noll.
- **common_name_length** Längden på common_name sträng i byte.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern. Om detta används kan du skicka NX_NULL för common_name-parametern.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-servern har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name på den aktuella DTLS-servern.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

Konfigurera en NetX-säker DTLS-Server för att begära och verifiera klient certifikat

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar en DTLS-Server för att begära och verifiera DTLS klient certifikat. Den här valfria funktionen används när X. 509-certifikat önskas för klientautentisering i stället för andra mekanismer (t. ex. en i förväg delad nyckel).

> [!IMPORTANT]
> *När en DTLS-Server har kon figurer ATS för att verifiera klient certifikat med hjälp av den här tjänsten måste minst ett certifikat för betrodd certifikat utfärdare läggas till på servern med hjälp av nx_secure_dtls_server_trusted_certificate_add eller servern avvisar alla inkommande klient anslutningar eftersom den inte kan verifiera klient certifikat mot det betrodda arkivet.*

Vid anrop av den här tjänsten kommer DTLS Server-instansen (när den har startats) begära klient certifikat som en del av DTLS-handskakningen. Förutsatt att klienten är korrekt konfigurerad med ett identitets certifikat (och tillhör ande certifikat kedja vid behov), kräver DTLS-servern att minnet allokeras för att bearbeta klient certifikat data. Det här minnet skickas in som *certs_buffer* parameter.

Certs_buffer måste anpassas till den största förväntade certifikat kedjan från en DTLS-klient, *gånger antalet DTLS-serversessioner*. Bufferten delas upp bland de tillgängliga sessionerna med hjälp av parametern *certs_per_session* som representerar det maximala förväntade antalet certifikat i en klient certifikat kedja. Bufferten måste också tillhandahålla utrymme för NX_SECURE_X509_CERT data strukturen som används för att parsa certifikat data.

Beräkningen av rätt buffertstorlek kan göras med följande formel:

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- Antalet DTLS-sessioner bestäms av storleken på den session-buffert som skickades till nx_secure_dtls_server_create.
- certs_per_session ska anges till det maximala förväntade antalet certifikat i en klient certifikat kedja.
- Den maximala förväntade certifikat storleken är beroende av programmet, nyckel storlekarna och andra faktorer, men 2KB är vanligt vis tillräckligt.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.
- **certs_per_session** Antal certifikat som ska allokeras till varje DTLS Server-session.
- **certs_buffer** Buffertutrymme för inkommande certifikat data.
- **buffer_size** Storlek på certifikatets buffert.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) konfigurationen av klient verifieringen X. 509.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0X4D) ogiltigt certifikat arkiv (DTLSserver-instans inte initalized?).

### <a name="allowed-from"></a>Tillåten från

Konversation

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
- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

Inaktiverar verifiering av klient-X. 509 för en NetX säker DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar X. 509 klient certifikat verifiering på en DTLS-Server. Tjänsten har ingen funktion om verifieringen av klient certifikatet för X. 509 inte är aktive rad.

> [!NOTE]
> Inaktive ring av klientautentisering på en aktiv DTLS-serverinstans kan leda till oförutsägbara beteenden. Tjänsten nx_secure_dtls_server_stop ska anropas innan Server tillstånd ändras.

### <a name="parameters"></a>Parametrar

- **server_ptr** Pekare till en tidigare skapad DTLS-serverinstans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har inaktiverat autentisering av X. 509-klient.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
- nx_secure_dtls_server_start nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

Hämta information om fjärran sluten klient från en DTLS-Server

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar nätverksinformation om en DTLS-klient som är ansluten till en viss DTLS Server-session. Den information som returneras består av fjärrklientens IP-adress och UDP-port, samt den lokala server port som klienten är ansluten till.

I allmänhet är DTLS session-instansen som erhålls i anropet från en av DTLS för aviseringar om aviseringar (t. ex. connect_notify eller receive_notify återanrop som skickas till nx_secure_dtls_server_create).

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekar mot en aktiv DTLS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) borttagning av server lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_INVALID_SOCKET** (0X13) den associerade UDP-socketen är inte giltig (sessionen initierades inte?).
- **NX_NOT_CONNECTED** (0X38) UDP-socketen är inte ansluten – klient anslutningen har släppts eller ännu inte upprättats.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_server_start nx_secure_dtls_server_stop,
- nx_secure_dtls_server_create nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive nx_secure_dtls_server_session_send,
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

### <a name="description"></a>Beskrivning

Den här tjänsten skapar och konfigurerar en DTLS-session. Detta används vanligt vis för att skapa DTLS-klientsessioner som DTLS-serversessioner hanteras med DTLS-serverns mekanism (se *nx_secure_dtls_server_create*), men det kan finnas instanser där ett program behöver skapa en enda fristående DTLS för Server session, vilket innebär att tjänsten kan användas <sup>7</sup>.

Parametrarna konfigurerar den information och minnes tilldelning som krävs för att instansiera en DTLS-session. Parametern crypto_table är en TLS-tabell som innehåller alla de kryptografiska rutiner som krävs för TLS/DTLS-kryptering och autentisering. Metadata_buffer används för kryptering caclulations (se nx_secure_tls_metadata_size_calculate i användar handboken för NetX Secure TLS) och packet_reassembly_buffer används för att sätta samman UDP-datagram till en fullständig DTLS-post för dekryptering.

Certs_number och remote_certificate_buffer krävs för DTLS-klienter som behöver utrymme för att lagra och bearbeta den inkommande DTLS Server certifikat kedjan. Bufferten måste kunna hantera den maximala förväntade storleken på certifikat kedjan för en server som den ska ansluta till. Bufferten delas upp av antalet förväntade certifikat (certs_number parameter) och måste också vara tillräckligt stor för att rymma en NX_SECURE_X509_CERT struktur per certifikat. Buffertstorleken kan fastställas med hjälp av följande formel:

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number är det förväntade maximala antalet certifikat i serverns certifikat kedja
- Maximal certifikat storlek beror på storleken på de nycklar som används och informationen i certifikatet, men 2KB är allmänt tillräckligt.

**7** det är inte rekommenderat att skapa DTLS-serversessioner med den här rutinen och den innehåller vissa begränsningar. Det primära problemet är att sessionen inte hanterar ytterligare klient anslutningar på ett smidigt sätt eftersom UDP är anslutnings lös en andra klient kan lagligen skicka data till serverns UDP-port när en tidigare DTLS-session fortfarande är aktiv, vilket skulle orsaka att serversessionen avslutas med ett fel.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekar till en oinitierad DTLS-session.
- **crypto_table** Pekare till en TLS/DTLS krypterings tabell struktur som används för alla kryptografiska åtgärder.
- **crypto_metadata_buffer** Buffertutrymme för kryptografiska åtgärds beräkningar och statusinformation.
- **crypto_metadata_size** Storlek på buffert för metadata.
- **packet_reassembly_buffer** Buffert som används av DTLS för att ommontera UDP-data i DTLS-poster för dekryptering.
- **packet_reassembly_buffer_size** Storlek på omassembly buffer. Bör normalt vara större än 16 KB, men kan vara mindre beroende på program.
- **certs_number** Maximalt Förväntat antal certifikat i fjärrserverns certifikat kedja.
- **remote_certificate_buffer** Buffertutrymme för inkommande certifikat data.
- **remote_certificate_buffer_size** Storlek på certifikatets buffert.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skapandet av session.
- **NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.
- **NX_INVALID_PARAMETERS** (0X4D) det finns inte tillräckligt med buffertutrymme för paket omsammansättning, certifikat eller kryptografi.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

Frigör resurser som används av en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en DTLS-session, vilket frigör alla resurser som har allokerats när den skapades.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS som initierades tidigare.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) en borttagning av sessionen har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

Stänga en aktiv NetX säker DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Beskrivning

Den här tjänsten avslutar en aktiv DTLS-session genom att skicka en TLS/DTLS CloseNotify-avisering till fjärrvärden. Den IP-adress och port som används är de som användes i föregående anrop till nx_secure_dtls_session_send.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS som initierades tidigare.
- **wait_option** ThreadX vänte värde som ska användas för nätverks åtgärder.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) en borttagning av sessionen har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0X111) Det gick inte att allokera paket för CloseNotify-avisering.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0X105) troligen internt fel – kryptografisk rutin känns inte igen.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) den underliggande UDP-sändningen misslyckades.
- **NX_IP_ADDRESS_ERROR** -fel (0x21) med en fjärran sluten värd-IP-adress.
- **NX_NOT_BOUND** (0x24) den underliggande UDP-socketen är inte kopplad till porten.
- **NX_INVALID_PORT** (0X46) ogiltig UDP-port.
- **NX_PORT_UNAVAILABLE** (0X23) UDP-porten är inte tillgänglig för användning.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

Lägga till ett lokalt identitets certifikat till en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till ett lokalt identitets certifikat till en DTLS. I allmänhet används den här tjänsten när en DTLS-klientsession måste tillhandahålla ett identitets certifikat till en fjärrserver-värd. Detta är en valfri konfiguration för DTLS, så ett certifikat är inte allmänt nödvändigt för DTLS-klienter. Ett identitets certifikat kräver en associerad privat nyckel.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS. Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekar till en tidigare skapad DTLS-session.
- **certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) det framgångs rika tillägget av certifikat till DTLS-sessionen.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.

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

- nx_secure_dtls_session_create nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

Ta bort ett lokalt identitets certifikat från en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett lokalt identitets certifikat från en DTLS med antingen ett certifikat-ID-nummer (tilldelat när certifikatet lades till med nx_secure_dtls_session_local_certificate_add) eller fältet X. 509 CommonName.

Om common_name används för att matcha certifikatet, ska cert_id-parametern anges till 0. Om cert_id används ska common_name skickas värdet NX_NULL.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS. Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekar till en tidigare skapad DTLS-session.
- **common_name** Pekar på den CommonName-sträng som ska matchas.
- **common_name_length** Längden på common_name strängen.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-sessionen lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name i den aktuella DTLS-sessionen.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.

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

- nx_secure_dtls_session_create nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

Ta emot program data över en etablerad NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar program data som tagits emot av en aktiv DTLS-session. DTLS-sessionen kan vara antingen en DTLS-klientsession (hanteras av en DTLS-serverinstans) eller en DTLS-klientsession. Det returnerade paketet kan bearbetas med hjälp av någon av NX_PACKET API-tjänsterna (se NetX-dokumentationen för mer information).

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS som initierades tidigare.
- **packet_ptr_ptr** Pekar till en NX_PACKET-pekare för det returnerade paketet.
- **wait_option** ThreadX vänte värde som ska användas för nätverks åtgärder.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) mottagning av program data paket.
- **NX_PTR_ERROR** (0X07) ogiltig session eller paket pekare.
- **NX_NOT_ENABLED** (0X14) UDP är inte aktiverat.
- **NX_NOT_BOUND** (0X24) UDP-socketen är inte kopplad till porten.
- **NX_SECURE_TLS_INVALID_PACKET** (0X104) emot data som inte var giltiga DTLS-poster.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) en DTLS-post kunde inte hashas korrekt (krypterings fel).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) kontroll av krypterings utfyllnad har misslyckats.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) emot en avisering från fjärrvärden.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0X102) tog emot ett okänt meddelande.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) emot en DTLS-post med ogiltig längd.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0X105) en okänd CIPHERSUITE påträffades (tyder på ett internt kryptografi fel).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) emot en DTLS post med en felmatchad DTLS-version.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_client_session_start nx_secure_dtls_session_end,
- nx_secure_dtls_session_send nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

Rensa data i en NetX Secure DTLS-session-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Beskrivning

Den här tjänsten återställer en DTLS-session och rensar alla tillfälliga kryptografiska data och gör det möjligt att använda strukturen igen för en ny session. Beständiga data (t. ex. certifikat Arkiv) bevaras så att nx_secure_dtls_session_create inte behöver anropas flera gånger.

### <a name="parameters"></a>Parametrar

- **dtls_session** Pekare till en DTLS som initierades tidigare.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades att återställa sessionen.
- **NX_PTR_ERROR** (0X07) ogiltig sessions-eller buffert pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

Skicka data över en DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett data paket över en etablerad DTLS-session till en fjärran sluten DTLS-värd på den angivna IP-adressen och porten. Sessionen som används är en aktiv DTLS-klientsession. Observera att IP-adressen och porten tillhandahålls på grund av tillstånds lös typ av UDP, men bör vanligt vis matcha adressen och porten som används för att starta sessionen i nx_secure_dtls_session_start.

De data som anges i paketet, som måste allokeras med hjälp av *nx_secure_dtls_packet_allocate*, krypteras med hjälp av DTLS-sessionens kryptografiska parametrar och rutiner och sedan skickas till fjärrvärden över DTLS-SESSIONens UDP-socket.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekar mot en aktiv DTLS-klientsession.
- **packet_ptr** Pekare till en NX_PACKET instans som har allokerats tidigare och fyllts med program data.
- **ip_address** Pekar till en NXD_ADDRESS-struktur som innehåller IP-adressen för fjärrvärden.
- **port** UDP-port på fjärrvärden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket sändningen har skickats.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) ett fel uppstod i den underliggande UDP-åtgärden för att skicka.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

- nx_secure_dtls_client_session_start nx_secure_dtls_session_receive,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

Lägga till ett certifikat för betrodd certifikat utfärdare i en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en betrodd certifikat utfärdare eller ett mellanliggande CA X. 509-certifikat till en DTLS-session. En DTLS-klient kräver minst ett betrott certifikat för att verifiera fjärrservernamn om inte en alternativ autentiseringsmekanism används (t. ex. i förväg delade nycklar). Ett betrott certifikat har vanligt vis ingen privat nyckel.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS. Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekar till en tidigare skapad DTLS-session.
- **certifikat** Pekar till en tidigare initierad X. 509-certifikat struktur.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) det framgångs rika tillägget av certifikat till DTLS-sessionen.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_INVALID_PARAMETERS** (0X4D) ett certifikat-ID på 0 skickades.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.

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

- nx_secure_dtls_session_create nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

Ta bort ett certifikat för betrodd certifikat utfärdare från en NetX Secure DTLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett certifikat för betrodd certifikat utfärdare från en DTLS med antingen ett certifikat-ID-nummer (tilldelat när certifikatet lades till nx_secure_dtls_session_trusted_certificate_add) eller fältet X. 509 CommonName.

Om common_name används för att matcha certifikatet, ska cert_id-parametern anges till 0. Om cert_id används ska common_name skickas värdet NX_NULL.

Parametern cert_id är en numerisk identifierare som inte är noll för certifikatet. Detta gör att certifikatet enkelt kan tas bort eller hittas i händelse av att det finns flera identitets certifikat med samma X. 509-namn som finns i certifikat arkivet DTLS. Mer information om X. 509-certifikat finns i användar handboken för NetX Secure TLS.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekar till en tidigare skapad DTLS-session.
- **common_name** Pekar på den CommonName-sträng som ska matchas.
- **common_name_length** Längden på common_name strängen.
- **cert_id** Numerisk unik identifierare som inte är noll för det här certifikatet på den här DTLS-servern.


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) borttagning av certifikat från DTLS-sessionen lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig pekare skickades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat som matchar cert_id eller common_name i den aktuella DTLS-sessionen.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

* Se referens för *nx_secure_dtls_session_create* ett mer komplett exempel.

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

- nx_secure_dtls_session_create nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_x509_certificate_initialize
