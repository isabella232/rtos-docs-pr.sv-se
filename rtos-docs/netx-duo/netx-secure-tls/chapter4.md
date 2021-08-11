---
title: Kapitel 4 – Beskrivning av Azure RTOS NetX Secure-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Secure-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b10260778f7f5e1a5bd0a38aded2339008b066cca77f2439a5881d28a0489524
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797763"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>Kapitel 4 – Beskrivning av Azure RTOS NetX Secure-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Secure-tjänster (anges nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **NX_SECURE_DISABLE_ERROR_CHECKING-makrot** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - Utföra self_test på krypteringsmetoderna
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - Beräknar hash-värdet med hjälp user_supplied hash-funktion
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - Ange det aktiva identitetscertifikatet för en NetX Secure TLS-session
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - Ange en Pre_Shared för en NetX Secure TLS-klientsession
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - Initierar NetX Secure TLS-modulen]
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - Lägga till ett lokalt certifikat i NetX Secure TLS-session
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - Hitta ett lokalt certifikat i en NetX Secure TLS-session efter eget namn
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - Ta bort lokalt certifikat från NetX Secure TLS-session
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - Beräkna storleken på kryptografiska metadata för en NetX Secure TLS-session
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - Allokera ett paket för en NetX Secure TLS-session
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - Lägga till Pre_Shared nyckel i en NetX Secure TLS-session
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - Allokera utrymme för certifikatet som tillhandahålls av en fjärransluten TLS-värd
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - Allokera utrymme för alla certifikat som tillhandahålls av en fjärransluten TLS-värd
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - Ledigt utrymme allokerat för inkommande certifikat
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - Lägga till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - Hitta ett certifikat med hjälp av en numerisk identifierare
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - Ta bort ett lokalt servercertifikat med hjälp av en numerisk identifierare
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - Konfigurera ett återanrop för TLS som ska användas för ytterligare certifikatverifiering
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-klienthandskakning
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - Aktivera X.509-klientverifiering och allokera utrymme för klientcertifikat
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - Inaktivera klientcertifikatautentisering för en Säker NetX-TLS-session
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - Aktivera klientcertifikatautentisering för en Säker NetX-TLS-session
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - Skapa en NetX Secure TLS-session för säker kommunikation
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - Ta bort en NetX Secure TLS-session
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - Avsluta en aktiv NetX Secure TLS-session
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - Ange paketets återmonteringsbuffert för en Säker NetX-TLS-session
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - Åsidosätt standardversionen av TLS-protokollet för en Säker NetX-TLS-session
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - Ta emot data från en NetX Secure TLS-session
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - Tilldela ett återanrop som anropas i början av en omförhandling av sessionen
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - Initiera en omförhandling av sessionshandskakning med fjärrvärden
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - Rensa och återställa en NetX Secure TLS-session
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - Skicka data via en NetX Secure TLS-session
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-serverhandskakning
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - Parsa ett Servernamnindikator (SNI)-tillägg som tagits emot från en TLS-klient
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - Ange ett DNS Servernamnindikator tillägg (SNI) som ska skickas till en fjärrserver
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - Starta en NetX Secure TLS-session
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - Tilldela en tidsstämpelfunktion till en Säker NetX-TLS-session
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - Lägga till betrott certifikat i NetX Secure TLS-session
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - Ta bort betrott certifikat från NetX Secure TLS-session
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - Initiera X.509-certifikat för NetX Secure TLS
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - Kontrollera DNS-namn mot X.509-certifikat
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - Kontrollera X.509-certifikat mot en agen lista över återkallade certifikat (CRL)]
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - Initiera en X.509 DNS-namnstruktur
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - Hitta och parsa ett utökat X.509-nyckelanvändningstillägg i ett X.509-certifikat
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - Hitta och returnera ett X.509-tillägg i ett X.509-certifikat
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - Hitta och parsa ett X.509-nyckelanvändningstillägg i ett X.509-certifikat

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

Utföra självtest på kryptografimetoderna

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Description

Den här tjänsten körs via kryptometodens självtester för att verifiera. Självtestet är bara tillgängligt om NetX Secure-biblioteket har skapats med symbolen NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definieras.

För varje kryptografimetod som stöds tillhandahåller självtestet fördefinierade indata och verifierar att utdata matchar det fördefinierade förväntade värdet.

NetX Secure crypto self test har stöd för följande algoritmer och nyckelstorlekar:

- DES: kryptering och dekryptering
- Triple DES (3DES): kryptering och dekryptering
- AES: 128-, 192-, 256-bitars nyckelstorlek, kryptering och dekryptering i CBC-läge och räknarläge.
- HMAC-MD5: autentisering och hash-beräkning
- HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, autentisering och hash-beräkning
- MD5: autentisering
- Pseudoslumpfunktion (PRF): PRF_HMAC_SHA1 och PRF_HMAC_SHA2-256
- RSA: 1024-, 2048-, 4096-bitars RSA power-modulus operation
- SHA: SHA1-autentisering (96- och 160-bitars), SHA2-autentisering (256-bitars, 384-bitars, 512-bitars)

Den här funktionen har de inbyggda vektorerna för de krypteringsalgoritmer som anges ovan. Den testar dock bara de som listas i *cipher_table skickas* till den här funktionen. För en TLS-session används till exempel bara chiffer-TLS_RSA_WITH_AES_128_CBC_SHA, den här funktionen utför självtest på RSA (1024-, 2048-, 4096-bitars), AES-CBC (128-bitars) och SHA1.

### <a name="parameters"></a>Parametrar

- **crypto_table** Pekare till kryptografitabellen som används av TLS-sessionen. Det här är samma crypto_table skickas till **_nx_secure_tls_session_create()-anropet._**
- **metadata** Pekare till blanksteg för kryptografimetadataområdet. .
- **metadata_size** Storleken på metadatabufferten.

### <a name="return-values"></a>Returvärden

- **NX_SECURE_TLS_SUCCESS** (0x00) Har testat de angivna kryptometoderna.
- **NX_PTR_ERROR** (0x07) Ogiltig struktur för kryptografimetod
- **NX_NOT_SUCCESSFUL** (0x43) Crypto-självtestet misslyckas.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Beräknar hash-värdet med hjälp av hashfunktionen som användaren har angett

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a>Description

Den här funktionen beräknar hash-värdet för dataströmmen i det angivna minnesområdet med hjälp av den angivna HMAC-kryptografimetoden och nyckelsträngen. Modulens hash-beräkningsfunktion är bara tillgänglig om NetX Secure-biblioteket har skapats med följande symbol som definieras: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK

### <a name="parameters"></a>Parametrar

- **hmac_ptr** Pekare till den HMAC-kryptografimetod som används för beräkningen av hash-värdet.
- **start_address** Startadressen för databufferten
- **end_address** Slutadressen för databufferten. Observera att hash-beräkningen inte omfattar data i den här end_address.
- **nyckel** Nyckelsträngen som används i HMAC-beräkningen.
- **key_length** Storleken på nyckelsträngen, i byte
- **metadata** Pekare till utrymme som används av HMAC-algoritmen.
- **metadata_size** Storleken på metadatabufferten.
- **output_buffer** Minnesplatsen där hash-utdata lagras.
- **output_buffer_size** Tillgängligt utrymme för utdatabufferten, i byte
- **actual_size** Returneras av funktionen som anger det faktiska antalet byte som skrivs till output_buffer.

### <a name="return-values"></a>Returvärden

- **0** Hash-värdet har beräknats.
- **1** Hash-beräkningen misslyckades.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a>Se även

- nx_secure_crypto_method_self_test

## <a name="nx_secure_tls_active_certificate_set"></a>nx_secure_tls_active_certificate_set

Ange det aktiva identitetscertifikatet för en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Description

Den här tjänsten är avsedd att anropas inifrån ett sessionsanrop (se nx_secure_tls_session_client_callback_set och nx_secure_tls_session_server_callback_set). När det anropas med en tidigare initierad NX_SECURE_X509_CERT-struktur används det certifikatet i stället för standardidentitetscertifikatet. I de flesta fall måste certifikatet ha lagts till i det lokala arkivet (se nx_secure_tls_local_certificate_add) annars kan TLS-handskakningen misslyckas.

Den här tjänsten är avsedd att tillåta att TLS stöder flera identitetscertifikat. Detta är användbart för en TLS-server som hanterar flera nätverksadresser så att servern kan välja ett lämpligt certifikat som ska tillhandahållas till fjärrklienten beroende på klientens startpunkt. För en TLS-klient kan den här rutinen användas för att ändra certifikatet som skickas till en fjärrserver vid körning när servern har identifierat sig själv i TLS-handskakningen (detta är mer ovanligt än TLS-serverns användningsfall).

Om flera certifikat kan dela samma unika X.509-namn måste certifikat läggas till med hjälp av nx_secure_tls_server_certificate_add, vilket introducerar en numerisk identifierare som är separat från certifikatet.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans som skickas till återanropet av sessionen.
- **certifikat** Pekare till ett initierat X.509-certifikat som ska användas för den aktuella sessionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tilldelning av certifikat till session.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller certifikat pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_client_psk_set"></a>nx_secure_tls_client_psk_set

Ange en i förväg delad nyckel för en NetX Secure TLS-klientsession

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en I förväg delad nyckel (PSK), dess identitetssträng och en identitetstips till ett TLS-sessionskontrollblock och anger att PSK ska användas i efterföljande TLS-klientanslutningar. PSK används i stället för ett digitalt certifikat när PSK-chiffer har aktiverats och används.

I det här fallet är PSK associerad med en specifik TLS-fjärrserver som TLS-klienten vill kommunicera med. PSK-uppsättningen via det här API:et kommer att tillhandahållas till den fjärranslutna TLS-servervärden under nästa TLS-handskakning.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** Längden på PSK-värdet.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** Längden på PSK-identiteten.
- **tips** En sträng som används för att ange vilken grupp av PSK:er som ska väljas på en TLS-server.
- **hint_length** Längden på tipssträngen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av PSK.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Det går inte att lägga till ytterligare en PSK.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Se även

- nx_secure_tls_psk_add
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_initialize"></a>nx_secure_tls_initialize

Initierar NetX Secure TLS-modulen

### <a name="prototype"></a>Prototyp

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>Description

Den här tjänsten initierar NetX Secure TLS-modulen. Den måste anropas innan andra NetX Secure-tjänster kan nås.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Returvärden

Ingen

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

Lägga till ett lokalt certifikat i NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en NX_SECURE_X509_CERT instans av struktur till det lokala arkivet för en TLS-session. Det här certifikatet kan användas av TLS-stacken för att identifiera enheten under TLS-handskakningen (om den har markerats som ett identitetscertifikat under initieringen av certifikatstrukturen med nx_secure_x509_certificate_initialize) eller som en utfärdare som en del av en certifikatkedja som tillhandahålls till fjärrvärden under TLS-handskakningen.

Om flera lokala certifikat med samma eget namn behövs kan certifikat läggas till med hjälp *nx_secure_tls_server_certificate_add* tjänsten (se varningen nedan).

Ett certifikat krävs **för** TLS-serverläge.

Ett certifikat är *valfritt* för TLS-klientläge.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. API:et för servercertifikat använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på X.509-namnet. De lokala certifikattjänsterna är ett praktiskt alternativ till den numeriska identifieraren för program som endast använder ett enda identitetscertifikat – med hjälp av eget namn behöver programmet inte hålla reda på numeriska identifierare.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certificate_ptr** Pekare till en initierad TLS-certifikatinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.
- **NX_INVALID_PARAMETERS** (0x4D) Försökte lägga till ett ogiltigt eller duplicerat certifikat.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller certifikat pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_find

## <a name="nx_secure_tls_local_certificate_find"></a>nx_secure_tls_local_certificate_find

Hitta ett lokalt certifikat i en NetX Secure TLS-session efter eget namn

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>Description

Den här tjänsten hittar ett certifikat i det lokala enhetscertifikatarkivet för en TLS-session och returnerar en pekare till NX_SECURE_X509_CERT strukturen i arkivet. Parametern common_name och dess längd (name_length) används för att identifiera certifikatet i arkivet genom att matcha certifikatets X.509 Ämnesnamn-fält.

Om det finns fler än ett certifikat med samma eget namn returneras bara det första – använd *nx_secure_tls_server_certificate_find* stället.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. API:et för servercertifikat använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på X.509-namnet. De lokala certifikattjänsterna är ett praktiskt alternativ till den numeriska identifieraren för program som endast använder ett enda identitetscertifikat – med hjälp av eget namn behöver programmet inte hålla reda på numeriska identifierare.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certifikat** Returnera pekaren till matchat certifikat.
- **common_name** Gemensam namnsträng som ska matchas (DNS-namn).
- **name_length** Längden på common_name strängdata.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Certifikatet hittades och pekaren returnerades i parametern "certifikat".
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Inget certifikat med det angivna eget namnet hittades.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session, certifikat pekare eller gemensam namnsträng.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_local_certificate_remove"></a>nx_secure_tls_local_certificate_remove

Ta bort lokalt certifikat från NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en lokal certifikatinstans från en TLS-session som är nyckelad i fältet Eget namn i certifikatet.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. API:et för servercertifikat använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på X.509-namnet. De lokala certifikattjänsterna är ett praktiskt alternativ till den numeriska identifieraren för program som endast använder ett enda identitetscertifikat – med hjälp av eget namn behöver programmet inte hålla reda på numeriska identifierare.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **common_name** Värdet eget namn för certifikatet som ska tas bort.
- **common_name_length** Längden på strängen Eget namn.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119)-certifikatet hittades inte.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_metadata_size_calculate"></a>nx_secure_tls_metadata_size_calculate

Beräkna storleken på kryptografiska metadata för en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Description

Den här tjänsten beräknar och returnerar storleken på de kryptografiska metadata som behövs för en viss TLS-session och TLS-kryptografitabell (mer information om kryptografisk chiffertabell finns i avsnittet "Initiera TLS med kryptografiska metoder").

Den här tjänsten ska anropas med den önskade kryptografiska tabellen för att beräkna storleken på metadatabufferten som skickas nx_secure_tls_session_create.

### <a name="parameters"></a>Parametrar

- **crypto_table** Pekare till en fullständig NetX Secure TLS-kryptografitabell.
- **metadata_size** Utdata från storleksberäkningen i byte.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad beräkning av metadatastorlek.
- **NX_PTR_ERROR** (0x07) Ogiltig kryptografitabell eller pekare för returstorlek.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

Allokera ett paket för en Säker NetX TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten allokerar NX_PACKET för den angivna aktiva TLS-sessionen från den angivna NX_PACKET_POOL. Den här tjänsten ska anropas av programmet för att allokera datapaket som ska skickas via en TLS-anslutning. TLS-sessionen måste initieras innan den här tjänsten anropas.

Det allokerade paketet initieras korrekt så att TLS-sidhuvud- och sidfotsdata kan läggas till när paketdata har fyllts i. Beteendet är annars identiskt med *nx_packet_allocate*.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **pool_ptr** Pekare till NX_PACKET_POOL som paketet ska allokeras från.
- **packet_ptr** Utdata pekare till det nyligen allokerade paketet.
- **wait_option** Indragningsalternativ för paketallokering.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckat paket allokeras.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underliggande paketallokering misslyckades.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a>Se även

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_psk_add"></a>nx_secure_tls_psk_add

Lägga till en i förväg delad nyckel i en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en I förväg delad nyckel (PSK), dess identitetssträng och en identitetstips till ett TLS-sessionskontrollblock. PSK används i stället för ett digitalt certifikat när PSK-chiffer har aktiverats och används.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** Längden på PSK-värdet.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** Längden på PSK-identiteten.
- **tips** En sträng som används för att ange vilken grupp av PSK:er som ska väljas på en TLS-server.
- **hint_length** Längden på tipssträngen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av PSK.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Det går inte att lägga till ytterligare en PSK.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Se även

- nx_secure_tls_client_psk_set
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_remote_certificate_allocate"></a>nx_secure_tls_remote_certificate_allocate

Allokera utrymme för certifikatet som tillhandahålls av en fjärransluten TLS-värd

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en instans NX_SECURE_X509_CERT en oiniterad NX_SECURE_X509_CERT struktur till en TLS-session i syfte att allokera utrymme för certifikat som tillhandahålls av en fjärrvärd under en TLS-session. Fjärrcertifikatdata parsas av NetX Secure TLS och informationen används för att fylla i den certifikatstrukturinstans som tillhandahålls till den här funktionen. Certifikat som läggs till på det här sättet placeras i en länkad lista.

Om det förväntas att fjärrvärden kommer att tillhandahålla flera certifikat ska den här funktionen anropas upprepade gånger för att allokera utrymme för alla certifikat. De ytterligare certifikaten läggs till i slutet av den länkade listan med certifikat.

Om du inte allokerar ett fjärrcertifikat misslyckas TLS-klientläget under TLS-handskakningen, såvida inte PSK-chiffer (Pre-Shared Key) används.

Den *raw_certificate_buffer pekar* på allokerat utrymme för att lagra det inkommande fjärrcertifikatet. Vanliga certifikat med RSA-nycklar på 2 048 bitar som använder SHA-256 för signaturer är i intervallet 1 000–2 000 byte. Bufferten bör vara tillräckligt stor för att minst innehålla den storleken, men beroende på fjärrvärdcertifikaten kan vara betydligt mindre eller större. Observera att om bufferten är för liten för att innehålla det inkommande certifikatet slutar TLS-handskakningen med ett fel.

I TLS-serverläge behövs endast en fjärrcertifikatallokering om klientcertifikatautentisering är aktiverat.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certificate_ptr** Pekare till en oiniterad X.509-certifikatinstans.
- **raw_certificate_buffer** Pekare till en buffert för att lagra det oparsade certifikat som tagits emot från fjärrvärden.
- **raw_buffer_size** Storleken på råcertifikatbufferten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad allokering av certifikat.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Den angivna bufferten var för liten.
- **NX_INVALID_PARAMETERS** (0x4D) Försökte lägga till ett ogiltigt certifikat.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize,
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a>nx_secure_tls_remote_certificate_buffer_allocate

Allokera utrymme för alla certifikat som tillhandahålls av en fjärransluten TLS-värd

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten allokerar utrymme för att bearbeta inkommande certifikatkedjor från fjärrservervärdar för att utföra X.509-autentisering och verifiering i en TLS-klientinstans. För TLS-serverläge behövs endast fjärrcertifikatallokering om X.509-klientcertifikatautentisering är aktiverat – för TLS-serverinstanser ska *tjänsttilldelningen nx_secure_tls_session_x509_client_verify_configure* användas i stället.

Om du inte allokerar fjärrcertifikat misslyckas TLS-klientläget under TLS-handskakningen, såvida inte PSK-chiffer (Pre-Shared Key) används.

Parametern *certificate_buffer* pekar på allokerat utrymme för att lagra inkommande fjärrcertifikat och de kontrollblock som behövs för dessa certifikat. Bufferten divideras med antalet certifikat *(* certs_number ) med en lika stor del som ges till varje certifikat. Parametern *buffer_size*  anger storleken på bufferten. Utrymmet som behövs finns med följande formel:

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Vanliga certifikat med RSA-nycklar på 2 048 bitar som använder SHA-256 för signaturer är i intervallet 1 000–2 000 byte. Bufferten bör vara tillräckligt stor för att minst innehålla den storleken för varje certifikat, men beroende på fjärrvärdcertifikaten kan vara betydligt mindre eller större. Observera att om bufferten är för liten för att innehålla det inkommande certifikatet slutar TLS-handskakningen med ett fel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certs_number** Antal certifikat som ska allokeras från den angivna bufferten.
- **certificate_buffer** Pekare till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.
- **buffer_size** Storleken på certifikatbufferten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad allokering av certifikat.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller buffert pekare.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Den angivna bufferten var för liten.
- **NX_INVALID_PARAMETERS** (0x4D) Bufferten var för liten för att innehålla det önskade antalet certifikat.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_free_all"></a>nx_secure_tls_remote_certificate_free_all

Ledigt utrymme allokerat för inkommande certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten används för att frigöra alla certifikatbuffertar som allokerats till en viss TLS-session genom nx_secure_tls_remote_certificate_allocated genom att returnera dem till sessionens lediga certifikatutrymme. Detta kan vara nödvändigt om ett program återanvänder ett TLS-sessionsobjekt utan att ta bort det och återskapa det med nx_secure_tls_session_delete och nx_secure_tls_session_create.

Observera att fjärrcertifikatutrymmet återställs automatiskt när TLS-sessionen återställs som i nx_secure_tls_session_end så att de flesta program inte behöver anropa den här tjänsten.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Åtgärden lyckades.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.
- **NX_INVALID_PARAMETERS** (0x4D) Internt fel – certifikatarkivet är sannolikt skadat.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_end

## <a name="nx_secure_tls_server_certificate_add"></a>nx_secure_tls_server_certificate_add

Lägga till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Description

Den här tjänsten används för att lägga till ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med hjälp av en numerisk identifierare i stället för att indexera arkivet med hjälp av X.509-certifikatutfärdaren (eget namn) i certifikatet. Den numeriska identifieraren är separat från certifikatet och tillåter att flera certifikat läggs till som identitetscertifikat på en TLS-server, samt att flera certifikat med samma eget namn kan läggas till i samma lokala TLS-sessionsarkiv. Samma tjänst kan användas för klientcertifikat, men det är ovanligt att en TLS-klient har flera identitetscertifikat.

Parametern cert_id är ett positivt heltal utan noll som tilldelats av programmet. Det faktiska värdet spelar ingen roll (förutom noll), men det måste vara unikt i arkivet för den angivna TLS-sessionen. Värdet cert_id kan användas för att hitta och ta bort certifikat från det lokala arkivet med hjälp nx_secure_tls_server_certificate_find och nx_secure_tls_server_certificate_remove, respektive.

> [!IMPORTANT]
> *Det här API:et ska inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. API:nx_secure_tls_server_certificate_add använder en unik numerisk identifierare för varje certifikat och lokala certifikattjänstindex baserat på X.509-namnet. Servercertifikattjänsterna tillåter att flera certifikat med delade data (särskilt eget namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certifikat** Pekare till en tidigare initierad X.509-certifikatinstans.
- **cert_id** Positivt, icke-noll, relativt unikt certifikat-ID-nummer.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00)Åtgärden lyckades.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session ellercertificate-pekare.
- **NX_SECURE_TLS_CERT_ID_INVALID** (0x138) Det angivna certifikat-ID:t hade ett ogiltigt värde (sannolikt 0).
- **NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) Det angivna certifikat-ID:t fanns redan i det lokala arkivet.
- **NX_INVALID_PARAMETERS(0x4D)** Internt fel – certifikatarkivet är sannolikt skadat.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_server_certificate_find"></a>nx_secure_tls_server_certificate_find

Hitta ett certifikat med hjälp av en numerisk identifierare

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>Description

Den här tjänsten används för att hitta ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med hjälp av en numerisk identifierare i stället för att indexera arkivet med hjälp av X.509-ämne (eget namn) i certifikatet.

Parametern cert_id är ett positivt heltal som inte är noll och tilldelas av programmet när certifikatet läggs till i det lokala TLS-sessionsarkivet med hjälp av nx_secure_tls_server_certificate_add.

> [!IMPORTANT]
> *Det här API:et ska inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. API:nx_secure_tls_server_certificate_add använder en unik numerisk identifierare för varje certifikat och lokala certifikattjänstindex baserat på X.509-namnet. Servercertifikattjänsterna tillåter att flera certifikat med delade data (särskilt eget namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certifikat** Pekare till en X.509-certifikat pekare för att returnera en referens till det hittade certifikatet.
- **cert_id** Värde för positivt certifikat-ID som inte är noll.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00)Åtgärden lyckades.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller certifikat pekare.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det angivna certifikat-ID:t matchade inte något i det lokala arkivet för den angivna TLS-sessionen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_remove

##  <a name="nx_secure_tls_server_certificate_remove"></a>nx_secure_tls_server_certificate_remove

Ta bort ett lokalt servercertifikat med hjälp av en numerisk identifierare

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>Description

Den här tjänsten används för att ta bort ett certifikat från en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med hjälp av en numerisk identifierare i stället för att indexera arkivet med hjälp av X.509-certifikatutfärdaren (eget namn) i certifikatet.

Parametern cert_id är ett positivt heltal som inte är noll och tilldelas av programmet när certifikatet läggs till i det lokala TLS-sessionsarkivet med hjälp av nx_secure_tls_server_certificate_add.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **cert_id** Värde för positivt certifikat-ID som inte är noll.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00)Åtgärden lyckades.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det angivna certifikat-ID:t matchade inte något i det lokala arkivet för den angivna TLS-sessionen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_alert_value_get"></a>nx_secure_tls_session_alert_value_get

Hämta TLS-aviseringsvärdet och nivån som skickas av fjärrvärden

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Description

Den här tjänsten används för att hämta TLS-aviseringsnivå och -värde när fjärrvärden skickar en avisering som svar på ett problem eller fel.

Värdena för alert_level- och alert_value-parametrarna är endast giltiga om den här funktionen anropas omedelbart efter ett TLS API-anrop som returnerade statusen NX_SECURE_TLS_ALERT_RECEIVED (0x114) som anger att en avisering togs emot från fjärrvärden.

Observera att om den lokala värdens TLS skickar en avisering är de returnerade felkoderna mycket mer beskrivande för det faktiska felet än själva TLS-aviseringen eftersom TLS-aviseringsvärden avsiktligt lämnas tvetydiga för att förhindra vissa typer av angrepp (till exempel ett "utfyllnadsorakel" eller liknande).

Aviseringsnivån tar bara ett av två värden: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) eller NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2). I allmänhet ges endast CloseNotify-aviseringen (används för att ange ett lyckat slut på en TLS-session) en nivå av "Varning" även om vissa tilläggskonfigurationssituationer också kan betraktas som varningar. De allra flesta aviseringar är "Allvarliga" som indikerar ett potentiellt säkerhetsfel och resulterar i omedelbar stängning av TLS-anslutningen (handskakning eller session).

TLS-aviseringsvärdena definieras i TLS RFCs. Här är listan från RFC 5246 (TLSv1.2) som referens:

| Aviseringsnamn                     | Värde | Beskrivning                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | Inget fel, indikerar att sessionen har avslutas                                                                                                                   |
| unexpected_message            | 10    | TLS tog emot ett oväntat eller oväntad meddelande                                                                                                           |
| bad_record_mac               | 20    | Dekryptering och/eller MAC-verifiering misslyckades                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **INAKTUELL** Dekrypteringen misslyckades (inaktuell på grund av utfyllnad av orakelattacker)                                                                                      |
| record_overflow               | 22    | En post togs emot som är större än den maximala TLS-poststorleken                                                                                        |
| decompression_failure         | 30    | Ett problem inträffade vid komprimering/dekomprimering av en TLS-post                                                                                       |
| handshake_failure             | 40    | Det uppstod ett ospecificerat handskakningsfel som inte omfattas av en annan avisering                                                                            |
| no_certificate_RESERVED      | 41    | **INAKTUELL I** TLS (endast SSL)                                                                                                                                 |
| bad_certificate               | 42    | Ett certifikat som togs emot innehöll ogiltig formatering eller signaturer                                                                                   |
| unsupported_certificate       | 43    | Ett certifikat togs emot som var av en ogiltig typ (t.ex. signeringscertifikat som användes för TLS-serverautentisering)                                    |
| certificate_revoked           | 44    | Certifikatstatusen (som anges av en CRL eller OCSP) angavs som "återkallad"                                                                       |
| certificate_expired           | 45    | Det mottagna certifikatet låg utanför det giltiga datumintervallet (antingen inte giltigt än eller har upphört att gälla)                                                                 |
| certificate_unknown           | 46    | Ett okänt certifikatproblem påträffades som inte omfattas av andra aviseringar                                                                          |
| illegal_parameter             | 47    | Vissa konfigurationer eller förhandlade värden i TLS-handskakningen var ogiltiga eller utanför intervallet                                                                      |
| unknown_ca                    | 48    | Det mottagna identitetscertifikatet kunde inte spåras via en certifikatkedja till ett betrott rotcertifikatutfärdarcertifikat.                                              |
| access_denied                 | 49    | Anger att ett giltigt certifikat togs emot, men programåtkomstkontrollen angav att certifikatet var ogiltigt för de begärda resurserna.            |
| decode_error                  | 50    | Ett fält eller värde i ett TLS-huvud eller handskakningsmeddelande var utanför intervallet eller ogiltigt, vilket ledde till ett fel vid avkodning av en TLS-post.                      |
| decrypt_error                 | 51    | Det gick inte att verifiera en signatur eller slutförd meddelandehash under TLS-handskakningen.                                                                         |
| export_restriction_RESERVED  | 60    | INAKTUELL I TLSv1.2                                                                                                                                        |
| protocol_version              | 70    | Den TLS-protokollversion som förhandlades under handskakningen känns igen men stöds inte (t.ex. TLSv1.0 visades men inte aktiverades).                       |
| insufficient_security         | 71    | Skickas när en handskakning misslyckas på grund av brist på säkra chiffer (t.ex. om nyckelstorleken är för liten för programkraven)                                |
| internal_error                | 80    | Vissa icke-TLS-fel (t.ex. problem med minnesallokering eller program) inträffade, vilket resulterade i en bruten TLS-session.                                         |
| user_canceled                 | 90    | Returneras om TLS-sessionen avbryts av en användare eller ett program innan handskakningen är klar (liknar CloseNotify).                                 |
| no_renegotiation              | 100   | Indiates att fjärrvärden inte är beredd att utföra TLS-omförhandlingshandskakningar som svar på en omförhandlingsbegäran.                                 |
| unsupported_extension         | 110   | Skickas om en TLS-klient tar emot ett ServerHello-tillägg som inte uttryckligen efterfrågas i den första ClientHello (vilket indikerar att servern har problem). |

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **alert_level** Returnera nivån för den mottagna aviseringen (varning eller allvarliga).
- **alert_value** Returnera värdet för den mottagna aviseringen (se tabell).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Åtgärden lyckades.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_start
- nx_secure_tls_session_send
- nx_secure_tls_session_receive

## <a name="nx_secure_tls_session_certificate_callback_set"></a>nx_secure_tls_session_certificate_callback_set

Konfigurera ett återanrop för TLS som ska användas för ytterligare certifikatverifiering

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en funktionspekare till en TLS-session som TLS anropar när ett certifikat tas emot från en fjärrvärd, så att programmet kan utföra verifieringskontroller som DNS-verifiering, återkallelse av certifikat och tillämpning av certifikatprincip.

NetX Secure TLS utför grundläggande X.509-sökvägsverifiering på certifikatet innan motringningen anropas för att säkerställa att certifikatet kan spåras till ett certifikat i det betrodda TLS-certifikatarkivet, men all annan validering hanteras av det här återanropet.

Motringningen ger TLS-sessionspekaren och en pekare till fjärrvärdidentitetscertifikatet (lövnoden i certifikatkedjan). Motringningen ska returnera NX_SUCCESS om all validering har lyckats, annars bör den returnera en felkod som anger verifieringsfelet. Alla andra värden än NX_SUCCESS kommer att orsaka att TLS-handskakningen avbryts omedelbart.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **func_ptr** Pekare till återanropsfunktionen för certifikatverifiering.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad allokering av funktionspekaren.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_tls_session_client_callback_set"></a>nx_secure_tls_session_client_callback_set

Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-klienthandskakning

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en funktions pekare till en TLS-session som TLS anropar när en TLS-klienthandskakning har tagit emot ett ServerHelloDone-meddelande. Med återanropsfunktionen kan ett program bearbeta alla TLS-tillägg från det mottagna ServerHello-meddelandet som kräver indata eller beslutsfattande.

Motringningen körs med det anropande TLS-sessionskontrollblocket och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt. Matrisen med tilläggsobjekt är avsedd att skickas till en hjälpfunktion som hittar och parsar ett visst tillägg. Det finns för närvarande inga specifika tillägg som stöds i NetX Secure som kräver TLS-klientindata, men återanropet är tillgängligt för programdesigners för att hantera anpassade eller nya tillägg som kan bli tillgängliga. Ett exempel på en hjälpfunktion som parsar TLS-tillägg som finns i hello messages finns *i nx_secure_tls_session_sni_extension_parse*.

Återanropet av klienten kan också användas för att välja det aktiva identitetscertifikatet med *hjälp av nx_secure_tls_active_certificate_set* för TLS-klienten om fjärrservern har begärt ett certifikat och angett information som gör att TLS-klienten kan välja ett specifikt certifikat. Se referensen för nx_secure_tls_active_certificate_set mer information.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **func_ptr** Pekare till funktionen för återanrop av TLS-klient.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad allokering av funktionspekare.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a>nx_secure_tls_session_x509_client_verify_configure

Aktivera X.509-klientverifiering och allokera utrymme för klientcertifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar valfri X.509-klientautentisering för en TLS-serverinstans. Den allokerar också det utrymme som krävs för att bearbeta inkommande certifikatkedjor från fjärrklientvärden. Certifikaten som tillhandahålls av fjärrklienten verifieras mot TLS-serverinstansens betrodda certifikat, som tilldelas med tjänsten *nx_secure_tls_trusted_certificate_add.*

För TLS-klientläget krävs fjärrcertifikatallokering och nx_secure_tls_remote_certificate_buffer_allocate *bör* användas i stället. Aktivering av X.509-klientautentisering på en TLS-klientinstans har ingen effekt.

Parametern *certificate_buffer* pekar på allokerat utrymme för att lagra inkommande fjärrcertifikat och de kontrollblock som behövs för dessa certifikat. Bufferten divideras med antalet certifikat *(* certs_number ) med en lika stor del som ges till varje certifikat. Parametern *buffer_size* anger storleken på bufferten. Utrymmet som behövs finns med följande formel:

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Vanliga certifikat med RSA-nycklar på 2 048 bitar som använder SHA-256 för signaturer är i intervallet 1 000–2 000 byte. Bufferten bör vara tillräckligt stor för att minst innehålla den storleken för varje certifikat, men beroende på fjärrvärdcertifikaten kan vara betydligt mindre eller större. Observera att om bufferten är för liten för att innehålla det inkommande certifikatet, slutar TLS-handskakningen med ett fel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certs_number** Antal certifikat som ska allokeras från den angivna bufferten.
- **certificate_buffer** Pekare till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.
- **buffer_size** Certifikatbuffertens storlek.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00)Lyckad allokering av certifikat.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-session eller buffertpekare.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Den angivna bufferten var för liten.
- **NX_INVALID_PARAMETERS** (0x4D) Bufferten var för liten för att innehålla det önskade antalet certifikat.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_buffer_allocate

## <a name="nx_secure_tls_session_client_verify_disable"></a>nx_secure_tls_session_client_verify_disable

Inaktivera klientcertifikatautentisering för en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar klientcertifikatautentisering för en specifik TLS-session. Mer information nx_secure_tls_session_client_verify_enable finns i nx_secure_tls_session_client_verify_enable.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillståndsändring.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_client_verify_enable"></a>nx_secure_tls_session_client_verify_enable

Aktivera klientcertifikatautentisering för en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar klientcertifikatautentisering för en specifik TLS-session. Om du aktiverar klientcertifikatautentisering för en TLS-serverinstans kommer TLS-servern att begära ett certifikat från valfri TLS-fjärrklient under den första TLS-handskakningen. Certifikatet som tas emot från den fjärranslutna TLS-klienten åtföljs av ett CertificateVerify-meddelande som TLS-servern använder för att verifiera att klienten äger certifikatet (har åtkomst till den privata nyckel som är associerad med certifikatet).

Om det angivna certifikatet kan verifieras och spåras tillbaka till ett certifikat i TLS-serverns betrodda certifikatarkiv via en X.509-certifikatkedja autentiseras den fjärranslutna TLS-klienten och handskakningen fortsätter. Om det uppstår fel vid bearbetning av certifikatet eller CertificateVerify-meddelandet slutar TLS-handskakningen med ett fel.

> [!NOTE]
> *TLS-servern måste ha minst ett certifikat i det betrodda arkivet som lagts till med nx_secure_tls_trusted_certificate_add annars misslyckas autentiseringen alltid.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillståndsändring.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_tls_session_create"></a>nx_secure_tls_session_create

Skapa en NetX Secure TLS-session för säker kommunikation

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>Description

Den här tjänsten initierar en NX_SECURE_TLS_SESSION-strukturinstans för användning vid etablering av säker TLS-kommunikation via en nätverksanslutning.

Metoden tar ett NX_SECURE_TLS_CRYPTO objekt som fylls i med de tillgängliga kryptografiska metoder som ska användas för TLS. Den *encryption_metadata_area* pekar på en buffert som allokerats för användning av TLS för de "metadata" som används av de kryptografiska metoderna i NX_SECURE_TLS_CRYPTO-tabellen för beräkningar. Tabellens storlek kan fastställas med hjälp av nx_secure_tls_metadata_size_calculate tjänsten. Mer information finns i avsnittet "Kryptografi i NetX Secure TLS" i kapitel 3.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **cipher_table** Pekare till kryptografiska TLS-metoder.
- **encryption_metadata_area** Pekare till blanksteg för kryptografimetadata.
- **encryption_metadata_size** Storleken på metadatabufferten.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00)Lyckad initiering av TLS-sessionen.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.
- **NX_INVALID_PARAMETERS** (0x4D) Metadatabufferten var för liten för de angivna metoderna.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) En obligatorisk chiffermetod för den aktiverade versionen av TLS angavs inte i chiffertabellen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_metadata_size_calculate
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_delete
- Kryptografi i NetX Secure TLS i kapitel 3

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

Ta bort en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en TLS-session som representeras av en NX_SECURE_TLS_SESSION-strukturinstans och släpper alla systemresurser som ägs av den sessionsinstansen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_end"></a>nx_secure_tls_session_end

Avsluta en aktiv NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten avslutar en TLS-session som representeras av en NX_SECURE_TLS_SESSION-strukturinstans genom att skicka TLS CloseNotify-meddelandet till fjärrvärden. Tjänsten väntar sedan på att fjärrvärden ska svara med ett eget CloseNotify-meddelande.

Om fjärrvärden inte skickar ett CloseNotify-meddelande betraktar TLS detta som ett fel och en möjlig säkerhetsöverträdelse, så det är viktigt att kontrollera returvärdet för en säker anslutning. Parametern **wait_option** kan användas för att styra hur länge tjänsten ska vänta på svaret innan kontrollen återgår till den anropande tråden.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **wait_option** Anger hur länge tjänsten ska vänta på svaret från fjärrvärden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) tog inte emot något svar från fjärrvärden innan den tog slut.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att allokera ett paket för att skicka CloseNotify-meddelandet.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka CloseNotify-meddelandet via TCP-socketen.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_packet_buffer_set"></a>nx_secure_tls_session_packet_buffer_set

Ange paketsammansättningsbufferten för en Säker NetX-TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten associerar ett paket med en återmonteringsbuffert till en TLS-session. För att kunna dekryptera och parsa inkommande TLS-poster måste data i varje post sammanställas från de underliggande TCP-paketen. TLS-poster kan vara upp till 16 kB stora (men är vanligtvis mycket mindre) så de kanske inte får plats i ett enda TCP-paket.

Om du vet att den inkommande meddelandestorleken kommer att vara mindre än TLS-postgränsen på 16 kB, kan buffertstorleken göras mindre, men för att hantera okända inkommande data bör bufferten göras så stor som möjligt. Om en inkommande post är större än den angivna bufferten avslutas TLS-sessionen med ett fel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **buffer_ptr** Pekare till buffert för TLS som ska användas för paket på ett återmonterat sätt.
- **buffer_size** Storleken på den angivna bufferten i byte.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_INVALID_PARAMETERS** (0x4D) Ogiltig buffert eller TLS-sessionspekare.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_protocol_version_override"></a>nx_secure_tls_session_protocol_version_override

Åsidosätt standardversionen av TLS-protokollet för en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Description

Den här tjänsten åsidosätter standardversionen av TLS-protokollet (senaste) som används av en viss session. Detta gör att NetX Secure TLS kan använda en äldre version av TLS för en specifik TLS-session utan att inaktivera nyare TLS-versioner vid kompileringstiden. Detta kan vara användbart i program som kan behöva kommunicera med en äldre värd som inte stöder den senaste versionen av TLS.

> [!IMPORTANT]
> *Från och med version 5.11SP3 stöder NetX Secure TLS RFC 7507 (se anmärkning nedan) och eventuella åsidosättningar till en äldre version med detta API leder till att en ÅTERSTÄLLNINGs-SCSV skickas i ClientHello. Om servern stöder en nyare version av TLS och återställnings-SCSV:en ingår i ClientHello avbryter den servern TLS-handskakningen med en avisering om olämplig återställning. SCSV skickas endast när versionsåsidosättning är en äldre version av TLS än vad som är aktiverat (t.ex. om du åsidosätter versionen till TLS 1.2 skickas ingen SCSV).*

Giltiga värden för protocol_version är följande makron: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 och NX_SECURE_TLS_VERSION_TLS_1_2.

Makron som NX_SECURE_TLS_DISABLE_TLS_1_1 och NX_SECURE_TLS_ENABLE_TLS_1_0 kan användas för att styra vilka versioner av TLS som kompileras i programmet. TLS version 1.2 är alltid aktiverad.

Observera att om fjärrvärden inte stöder den angivna versionen misslyckas anslutningen – endast den angivna åsidosättningsversionen förhandlas av NetX Secure TLS.

> [!IMPORTANT]
> RFC 7507: TLS Fallback SCSV. Denna RFC introducerades för att minimera ett säkerhetsproblem som ursprungligen orsakades av servrar som felaktigt hanterade protokoll nedgraderingsförhandlingen och i stället avvisade annars giltiga ClientHello-meddelanden. I ett försök att fortsätta vara kompatibelt med dessa gamla servrar började vissa TLS-klientprogram att försöka utföra misslyckade handskakningar på nytt med och äldre TLS-version (t.ex. misslyckades TLS 1.2 så försök med TLS 1.1). Den här lösningen introducerade dock ett nytt problem – en angripare kan tvinga en klient att nedgradera genom att artificiellt införa ett nätverks- eller paketfel som orsakar att serveranslutningen misslyckas – även om servern hade stöd för den nyare TLS-versionen. Genom att nedgradera till en äldre version kan angriparen utnyttja svagheter i den versionen (särskilt SSLv3<sup>21</sup> är svag för ATTACKENDLE). För att förhindra den här situationen har RFC 7507 introduduerat "återställnings-SCSV", en pseudociphersuite<sup>22</sup> som skickas i ClientHello som meddelar en TLS-server när en TLS-klient använder en TLS-version som inte är den senaste versionen som stöds. På så sätt kan en server som stöder en nyare version avvisa en ClientHello som innehåller återställnings-SCSV och förhindra att nedgraderingsattacken lyckas.

21. NetX Secure implementerar inte SSLv3 på grund av att det finns kända allvarliga svagheter, till exempelDLE.

22. En pseudociphersuite, eller SCSV (Signaling Cipher Suite Value), är ett reserverat chiffersvitnummer som används för att signalera aktiverade TLS-implementeringar om funktioner som inte var tillgängliga i äldre TLS-versioner. Återställnings-SCSV och TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) är exempel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **protocol_version** TLS-versions makro för den specifika TLS-version som ska användas.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillståndsändring.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Känd men inte stöds TLS-version.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ogiltig protokollversion.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_receive"></a>nx_secure_tls_session_receive

Ta emot data från en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten tar emot data från den angivna aktiva TLS-sessionen och hanterar dekrypteringen av dessa data innan den ges till anroparen i NX_PACKET parametern. Om inga data köas i den angivna sessionen pausas anropet baserat på det angivna väntealternativet.

> [!IMPORTANT]
> *Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **packet_ptr** Pekare till en allokerad TLS-paket pekare.
- **wait_option** Anger hur länge tjänsten ska vänta på ett paket från fjärrvärden innan den returneras.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_NO_PACKET** (0x01) Inga data har tagits emot.
- **NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett mottaget meddelande misslyckades med en autentiseringshasharkontroll.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget meddelande innehöll en okänd protokollversion i rubriken.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Tog emot en TLS-avisering från fjärrvärden.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a>Se även

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a>nx_secure_tls_session_renegotiate_callback_set

Tilldela ett återanrop som anropas i början av en omförhandling av sessionen

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Description

Den här tjänsten tilldelar ett återanrop till en TLS-session som anropas när det första meddelandet i en omförhandling av session tas emot från fjärrvärden.

Återanropsfunktionen är avsedd som ett meddelande till programmet om att en omförhandling av handskakningen har börjat – programmet kan välja att avsluta TLS-sessionen genom att returnera ett värde som inte är noll från återanropet, vilket gör att TLS avslutar TLS-sessionen med ett fel. Om programmet vill fortsätta med omförhandlingen ska återanropet returnera NX_SUCCESS.

> [!NOTE]
> *På grund av semantiken för TLS-omförhandling anropas motringningen för NetX Secure TLS-klienter när en HelloRequest tas emot från fjärrservern, men inte när klienten initierar omförhandlingen. På NetX Secure TLS-servrar anropas motringningen när en omförhandling av ClientHello tas emot (alla ClientHello tas emot i samband med en aktiv TLS-session). Det innebär att återanropet anropas oavsett om fjärrvärden eller det lokala programmet har initierat omförhandlingen eftersom TLS-servern skickar en HelloRequest som fjärrklienten svarar på.*

NetX Secure TLS implementerar Secure Renegotiation Incation Extension från RFC 5746 för att säkerställa att omförhandling av handskakningar inte utsätts för man-in-the-middle-attacker.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till TLS-sessionsinstans.
- **func_ptr** Pekare till återanropsfunktionen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tilldelning av återanrop.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare för återanropsfunktionen eller TLS-sessionen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiate

## <a name="nx_secure_tls_session_renegotiate"></a>nx_secure_tls_session_renegotiate

Starta en omförhandling av sessionhandskakning med fjärrvärden

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Description

Den här tjänsten initierar en *handskakning om sessionsförhandling* med en ansluten fjärransluten TLS-värd. En omförhandling består av en andra TLS-handskakning i kontexten för en tidigare etablerad TLS-session. Vart och ett av de nya handskakningsmeddelandena krypteras med TLS-sessionen tills nya sessionsnycklar genereras och ChangeCipherSpec-meddelanden utbyts, då de nya nycklarna används för att kryptera alla meddelanden.

En omförhandling kan initieras när som helst när en TLS-session har upprättats. Om en omförhandling görs under en TLS-handskakning eller innan en TLS-session upprättas vidtas ingen åtgärd.

> [!NOTE]
> *En hel TLS-handskakning utförs när den här tjänsten anropas, så tiden till slutförande och returnerad status varierar beroende på aktuella TLS-inställningar och sessionsparametrar.*

NetX Secure TLS implementerar Secure Renegotiation Incation Extension från RFC 5746 för att säkerställa att omförhandling av handskakningar inte utsätts för man-in-the-middle-attacker.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till TLS-sessionsinstans.
- **wait_option** Anger hur länge tjänsten ska vänta på ett paket från fjärrvärden innan den returneras. Detta skickas till alla NetX-tjänster i TLS.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad omförhandling.
- **NX_NO_PACKET** (0x01) Inga data har tagits emot.
- **NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett mottaget meddelande misslyckades med en autentiseringshasharkontroll.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget meddelande innehöll en okänd protokollversion i rubriken.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Tog emot en TLS-avisering från fjärrvärden.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) Den lokala eller fjärranslutna TLS-sessionen är inaktiv, vilket gör omförhandling omöjligt.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) Fjärrvärden tillhandahåller inte antingen SCSV eller Secure Renegotiation Extension och därför går det inte att utföra omförhandling.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underliggande paketallokering misslyckades.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiation_callback_set

## <a name="nx_secure_tls_session_reset"></a>nx_secure_tls_session_reset

Rensa och återställa en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar ut en TLS-session och återställer tillståndet som om sessionen precis hade skapats så att ett befintligt TLS-sessionsobjekt kan användas på nytt för en ny session.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_INVALID_PARAMETERS** (0x4D) Ogiltig TLS-sessionspekare.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_send"></a>nx_secure_tls_session_send

Skicka data via en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar data i den NX_PACKET, med hjälp av den angivna aktiva TLS-sessionen och hanterar krypteringen av dessa data innan de skickas till fjärrvärden. Om mottagarens senast annonserade fönsterstorlek är mindre än den här begäran, pausar tjänsten eventuellt baserat på de angivna väntealternativen.

> [!IMPORTANT]
> *Om inget fel returneras ska programmet inte släppa paketet efter det här anropet. Detta leder till oförutsägbara resultat eftersom nätverksdrivrutinen släpper paketet efter överföringen.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **packet_ptr** Pekare till ett TLS-paket som innehåller data som ska skickas.
- **wait_option** Definierar hur tjänsten beter sig om begäran är större än mottagarens fönsterstorlek.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_NO_PACKET** (0x01) Inga data tas emot.
- **NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka den underliggande TCP-socketen.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Den angivna TLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a>Se även

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_server_callback_set"></a>nx_secure_tls_session_server_callback_set

Konfigurera ett återanrop för TLS som ska anropas i början av en TLS-serverhandskakning

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Description

Den här tjänsten tilldelar en funktions pekare till en TLS-session som TLS anropar när en TLS-serverhandskakning har tagit emot ett ClientHello-meddelande. Med återanropsfunktionen kan ett program bearbeta alla TLS-tillägg från det mottagna ClientHello-meddelandet som kräver indata eller beslutsfattande.

Motringningen körs med det anropande TLS-sessionskontrollblocket och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt. Matrisen med tilläggsobjekt är avsedd att skickas till en hjälpfunktion som hittar och parsar ett visst tillägg. Ett exempel på en hjälpfunktion som parsar TLS-tillägg som finns i hello messages finns *i nx_secure_tls_session_sni_extension_parse*.

Serveranropet kan också användas för att välja det aktiva identitetscertifikatet *med hjälp nx_secure_tls_active_certificate_set* för TLS-servern. Detta inträffar oftast som svar på ett Servernamnindikator-tillägg (SNI) som gör att en TLS-klient kan ange vilken server den försöker kontakta. Se referenserna för *nx_secure_tls_session_sni_extension_parse* *och nx_secure_tls_active_certificate_set* mer information.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **func_ptr** Pekare till funktionen för återanrop av TLS-server.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad allokering av funktionspekaren.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_active_certificate_set
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_sni_extension_parse"></a>nx_secure_tls_session_sni_extension_parse

Parsa ett Servernamnindikator (SNI)-tillägg som tagits emot från en TLS-klient

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Description

Den här tjänsten är avsedd att anropas inifrån en TLS-serversession som läggs till i en TLS-session med hjälp av nx_secure_tls_session_server_callback_set. Motringning anropas efter mottagningen av ett ClientHello-meddelande från en fjärransluten TLS-klient och tillhandahålls en matris med tillgängliga tillägg (och antalet tillägg i matrisen). Matrisen och dess längd kan skickas direkt till den här rutinen för att avgöra om det finns ett SNI-tillägg – annars returneras NX_SECURE_TLS_EXTENSION_NOT_FOUND som anger att klienten valde att inte visa SNI-tillägget (detta är inte ett fel).

Om SNI-tillägget hittas returneras X.509 DNS-namnet som anges av TLS-klienten i dns_name strukturen. För närvarande tillhandahåller SNI-tillägget endast en enda DNS-namnpost som kan användas av TLS-servern för att avgöra vilket identitetscertifikat som ska skickas till fjärrklienten.**

Den NX_SECURE_X509_DNS_NAME strukturen innehåller helt enkelt DNS-namnet som en UCHAR-sträng *i fältet nx_secure_x509_dns_name* och längden på namnsträngen i *nx_secure_x509_dns_name_length*. Makron NX_SECURE_X509_DNS_NAME_MAX kontrollerar storleken på nx_secure_x509_dns_name bufferten.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **tillägg** Pekare till en matris med TLS Hello-tillägg (från sessionsanrop).
- **num_extensions** Antal tillägg i matrisen (från återanrop av session).
- **dns_name** Returnera DNS-namnet som anges i SNI-tillägget.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad parsning av tillägget.
- **NX_PTR_ERROR** (0x07) Ogiltig extensions-matris eller TLS-sessionspekare.
- **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI-tillägget hittades inte.
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI-tilläggsformatet var ogiltigt.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

### <a name="see-also"></a>Se även

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

Ange ett DNS Servernamnindikator tillägg (SNI) som ska skickas till en fjärrserver

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Description

Med den här tjänsten kan ett TLS-klientprogram tillhandahålla ett föredraget dns-servernamn till en fjärransluten TLS-server med hjälp av TLS-tillägget för Servernamnindikator (SNI). Med SNI-tillägget kan servern välja rätt identitetscertifikat och parametrar baserat på klientens angivna serverpreferenser. SNI-tillägget stöder för närvarande bara ett enda DNS-namn som ska skickas, därav parametern singular name. Parametern dns_name initieras med *nx_secure_x509_dns_name_initialize* och innehåller klientens föredragna server. Om du vill ta bort namnet på tillägget anropar du bara den här tjänsten med parametervärdet "dns_name" NX_NULL.

Den NX_SECURE_X509_DNS_NAME strukturen innehåller helt enkelt DNS-namnet som en UCHAR-sträng  *i fältet nx_secure_x509_dns_name* och längden på namnsträngen i *nx_secure_x509_dns_name_length*. Makro-NX_SECURE_X509_DNS_NAME_MAX styr storleken på nx_secure_x509_dns_name bufferten.

> [!NOTE]
> *Den här rutinen måste anropas innan nx_secure_tls_session_start anropas, annars innehåller ClientHello inte SNI-tillägget.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **dns_name** DNS-namn som anges av programmet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades tillägg av DNS-servernamn.
- **NX_PTR_ERROR** (0x07) Ogiltigt DNS-namn eller TLS-sessionspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_start
- nx_secure_x509_dns_name_initialize

## <a name="nx_secure_tls_session_start"></a>nx_secure_tls_session_start

Starta en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten startar en TLS-session med hjälp av det angivna TLS-sessionskontrollblocket och en ansluten TCP-socket. TCP-anslutningen måste redan slutföras efter ett lyckat anrop till antingen nx_tcp_client_socket_connect eller nx_tcp_server_socket_accept.

Den här tjänsten avgör typen av TLS-session (klient eller server) från TCP-socketen.

Väntealternativet definierar hur tjänsten beter sig medan TLS-handskakningen pågår.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **tcp_socket_ptr** Pekare till en ansluten TCP-socket.
- **wait_option** Definierar hur tjänsten beter sig medan TLS-handskakningen pågår.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) En mottagen TLS-meddelandetyp är felaktig.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Meddelandebearbetningen under TLS-handskakningen misslyckades.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett inkommande meddelande misslyckades med en hash-MAC-kontroll.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka underliggande TCP-socket.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Ett inkommande meddelande hade ett fält med ogiltig längd.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Ett inkommande ChangeCipherSpec-meddelande var felaktigt.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Ett inkommande TLS-certifikat kan inte användas för att identifiera TLS-fjärrservern.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Chiffer med offentlig nyckel som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Fjärrvärden har inte angett några chiffer som stöds av NetX Secure TLS-stacken.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget TLS-meddelande hade en okänd TLS-version i huvudet.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Ett mottaget TLS-meddelande hade en känd TLS-version som inte stöds i rubriken.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) En intern TLS-paketallokering misslyckades.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Fjärrvärden angav ett ogiltigt certifikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Fjärrvärden skickade en avisering som anger ett fel och avslutar TLS-sessionen.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) En post i chiffertabellen hade en NULL-funktionspekare.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) En fjärransluten TLS ClientHello innehöll återställnings-SCSV:n och ett versionshanteringsförsök.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a>Se även

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_send
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_end
- nx_secure_tls_session_create
- nx_tcp_socket_accept
- nx_tcp_socket_listen
- nx_tcp_socket_disconnect
- nx_tcp_socket_unaccept
- nx_tcp_socket_relisten
- nx_tcp_socket_delete
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset

## <a name="nx_secure_tls_session_time_function_set"></a>nx_secure_tls_session_time_function_set

Tilldela en tidsstämpelfunktion till en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Description

Den här funktionen ställer in en funktionspekare som TLS anropar när den behöver hämta den aktuella tiden, som används i olika TLS-handskakningsmeddelanden och för verifiering av certifikat.

Funktionen förväntas returnera aktuell GMT i 32-bitarsformat UNIX (sekunder sedan midnatt från och med den 1 januari 1970, UTC, ignorerar skottsekunder), enligt ClientHello-kraven i TLS RFC 5246.

Om ingen tidsstämpelfunktion tilldelas används värdet 0 för tidsstämpeln i TLS-handskakningen och kontrollen av förfallodatum för certifikat fungerar inte.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsinstans.
- **time_func_ptr** Pekare till en funktion som returnerar den aktuella tiden (GMT) UNIX 32-bitars format.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_INVALID_PARAMETERS** (0x4D) Ogiltig TLS-sessionspekare.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_sendnx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_trusted_certificate_add"></a>nx_secure_tls_trusted_certificate_add

Lägga till betrott certifikat i NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en NX_SECURE_X509_CERT instans av en struktur i en TLS-session. Det här certifikatet används av TLS-stacken för att verifiera certifikat som tillhandahålls av fjärrvärden under TLS-handskakningen.

Betrodda certifikat krävs för TLS-klientläge.

Betrodda certifikat krävs endast för TLS-serverläge om klientcertifikatautentisering är aktiverat.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **certificate_ptr** Pekare till en initierad TLS-certifikatinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.
- **NX_INVALID_PARAMETERS** (0x4D) Försökte lägga till ett ogiltigt certifikat.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_remove

## <a name="nx_secure_tls_trusted_certificate_remove"></a>nx_secure_tls_trusted_certificate_remove

Ta bort betrott certifikat från NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>Description

Den här tjänsten tar bort ett betrott certifikat från en TLS-session som är nyckelad i fältet Eget namn i certifikatet.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-sessionsinstans.
- **common_name** Värdet eget namn för certifikatet som ska tas bort.
- **common_name_length** Längden på strängen Eget namn.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.
- **NX_PTR_ERROR** (0x07) Ogiltig TLS-sessionspekare.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119)-certifikatet hittades inte.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Se även

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_x509_certificate_initialize"></a>nx_secure_x509_certificate_initialize

Initiera X.509-certifikat för NetX Secure TLS

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a>Description

Den här tjänsten initierar NX_SECURE_X509_CERT en struktur från ett binärt kodat digitalt X.509-certifikat för användning i en TLS-session.

Certifikatdata måste **vara** ett giltigt digitalt X.509-certifikat i DER-kodat binärt format. Vissa data kan komma från valfri källa (t.ex. filsystem, kompilerad konstant buffert osv.) så länge en UCHAR-pekare till dessa data tillhandahålls.

Parametern *raw_data_buffer* och dess storlek är valfria parametrar som anger en dedikerad buffert som certifikatdata kopieras till innan parsning. Om raw_data_buffer skickas som NX_NULL kommer NX_SECURE_X509_CERT-strukturen att peka direkt till certificate_data -matrisen (buffer_size ignoreras i det här fallet). Om raw_data_buffer skickas som NX_NULL ***ska*** du inte ändra de data som pekar på certificate_data pekaren eller certifikatbearbetningen kommer troligen att misslyckas!

Den privata nyckelparametern är för lokala identitetscertifikat – den privata nyckeln används av servrar för att dekryptera inkommande nyckeldata från en klient (krypteras med serverns offentliga nyckel) och av klienter för att verifiera deras identitet till en server när servern begär ett klientcertifikat. Om du lägger till en privat nyckel med det här API:et markeras det associerade certifikatet automatiskt som ett identitetscertifikat för ett TLS-program. När du initierar certifikat för andra syften (t.ex. det betrodda arkivet) ska *private_key_data-parametern* skickas som NULL, *private_key_data_length* som 0 och *private_key_type* ska skickas som NX_SECURE_X509_KEY_TYPE_NONE.

Parametern *private_key_type* anger formateringen av den privata nyckeln. Om den privata nyckeln till exempel är en PRIVAT RSA-nyckel med DER-kodad PKCS#1-format ska private_key_type skickas som NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, en typ som är känd för NetX Secure som parsas omedelbart och sparas för senare användning.

Den private_key_type också stöd för användardefinierade nyckeltyper<sup>23</sup> för plattformar och program som har specifika nyckelformat eller andra behov. En maskinvarubaserad krypteringsmotor kan till exempel använda ett visst format som inte kan tolkas av NetX Secure-programvaran, eller så kan en privat nyckel krypteras eller representeras av en kryptografitoken, vilket kan vara fallet med en kryptografisk Trusted Platform Module (TPM) eller PKCS#11-maskinvara. När en användardefinierad nyckeltyp används skickas nyckeldata ordagrant till lämplig kryptografirutin. Till exempel skulle en privat RSA-nyckel skickas, utan parsning eller bearbetning, direkt till den KRYPTOgrafiska RSA-rutin som tillhandahålls till TLS i chiffersvittabellen. Den användardefinierade nyckeltypen skickas också till den kryptografiska rutinen (när det gäller RSA är det här parametern "op").

Intervallet med användardefinierade nycklar omfattar den övre halvan av ett 32-bitars heltal utansignerat heltal, från 0x0001 0000-0xFFFF FFFF. Värden som är mindre 0x0001 0000 är reserverade för NetX Secure-användning.

Användardefinierade nyckeltyper är en avancerad funktion som kräver anpassade kryptografiska rutiner för att hantera rådata för privata nycklar. Kontakta din Express Logic-representant om du behöver den här funktionen.

### <a name="parameters"></a>Parametrar

- **certificate_ptr** Pekare till en oiniterad X.509-certifikatinstans.
- **certificate_data** Pekare till DER-kodade X.509-binära data.
- **raw_data_buffer** Pekare till valfri dedikerad certifikatdatabuffert.
- **buffer_size** Storleken på valfri dedikerad certifikatdatabuffert.
- **certificate_data_length** Längden på binära certifikatdata i byte.
- **private_key_data** Pekare till valfria privata nyckeldata.
- **private_key_data_length** Längden på privata nyckeldata.
- **private_key_type** Nyckeltypsidentifierare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av certifikat.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certifikatdata innehöll inte ett DER-kodat X.509-certifikat.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D)-certifikatet hade ingen kryptering med offentlig nyckel som stöds av NetX Secure.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Privat nyckel eller certifikat innehöll inte en giltig ASN.1-sekvens.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) Den angivna privata nyckeln var inte en giltig PKCS#1 RSA-nyckel.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) Den angivna privata nyckeltypen var inte användardefinierad och matchade inte någon känd typ.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a>Se även

- nx_secure_local_certificate_add
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- Importera X.509-certifikat till NetX Secure i kapitel 3.

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

Kontrollera DNS-namn mot X.509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Description

Den här tjänsten kontrollerar ett certifikats eget namn mot ett toppdomännamn (TLD) som tillhandahålls av anroparen i syfte att DNS-verifiering av en fjärrvärd. Den här verktygsfunktionen är avsedd att anropas inifrån en återanropsrutin för certifikatverifiering som tillhandahålls av programmet. TLD-namnet ska vara den översta delen av den URL som används för att komma åt fjärrvärden (.) -separated string before the first slash). Om eget namn innehåller ett jokertecken (till exempel .example.com) matchar jokertecknet alla med *samma suffix. Observera att* endast det första jokertecknet (" ") som påträffas (läsning från höger till vänster) övervägs för  matchning med jokertecken – till exempel matchar abc.*.example.com alla namn som slutar på ".example.com".

Om det gemensamma namnet inte matchar den angivna strängen parsas tillägget "subjectAltName" (om det finns i certifikatet) och eventuella DNSName-poster jämförs också. Om ingen av dessa poster matchar returneras ett fel.

Det är viktigt att förstå formatet för det vanliga namnet (och subjectAltName-poster) i förväntade certifikat. Vissa certifikat kan till exempel använda en rå IP-adress eller ett jokertecken. DNS-TLD-strängen måste vara formaterad så att den matchar förväntade värden i mottagna certifikat.

### <a name="parameters"></a>Parametrar

- **certificate_ptr** Pekare till en X.509-certifikatinstans.
- **dns_tld** Top-Level domännamn att jämföra med.
- **dns_tld_length** Längden på TLD-strängen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad jämförelse med Eget namn eller subjectAltName.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) Inget matchande namn hittades.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_x509_crl_revocation_check"></a>nx_secure_x509_crl_revocation_check

Kontrollera X.509-certifikat mot en agen lista över återkallade certifikat (CRL)

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Description

Den här tjänsten tar en DER-kodad lista över återkallade certifikat och söker efter ett specifikt certifikat i listan. Utfärdaren av listan över återkallade certifikat verifieras mot ett tillhandahållet certifikatarkiv, CRL-utfärdaren verifieras att vara samma som den för certifikatet som kontrolleras och serienumret för certifikatet i fråga används för att söka i listan över återkallade certifikat. Om utfärdarna matchar, signaturen checkar ut och certifikatet **inte finns** i listan, lyckas anropet. Alla andra fall gör att ett fel returneras.

### <a name="parameters"></a>Parametrar

- **crl_data** Pekare till en DER-kodad CRL.
- **crl_length** Längd i byte för CRL-data.
- **store** Pekare till ett X.509-certifikatarkiv.
- **certificate_ptr** Pekare till en X.509-certifikatinstans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad validering av att certifikatet inte återkallades.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) det går inte att hitta certifikatet för CRL-utfärdaren.
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Det går inte att hitta certifikatets certifikatutfärdare.
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) CRL ASN.1 innehöll ett ogiltigt längdfält.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** Listan över återkallade certifikat innehöll ogiltig ASN.1.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Verifieringen av certifikatkedjan misslyckades.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL och certifikatutfärdare matchade inte.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) CRL-signaturen var ogiltig.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) Certifikatet som kontrolleras hittades i listan över återkallade certifikat och återkallas därför.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_common_name_dns_check

## <a name="nx_secure_x509_dns_name_initialize"></a>nx_secure_x509_dns_name_initialize

Initiera en X.509 DNS-namnstruktur

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Description

Den här tjänsten initierar ett X.509 DNS-namn för användning med vissa API-tjänster som kräver ett visst namnformat. Till exempel *förväntar nx_secure_tls_sni_extension_parse tjänsten* ett NX_SECURE_X509_DNS_NAME-objekt för att matcha namnet som tillhandahålls av en fjärrvärd i Servernamnindikator-tillägget under TLS-handskakningen. Ett DNS-namn är helt enkelt en teckensträng med en längd – den maximala tillåtna längden för ett DNS-namn (och storleken på den interna bufferten i NX_SECURE_X509_DNS_NAME) styrs av makro-NX_SECURE_X509_DNS_NAME_MAX (standardvärdet är 100 byte).

### <a name="parameters"></a>Parametrar

- **dns_name** DNS-namnstruktur som ska initieras.
- **name_string** DNS-namnsträngsdata.
- **längd** Namnsträngens längd.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering.
- **NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) Den angivna namnsträngen överskred NX_SECURE_X509_DNS_NAME_MAX.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_session_sni_extension_set

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a>nx_secure_x509_extended_key_usage_extension_parse

Hitta och parsa ett utökat X.509-nyckelanvändningstillägg i ett X.509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Description

Den här tjänsten är avsedd att anropas inifrån ett återanrop för certifikatverifiering *(se nx_secure_tls_session_certificate_callback_set).* Den söker efter ett specifikt utökat nyckelanvändnings-OID i ett X.509-certifikat och returnerar om OID:t finns. Parametern key_usage är en heltalsmappning av OID:erna som används internt av NetX Secure X.509 och TLS för att undvika att OID-strängar med variabel längd anges som parametrar.

Relevanta OID:er för tillägget för utökad nyckelanvändning anges i tabellen nedan. En typisk TLS-klientimplementering som vill kontrollera användningen av utökad nyckel i ett mottaget TLS-servercertifikat skulle kontrollera om OID-NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH finns. Om tillägget finns men inte OID:n skulle certifikatet anses vara ogiltigt för att identifiera värden som en TLS-server och återanropet av certifikatverifieringen bör returnera ett fel. Om själva tillägget saknas är det upp till programmet om TLS-handskakningen ska fortsätta eller inte.

I återanropet för certifikatverifiering är felreturkoden NX_SECURE_X509_KEY_USAGE_ERROR reserverad för programanvändning. Om det uppstår ett fel vid kontroll av nyckelanvändning kan det här värdet returneras från återanropet för att ange orsaken till felet.

| NetX Secure Identifier                                | OID-värde         | Description                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | Certifikatet kan användas för att identifiera en TLS-server |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | Certifikatet kan användas för att identifiera en TLS-klient |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | Certifikatet kan användas för att signera kod             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | Certifikatet kan användas för att signera e-post           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | Certifikatet kan användas för att signera tidsstämplar       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | Certifikatet kan användas för att signera OCSP-svar   |

OID:er och mappningar för utökat nyckelanvändningstillägg för X.509

### <a name="parameters"></a>Parametrar

- **certifikat** Pekare till certifikatet som verifieras.
- **key_usage** OID-heltalsmappning från tabellen ovan.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Angivet nyckelanvändnings-OID hittades.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1-tagg för flera byte som påträffades (certifikat stöds inte).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1-fält (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Ogiltig ASN.1-taggklass påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Ogiltigt tillägg påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Tillägget för utökad nyckelanvändning hittades inte i det angivna certifikatet.
- **NX_PTR_ERROR** (0x07) Ogiltig certifikat pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find

## <a name="nx_secure_x509_extension_find"></a>nx_secure_x509_extension_find

Hitta och returnera ett X.509-tillägg i ett X.509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Description

Den här tjänsten är avsedd att anropas inifrån ett återanrop för *certifikatverifiering* (se nx_secure_tls_session_certificate_callback_set) och är en avancerad X.509-tjänst.

Funktionen söker efter ett visst tillägg i ett X.509-certifikat baserat på ett OID och returnerar om OID:t finns, tillsammans med en struktur som innehåller referenser till relevanta råtilläggsdata. Parametern extension_id är en heltalsmappning av OID:erna som används internt av NetX Secure X.509 och TLS för att undvika att OID-strängar med variabel längd anges som parametrar.

Hjälpfunktionerna som tillhandahålls för specifika tillägg (till exempel *nx_secure_x509_key_usage_extension_parse*) anropar nx_secure_x509_extension_find internt för att hämta tilläggsdata.

Relevanta OID:er för kända X.509-tillägg anges i tabellen nedan.

Den NX_SECURE_X509_EXTENSION strukturen innehåller pekare till X.509-certifikatet som gör att hjälpfunktioner som *nx_secure_x509_key_usage_extension_parse snabbt* kan avkoda råtillägget DER-kodade ASN.1-data.

Information om specifika tillägg finns i RFC 5280 (X.509-specifikation) eller referensen för lämpliga hjälpfunktioner om det finns.

Den aktuella versionen av NetX Secure X.509 har begränsat stöd för X.509-tillägg. Fler hjälpfunktioner kommer att läggas till i framtiden.

> [!IMPORTANT]
> *Den här tjänsten är en avancerad funktion för användare som är bekanta med X.509-tillägg och DER-kodad ASN.1. Den tillhandahålls för att göra det möjligt för de användare att komma åt tillägg som NetX Secure X.509 för närvarande inte tillhandahåller hjälpfunktioner för. För dessa tillägg utan hjälpfunktioner måste du parsa rå-DER-kodad ASN.1 själv.*

| NetX Secure Identifier                              | OID-värde | Description                                                                    | Hjälpfunktion? |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | Katalogattribut – grundläggande informationsattribut om certifikatämne  | No               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | Används för att identifiera en specifik offentlig nyckel                                         | No               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | Innehåller information om giltiga användningsområden för certifikatets offentliga nyckel              | Yes              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | Tillhandahåller alternativa DNS-namn för att identifiera certifikatet                     | Ja<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | Tillhandahåller alternativa DNS-namn för att identifiera certifikatets utfärdare            | No               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | Innehåller grundläggande information om begränsningar för certifikatanvändning                        | No               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | Används för att begränsa certifikatnamn till specifika domäner                        | No               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | Tillhandahåller URI:er för CRL-distribution                                             | No               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | Lista över certifikatprinciper för stora PKI-system                             | No               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | Lista över certifikatprinciper för certifikatutfärdare                                                | No               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | Används för att identifiera en specifik offentlig nyckel som är associerad med en certifikatsignatur | No               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | Begränsningar för CA-princip                                                          | No               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | Ytterligare information om OID-baserad nyckelanvändning                                     | Yes              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Innehåller information om att hämta delta-CRL:er                                  | No               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | Certifikatfält för certifikatutfärdare som anger att AnyPolicy inte kan användas                  | No               |

OID:er och mappningar för X.509-tillägg

24. SubjectAltName-tillägget parsas som en del av DNS-namnkontrollen i nx_secure_x509_common_name_dns_check.

### <a name="parameters"></a>Parametrar

- **certifikat** Pekare till certifikat som verifieras.
- **tillägg** Returstruktur som innehåller pekare och längd för tilläggsdata.
- **extension_id** OID-heltalsmappning från tabellen ovan.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Angivet tilläggs-OID hittades och data returnerades.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1-tagg med flera byte (stöds inte certifikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1-fält påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Ogiltig ASN.1-taggklass påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Ogiltigt tillägg påträffades
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Det angivna tilläggs-OID:t hittades inte i det angivna certifikatet.
- **NX_PTR_ERROR** (0x07) Ogiltigt certifikat eller tilläggspekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extended_key_usage_extension_parse

## <a name="nx_secure_x509_key_usage_extension_parse"></a>nx_secure_x509_key_usage_extension_parse

Hitta och parsa ett X.509-nyckelanvändningstillägg i ett X.509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Description

Den här tjänsten är avsedd att anropas inifrån ett återanrop för certifikatverifiering *(se nx_secure_tls_session_certificate_callback_set).* Den söker efter nyckelanvändningstillägget och returnerar bitfältet Nyckelanvändning i parametern "bitfield".

Bitarna, som definieras av X.509-specifikationen (RFC 5280) anges i tabellen nedan. Ett bitvis AND med lämplig bitmask (och kontroll av icke-noll) ger värdet för varje bit.

Observera att DER-kodningen för bitfältet eliminerar extra nollor, så den faktiska positionen för bitarna i rådatacertifikatdata skiljer sig förmodligen från deras positioner i det avkodade bitfältet. De angivna bitmaskerna är endast avsedda att användas på det avkodade bitfält som *returneras av nx_secure_x509_key_usage_extension_parse* och inte med råa DER-kodade certifikatdata.

I återanropet för certifikatverifiering är felreturkoden NX_SECURE_X509_KEY_USAGE_ERROR reserverad för programanvändning. Om det uppstår ett fel vid kontroll av nyckelanvändning kan det här värdet returneras från återanropet för att ange orsaken till felet.

| NetX Secure Identifier                            | Bitposition | Description                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | Certifikatet kan användas för digitala signaturer                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | Certifikat kan användas för att verifiera andra digitala signaturer än de för certifikat och listor över återkallade certifikat                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | Certifikatet kan användas för att kryptera symmetriska nycklar (nyckeltransport)                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | Certifikatet kan användas för att direkt kryptera rådata för användare (ovanligt)                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | Certifikatet kan användas för nyckelavtal (som med Diffie-Hellman)                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | Certifikatet kan användas för att signera och verifiera andra certifikat (certifikatet är ett CA- eller ICA-certifikat).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | Certifikatets offentliga nyckel används för att verifiera signaturer på listor över återkallade certifikat                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | Används med Nyckelavtalsbit (bit 4) – när det här anges kan certifikatnyckeln endast användas för kryptering under nyckelavtalet. Odefinierat om Nyckelavtalsbit inte har angetts. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | Används med nyckelavtalsbit (bit 4) – när den har angetts kan certifikatnyckeln endast användas för att dekryptera under nyckelavtalet. Odefinierat om Nyckelavtalsbit inte har angetts. |

Bitmasker och värden för X.509-nyckelanvändningstillägg

### <a name="parameters"></a>Parametrar

- **certifikat** Pekare till certifikat som verifieras.
- **bitfield** Returnera hela bitfältet från tillägget.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Nyckelanvändningstillägg hittades och bitfält returnerades.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1-tagg med flera byte (stöds inte certifikat).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1-fält påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Ogiltig ASN.1-taggklass påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Ogiltigt tillägg påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)Nyckelanvändningstillägget hittades inte i det angivna certifikatet.
- **NX_PTR_ERROR** (0x07) Ogiltigt certifikat eller pekare för bitfält.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_extended_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find
