---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX Secure Services
description: Det här kapitlet innehåller en beskrivning av alla NetX säkra tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826949"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>Kapitel 4 – Beskrivning av Azure återställnings tider NetX Secure Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX-säkra tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "returnera värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_SECURE_DISABLE_ERROR_CHECKING** makro som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - Utför self_test på krypterings metoderna
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - Beräknar hash-värde med user_supplied hash-funktion
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - Ange det aktiva identitets certifikatet för en NetX Secure TLS-session
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - Ange en Pre_Shared nyckel för en NetX Secure TLS-klientsession
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - Initierar NetX Secure TLS-modulen]
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - Lägg till ett lokalt certifikat till NetX Secure TLS-session
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - Hitta ett lokalt certifikat i en NetX Secure TLS-session efter eget namn
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - Ta bort det lokala certifikatet från NetX Secure TLS-sessionen
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - Beräkna storleken på kryptografiska metadata för en NetX säker TLS-session
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - Allokera ett paket för en NetX säker TLS-session
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - Lägga till en Pre_Shared nyckel till en NetX Secure TLS-session
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - Allokera utrymme för certifikatet som tillhandahålls av en fjärran sluten TLS-värd
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - Allokera utrymme för alla certifikat som tillhandahålls av en fjärran sluten TLS-värd
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - Ledigt utrymme allokerat för inkommande certifikat
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - Lägg till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - Hitta ett certifikat med en numerisk identifierare
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - Ta bort ett lokalt Server certifikat med en numerisk identifierare
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - Konfigurera en motringning för TLS som ska användas för ytterligare certifikat validering
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-klient hand skakning
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - Aktivera client X. 509-verifiering och allokera utrymme för klient certifikat
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - Inaktivera autentisering av klient certifikat för en NetX säker TLS-session
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - Aktivera autentisering av klient certifikat för en NetX säker TLS-session
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - Skapa en NetX Secure TLS-session för säker kommunikation
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - Ta bort en NetX Secure TLS-session
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - Avsluta en aktiv NetX säker TLS-session
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - Ställ in bufferten för paket ommontering för en NetX Secure TLS-session
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - Åsidosätt standard versionen av TLS-protokollet för en NetX säker TLS-session
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - Ta emot data från en NetX Secure TLS-session
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - Tilldela ett återanrop som ska anropas i början av en omförhandling av en session
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - Starta en handhandlings hand skakning med fjärrvärden
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - Ta bort och Återställ en NetX säker TLS-session
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - Skicka data via en NetX Secure TLS-session
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-servers hand skakning
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - Parsa ett Servernamnindikator-tillägg (SNI) som tagits emot från en TLS-klient
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - Ange ett Servernamnindikator-tillägg (SNI) som ska skickas till en fjärrserver
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - Starta en NetX Secure TLS-session
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - Tilldela en timestamp-funktion till en NetX Secure TLS-session
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - Lägg till betrott certifikat i NetX Secure TLS-session
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - Ta bort betrott certifikat från NetX Secure TLS-session
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - Initiera X. 509-certifikat för NetX Secure TLS
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - Kontrol lera DNS-namn mot X. 509-certifikat
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - Kontrol lera X. 509-certifikatet mot en angiven lista över återkallade certifikat (CRL)]
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - Initiera en X. 509 DNS-namn struktur
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - Hitta och parsa ett tillägg för utökad nyckel användning i X. 509 i ett X. 509-certifikat
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - Hitta och returnera ett X. 509-tillägg i ett X. 509-certifikat
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - Hitta och parsa ett tillägg för nyckel användning i X. 509 i ett X. 509-certifikat

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

Utför självtest på krypterings metoderna

### <a name="prototype"></a>Prototyp

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten körs via de självtester som används av krypterings metod för att verifiera. Själv testet är bara tillgängligt om NetX-biblioteket har skapats med symbolen NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definierat.

För varje krypterings metod som stöds tillhandahåller självtesten fördefinierade indata och verifierade utdata matchar det fördefinierade förväntade värdet.

NetX för säker kryptering stöder följande algoritmer och nyckel storlekar:

- DES: kryptering och dekryptering
- Tredubbel DES (3DES): kryptering och dekryptering
- AES: 128-, 192-, 256-bitars nyckel storlek, kryptering och dekryptering i CBC-läge och räknar läge.
- HMAC-MD5: autentisering och hash-beräkning
- HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, autentisering och hash-beräkning
- MD5: autentisering
- Pseudo – slumpmässig funktion (PRF): PRF_HMAC_SHA1 och PRF_HMAC_SHA2-256
- RSA: 1024-, 2048-, 4096-bitars RSA-åtgärd för PowerPivot-modul
- SHA: SHA1 (96-och 160-bitars), SHA2 (256bit, 384bit, 512bit)-autentisering

Den här funktionen har inbyggda vektorer för de krypteringsalgoritmer som anges ovan. Det testar dock bara de som anges i *cipher_table* som har skickats till den här funktionen. För en TLS-session används till exempel endast ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, den här funktionen utför självtest på RSA (1024-, 2048-, 4096-bitars), AES-CBC (128-bit) och SHA1.

### <a name="parameters"></a>Parametrar

- **crypto_table** Pekare till tabellen för kryptografi som används av TLS-sessionen. Detta är samma crypto_table som skickas till **_nx_secure_tls_session_create ()-_** anropet.
- **metadata** Pekar på utrymme för området för kryptografiska metadata. .
- **metadata_size** Storlek på bufferten för metadata.

### <a name="return-values"></a>Retur värden

- **NX_SECURE_TLS_SUCCESS** (0X00) har testat de kryptografiska metoder som angetts.
- **NX_PTR_ERROR** (0X07) ogiltig struktur för kryptografisk metod
- Det gick inte att kontrol lera **NX_NOT_SUCCESSFUL** (0x43).

### <a name="allowed-from"></a>Tillåten från

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

Beräknar hash-värde med hjälp av en användardefinierad hash-funktion

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

### <a name="description"></a>Beskrivning

Den här funktionen beräknar hash-värdet för data strömmen i det angivna minnes området med hjälp av den angivna HMAC-kryptografi metoden och nyckel strängen. Compute-funktionen modul-hash är bara tillgänglig om NetX Secure Library skapas med följande symbol som definieras: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK

### <a name="parameters"></a>Parametrar

- **hmac_ptr** Pekar på den HMAC-kryptografiska metod som används för beräkning av hash-värde.
- **start_address** Start adressen för databufferten
- **end_address** Den avslutande adressen för databufferten. Observera att hash-beräkningen inte omfattar data i den här end_address.
- **nyckel** Den nyckel sträng som används i HMAC-beräkningen.
- **key_length** Nyckel strängens storlek i byte
- **metadata** Pekar på utrymmet som används av HMAC-algoritmen.
- **metadata_size** Storlek på bufferten för metadata.
- **output_buffer** Minnes platsen där hash-utdata lagras.
- **output_buffer_size** Tillgängligt utrymme för utdatabufferten i byte
- **actual_size** Returneras av funktionen som indikerar det faktiska antalet byte som skrivs till output_buffer.

### <a name="return-values"></a>Retur värden

- **0** beräknade hash-värdet.
- **1** det gick inte att beräkna hashen.

### <a name="allowed-from"></a>Tillåten från

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

Ange det aktiva identitets certifikatet för en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är avsedd att anropas inifrån en motringning för session (se nx_secure_tls_session_client_callback_set och nx_secure_tls_session_server_callback_set). När det anropas med en tidigare initierad NX_SECURE_X509_CERT-struktur, kommer certifikatet att användas i stället för standard identitets certifikatet. I de flesta fall måste certifikatet ha lagts till i det lokala arkivet (se nx_secure_tls_local_certificate_add) eller så kan TLS-handskakningen Miss lyckas.

Den här tjänsten är avsedd att tillåta TLS att stödja flera identitets certifikat. Detta är användbart för en TLS-server som hanterar flera nätverks adresser så att servern kan välja ett lämpligt certifikat för att tillhandahålla fjärrklienten beroende på klientens start punkt. För en TLS-klient kan den här rutinen användas för att ändra certifikatet som skickas till en fjärrserver vid körning när servern har identifierat sig själv i TLS-handskakningen (detta är mer sällsynt än TLS-serverns användnings fall).

Om flera certifikat kan dela samma X. 509-unika namn måste certifikaten läggas till med nx_secure_tls_server_certificate_add, vilket ger en numerisk identifierare separat från certifikatet.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en TLS-sessionsbiljett som överförts till återanropet i sessionen.
- **certifikat** Pekar på ett initierat X. 509-certifikat som ska användas för den aktuella sessionen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har slutfört tilldelningen av certifikat till sessionen.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session eller certifikat pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett kontroll block för TLS-session och anger att PSK ska användas i efterföljande TLS-klientanslutningar. PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.

I det här fallet är PSK associerat med en speciell fjärran sluten TLS-server som TLS-klienten vill kommunicera med. Det PSK-värde som anges via denna API kommer att tillhandahållas till värden för fjärr-TLS-servern under nästa TLS-handskakning.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** PSK-värdets längd.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** PSK-identitetens längd.
- **tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.
- **hint_length** Längden på tips strängen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av PSK lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten initierar NetX Secure TLS-modulen. Det måste anropas innan andra NetX-säkra tjänster kan nås.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Retur värden

Inget

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

Lägg till ett lokalt certifikat till NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en initierad NX_SECURE_X509_CERT struktur instans i det lokala arkivet i en TLS-session. Det här certifikatet kan användas av TLS-stacken för att identifiera enheten under TLS-handskakningen (om den har marker ATS som ett identitets certifikat när certifikat strukturen initierades med nx_secure_x509_certificate_initialize) eller som en utfärdare som en del av en certifikat kedja som tillhandahölls till fjärrvärden under TLS-handskakningen.

Om flera lokala certifikat med samma namn krävs kan certifikat läggas till med hjälp av *nx_secure_tls_server_certificate_add* tjänsten (se varning nedan).

Ett certifikat **krävs** för TLS-server läge.

Ett certifikat är *valfritt* för TLS-klient läge.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. Server certifikatets API använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på det 509-namn som används i X. De lokala certifikat tjänsterna är ett bekvämt alternativ till den numeriska identifieraren för program som bara använder ett enda identitets certifikat – genom att använda det egna namnet behöver programmet inte hålla koll på numeriska identifierare.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certificate_ptr** Pekar mot en initierad TLS-certifikat instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.
- **NX_INVALID_PARAMETERS** (0X4D) försökte lägga till ett ogiltigt eller duplicerat certifikat.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session eller certifikat pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten hittar ett certifikat i certifikat arkivet för den lokala enheten för en TLS-session och returnerar en pekare till NX_SECURE_X509_CERT strukturen i arkivet. Common_name-parametern och dess längd (name_length) används för att identifiera certifikatet i arkivet genom att matcha certifikatets namn för fältet X. 509 subject.

Om det finns mer än ett certifikat med samma egna namn kommer endast det första att returneras – Använd *nx_secure_tls_server_certificate_find* i stället.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. Server certifikatets API använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på det 509-namn som används i X. De lokala certifikat tjänsterna är ett bekvämt alternativ till den numeriska identifieraren för program som bara använder ett enda identitets certifikat – genom att använda det egna namnet behöver programmet inte hålla koll på numeriska identifierare.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certifikat** Returnera pekare till matchat certifikat.
- **common_name** Gemensam namn sträng som ska matchas (DNS-namn).
- **name_length** Längden på common_name sträng data.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) certifikat hittades och pekaren returnerades i "Certificate"-parametern.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Det gick inte att hitta något certifikat med det angivna nätverks namnet.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session, certifikat pekare eller gemensam namn sträng.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ta bort det lokala certifikatet från NetX Secure TLS-sessionen

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en lokal certifikat instans från en TLS-session, som är nyckelbaserad i fältet eget namn i certifikatet.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_server_certificate_add. Server certifikatets API använder en unik numerisk identifierare för varje certifikat och nx_secure_tls_local_certificate_add index baserat på det 509-namn som används i X. De lokala certifikat tjänsterna är ett bekvämt alternativ till den numeriska identifieraren för program som bara använder ett enda identitets certifikat – genom att använda det egna namnet behöver programmet inte hålla koll på numeriska identifierare.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **common_name** Värdet för eget namn för det certifikat som ska tas bort.
- **common_name_length** Längden på den gemensamma namn strängen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.
- Det gick inte att hitta **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** -certifikat (0x119).

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Beräkna storleken på kryptografiska metadata för en NetX säker TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten beräknar och returnerar storleken på de kryptografiska metadata som behövs för en viss TLS-session och TLS-kryptografisk tabell (se avsnittet "initiera TLS med kryptografiska metoder" för mer information om tabellen för kryptografi kryptering).

Den här tjänsten ska anropas med önskad kryptografiska tabell för att beräkna storleken på den metadata-buffert som överfördes till nx_secure_tls_session_create.

### <a name="parameters"></a>Parametrar

- **crypto_table** Pekar till en fullständig NetX Secure TLS-kryptografi tabell.
- **metadata_size** Resultatet av storleks beräkningen i byte.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) utförde beräkningen av metadata-storlek.
- **NX_PTR_ERROR** (0X07) ogiltig-pekare för kryptografi tabell eller RETUR storlek.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Beräkna hash-värdet för NetX säkra biblioteks rutiner

### <a name="prototype"></a>Prototyp

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar NetX Secure TLS-modulen. Det måste anropas innan andra NetX-säkra tjänster kan nås.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-values"></a>Retur värden

Inget

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Se även

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

Allokera ett paket för en NetX säker TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar en NX_PACKET för den angivna aktiva TLS-sessionen från den angivna NX_PACKET_POOL. Den här tjänsten ska anropas av programmet för att allokera data paket som ska skickas via en TLS-anslutning. TLS-sessionen måste initieras innan den här tjänsten anropas.

Det allokerade paketet initieras korrekt så att TLS-sidhuvudet och sid fots data kan läggas till efter att paket data har fyllts i. Beteendet är annars identiskt med *nx_packet_allocate*.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **pool_ptr** Pekar till en NX_PACKET_POOL som paketet ska allokeras från.
- **packet_ptr** Utmatnings pekare till det nyligen allokerade paketet.
- **wait_option** Uppehålls alternativ för paket tilldelning.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket tilldelningen lyckades.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) den underliggande paket tilldelningen misslyckades.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Lägga till en i förväg delad nyckel till en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en i förväg delad nyckel (PSK), dess identitets sträng och ett identitets tips till ett kontroll block för TLS-session. PSK används i stället för ett digitalt certifikat när PSK-krypteringssviter är aktiverade och används.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **pre_shared_key** Det faktiska PSK-värdet.
- **psk_length** PSK-värdets längd.
- **psk_identity** En sträng som används för att identifiera det här PSK-värdet.
- **identity_length** PSK-identitetens längd.
- **tips** En sträng som används för att ange vilken grupp av PSKs som ska väljas på en TLS-server.
- **hint_length** Längden på tips strängen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av PSK lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) kan inte lägga till en annan PSK.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Allokera utrymme för certifikatet som tillhandahålls av en fjärran sluten TLS-värd

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en oinitierad NX_SECURE_X509_CERT struktur instans till en TLS-session för att allokera utrymme för certifikat som tillhandahålls av en fjärrvärd under en TLS-session. Fjärrcertifikatets data parsas av NetX Secure TLS och den informationen används för att fylla i den certifikat struktur instans som anges för den här funktionen. Certifikat som läggs till på det här sättet placeras i en länkad lista.

Om det är förväntat att fjärrvärden ska tillhandahålla flera certifikat, ska den här funktionen anropas flera gånger för att allokera utrymme för alla certifikat. De ytterligare certifikaten läggs till i slutet av den länkade listan över certifikat.

Om ett fjärrcertifikat inte allokeras kan ett klient läge för TLS Miss lyckas under TLS-handskakningen om inte en i förväg delad nyckel (PSK) ciphersuite används.

Parametern *raw_certificate_buffer* pekar på utrymmet som allokerats för att lagra det inkommande Fjärrcertifikatet. Typiska certifikat med RSA-nycklar på 2048-bitar som använder SHA-256 för signaturer är i intervallet 1000-2000 byte. Bufferten bör vara tillräckligt stor för att minst innehålla den storlek som används, men beroende på vilka fjärrcertifikaten kan vara betydligt mindre eller större. Observera att om bufferten är för liten för att rymma det inkommande certifikatet, avslutas TLS-handskakningen med ett fel.

För TLS-serverinställningar behövs endast en tilldelning av fjärrcertifikat om autentisering av klient certifikat är aktiverat.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certificate_ptr** Pekar mot en oinitierad X. 509-certifikat instans.
- **raw_certificate_buffer** Pekar på en buffert för att lagra det icke-parsade certifikatet som togs emot från fjärrvärden.
- **raw_buffer_size** Storlek på den råa certifikatets buffert.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) allokering av certifikat har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0X12D) den angivna bufferten var för liten.
- **NX_INVALID_PARAMETERS** (0X4D) försökte lägga till ett ogiltigt certifikat.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Allokera utrymme för alla certifikat som tillhandahålls av en fjärran sluten TLS-värd

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar utrymme för att bearbeta inkommande certifikat kedjor från fjärranslutna Server värdar för att utföra X. 509-autentisering och verifiering i en TLS-klient instans. För TLS-serverinställningar behövs endast fjärrtilldelning av certifikat om klienten X. 509-certifikatautentisering är aktive rad – för TLS Server-instanser bör tjänsten *nx_secure_tls_session_x509_client_verify_configure* användas i stället.

Om du inte allokerar fjärrcertifikat, Miss lyckas TLS-klientens läge under TLS-handskakningen om inte en i förväg delad nyckel (PSK) ciphersuite används.

*Certificate_buffer* -parametern pekar på utrymme som allokerats för att lagra inkommande fjärrcertifikat och kontroll block som behövs för dessa certifikat. Bufferten kommer att divideras med antalet certifikat (*certs_number*) med samma del som varje certifikat. Parametern *buffer_size*  anger buffertens storlek. Utrymmet som behövs hittar du i följande formel:

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Typiska certifikat med RSA-nycklar på 2048-bitar som använder SHA-256 för signaturer är i intervallet 1000-2000 byte. Bufferten bör vara tillräckligt stor för att minst innehålla den storlek som används för varje certifikat, men beroende på fjärrdatorns certifikat kan vara betydligt mindre eller större. Observera att om bufferten är för liten för att rymma det inkommande certifikatet, avslutas TLS-handskakningen med ett fel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certs_number** Antal certifikat som ska allokeras från den angivna bufferten.
- **certificate_buffer** Pekar till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.
- **buffer_size** Storlek på certifikatets buffert.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) allokering av certifikat har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session eller buffert pekare.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0X12D) den angivna bufferten var för liten.
- **NX_INVALID_PARAMETERS** (0X4D) bufferten var för liten för att rymma det önskade antalet certifikat.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten används för att frigöra alla certifikat-buffertar som tilldelas till en viss TLS-session genom att nx_secure_tls_remote_certificate_allocated genom att returnera dem till det lediga certifikat utrymmet i den aktuella sessionen. Detta kan vara nödvändigt om ett program återanvänder ett TLS-sessionsobjekt utan att ta bort det och återskapa det med nx_secure_tls_session_delete och nx_secure_tls_session_create.

Observera att det fjärranslutna certifikat utrymmet återställs automatiskt när TLS-sessionen återställs i nx_secure_tls_session_end så att de flesta program inte behöver anropa den här tjänsten.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.
- **NX_INVALID_PARAMETERS** (0X4D) internt fel – certifikat arkivet är antagligen skadat.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Lägg till ett certifikat specifikt för TLS-servrar med hjälp av en numerisk identifierare

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten används för att lägga till ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med en numerisk identifierare i stället för att indexera lagret med hjälp av X. 509-ämnet (eget namn) i certifikatet. Den numeriska identifieraren är separat från certifikatet och gör det möjligt att lägga till flera certifikat som identitets certifikat till en TLS-server, samt tillåta att flera certifikat med samma eget namn läggs till i samma lokala TLS-session. Samma tjänst kan användas för klient certifikat, men det är sällsynt att en TLS-klient har flera identitets certifikat.

Parametern cert_id är ett positivt heltal som inte är noll som tilldelats av programmet. Det faktiska värdet spelar ingen roll (förutom noll) men det måste vara unikt i arkivet för den angivna TLS-sessionen. Cert_id-värdet kan användas för att söka efter och ta bort certifikat från det lokala arkivet med nx_secure_tls_server_certificate_find respektive nx_secure_tls_server_certificate_remove.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. Nx_secure_tls_server_certificate_add-API: et använder en unik numerisk identifierare för varje certifikat, och det lokala Certificate Services-indexet baserat på det X. 509-delade namnet. Server certifikat tjänsterna tillåter att flera certifikat med delade data (särskilt nätverks namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certifikat** Pekar till en tidigare initierad X. 509-certifikat instans.
- **cert_id** Positivt, icke-noll, relativt unikt certifikat-ID-nummer.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig TLS session orcertificate-pekare.
- **NX_SECURE_TLS_CERT_ID_INVALID** (0X138) det tillhandahållna certifikat-ID: t hade ett ogiltigt värde (troligen 0).
- **NX_SECURE_TLS_CERT_ID_DUPLICATE** (0X139) det tillhandahållna certifikat-ID: t fanns redan i det lokala arkivet.
- **NX_INVALID_PARAMETERS (0X4D)** Internt fel – certifikat arkivet är antagligen skadat.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hitta ett certifikat med en numerisk identifierare

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten används för att hitta ett certifikat i en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med en numerisk identifierare i stället för att indexera lagret med hjälp av X. 509-ämnet (eget namn) i certifikatet.

Parametern cert_id är ett positivt heltal som inte är noll och som tilldelas av programmet när certifikatet läggs till i det lokala arkivet för TLS-sessionen med hjälp av nx_secure_tls_server_certificate_add.

> [!IMPORTANT]
> *Detta API bör inte användas med samma TLS-session när du använder nx_secure_tls_local_certificate_add. Nx_secure_tls_server_certificate_add-API: et använder en unik numerisk identifierare för varje certifikat, och det lokala Certificate Services-indexet baserat på det X. 509-delade namnet. Server certifikat tjänsterna tillåter att flera certifikat med delade data (särskilt nätverks namn) finns i samma lokala arkiv – detta är användbart för en server med flera identiteter.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certifikat** Pekar på en X. 509-certifikat pekare för att returnera en referens till det påträffade certifikatet.
- **cert_id** Positivt värde för certifikat-ID som inte är noll.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session eller certifikat pekare.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) det angivna certifikat-ID: t matchade inte några i det lokala arkivet i den angivna TLS-sessionen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ta bort ett lokalt Server certifikat med en numerisk identifierare

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten används för att ta bort ett certifikat från en TLS-sessions lokala arkiv (se nx_secure_tls_local_certificate_add) med en numerisk identifierare i stället för att indexera lagret med hjälp av X. 509-ämnet (eget namn) i certifikatet.

Parametern cert_id är ett positivt heltal som inte är noll och som tilldelas av programmet när certifikatet läggs till i det lokala arkivet för TLS-sessionen med hjälp av nx_secure_tls_server_certificate_add.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **cert_id** Positivt värde för certifikat-ID som inte är noll.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) det angivna certifikat-ID: t matchade inte några i det lokala arkivet i den angivna TLS-sessionen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hämta TLS-avisering svärdet och nivån som skickas av den fjärranslutna värden

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Beskrivning

Den här tjänsten används för att hämta TLS-aviserings nivån och värdet när fjärrvärden skickar en avisering som svar på ett problem eller fel.

Värdena för parametrarna alert_level och alert_value är bara giltiga om den här funktionen anropas omedelbart efter ett TLS API-anrop som returnerade statusen NX_SECURE_TLS_ALERT_RECEIVED (0x114) som indikerar att en avisering togs emot från fjärrvärden.

Observera att om den lokala värd-TLS skickar en avisering, är de returnerade fel koderna mycket mer beskrivande av det faktiska felet än TLS-aviseringen, eftersom TLS-aviserings värden oavsiktligt utelämnas för att förhindra vissa typer av angrepp (t. ex. ett "utfyllnad för Oracle"-angrepp eller liknande).

Aviserings nivån har bara ett av två värden: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) eller NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2). I allmänhet får endast CloseNotify-aviseringen (som används för att visa en lyckad slut punkt till en TLS-session) en nivå av "varning", även om vissa konfigurations situationer för tillägg också kan anses vara varningar. De flesta aviseringar är "oåterkallelig" som indikerar ett potentiellt säkerhets fel och som resulterar i omedelbar avslutning av TLS-anslutningen (hand skakning eller session).

TLS-aviseringens värden definieras i TLS-rapporterna, här är listan från RFC 5246 (TLSv 1.2) som referens:

| Aviseringsnamn                     | Värde | Beskrivning                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | Inget fel, indikerar lyckad session slut                                                                                                                   |
| unexpected_message            | 10    | TLS tog emot ett oväntat eller meddelande som inte är i ordning                                                                                                           |
| bad_record_mac               | 20    | Dekryptering och/eller MAC-verifiering misslyckades                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **Föråldrad** Det gick inte att dekryptera (inaktuellt på grund av att Oracle-attacker för utfyllnad)                                                                                      |
| record_overflow               | 22    | En post som är större än den största tillåtna storleken för TLS-data har tagits emot                                                                                        |
| decompression_failure         | 30    | Ett problem påträffades vid komprimering/expandering av en TLS-post                                                                                       |
| handshake_failure             | 40    | Ett ospecificerat hand skaknings fel inträffade som inte omfattas av en annan avisering                                                                            |
| no_certificate_RESERVED      | 41    | **Föråldrad** i TLS (endast SSL)                                                                                                                                 |
| bad_certificate               | 42    | Ett certifikat som tagits emot innehöll ogiltig formatering eller signaturer                                                                                   |
| unsupported_certificate       | 43    | Ett certifikat togs emot som har en ogiltig typ (t. ex. endast signerings certifikat som används för TLS-serverautentisering)                                    |
| certificate_revoked           | 44    | Certifikat statusen (som anges av en CRL eller OCSP) indikeras som "återkallad"                                                                       |
| certificate_expired           | 45    | Det mottagna certifikatet var utanför det giltiga datum intervallet (antingen inte giltigt ännu eller har gått ut)                                                                 |
| certificate_unknown           | 46    | Vissa okända certifikat problem påträffades som inte omfattas av andra aviseringar                                                                          |
| illegal_parameter             | 47    | En del konfiguration eller förhandlat värde i TLS-handskakningen var ogiltigt eller utanför intervallet                                                                      |
| unknown_ca                    | 48    | Mottaget identitets certifikat kunde inte spåras via en certifikat kedja till ett betrott rot certifikat för certifikat utfärdare.                                              |
| access_denied                 | 49    | Anger att ett giltigt certifikat togs emot men program åtkomst kontrollen angav att certifikatet inte var giltigt för de begärda resurserna.            |
| decode_error                  | 50    | Ett fält eller värde i ett TLS-huvud eller hand skaknings meddelande låg utanför intervallet eller är ogiltigt, vilket ledde till ett fel vid avkodning av en TLS-post.                      |
| decrypt_error                 | 51    | Det gick inte att verifiera en signatur eller en färdig meddelande-hash under TLS-handskakningen.                                                                         |
| export_restriction_RESERVED  | 60    | Föråldrad i TLSv 1.2                                                                                                                                        |
| protocol_version              | 70    | Den TLS-protokollversion som förhandlas under hand skakningen känns igen men stöds inte (t. ex. TLSv 1.0 har presenter ATS men inte Aktiver ATS).                       |
| insufficient_security         | 71    | Skickas varje gång en hand skakning Miss lyckas på grund av att det inte finns några säkra chiffer (till exempel att nyckel storleken är för liten för program kraven)                                |
| internal_error                | 80    | Vissa icke-TLS-fel (t. ex. problem med minnesallokering, program problem) uppstod i en bruten TLS-session.                                         |
| user_canceled                 | 90    | Returneras om TLS-sessionen avbryts av en användare eller ett program innan hand skakningen är slutförd (liknar CloseNotify).                                 |
| no_renegotiation              | 100   | Indiates att den fjärranslutna värddatorn inte kan utföra en TLS renegotiation-handskakning som svar på en begäran om omförhandling.                                 |
| unsupported_extension         | 110   | Skickas om en TLS-klient tar emot en ServerHello som innehåller tillägg som inte uttryckligen efterfrågats i den inledande sitt hälsnings (vilket indikerar att servern har problem). |

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **alert_level** Returnera nivån för den mottagna aviseringen (varning eller allvarligt).
- **alert_value** Returnera värdet för den mottagna aviseringen (se tabellen).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Konfigurera en motringning för TLS som ska användas för ytterligare certifikat validering

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en-funktions pekare till en TLS-session som TLS kommer att anropa när ett certifikat tas emot från en fjärrvärd, så att programmet kan utföra verifierings kontroller, till exempel DNS-validering, certifikat återkallning och tillämpning av certifikat principer.

NetX Secure TLS utför grundläggande X. 509-sökvägar på certifikatet innan återanropet anropas för att säkerställa att certifikatet kan spåras till ett certifikat i det betrodda TLS-certifikatarkivet, men alla andra verifieringar hanteras av återanropet.

Återanropet innehåller TLS-sessionens pekare och en pekare till fjärrvärdets identitets certifikat (löv i certifikat kedjan). Återanropet ska returnera NX_SUCCESS om all verifiering lyckas, annars bör den returnera en felkod som indikerar verifierings felet. Ett annat värde än NX_SUCCESS gör att TLS-handskakningen avbryts omedelbart.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **func_ptr** Pekar mot funktionen motringning för certifikat validering.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) allokering av funktions pekare.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-klient hand skakning

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en-funktions pekare till en TLS-session som TLS kommer att anropa när en TLS-klients hand skakning har tagit emot ett ServerHelloDone-meddelande. Funktionen motringning gör att ett program kan bearbeta alla TLS-tillägg från det mottagna ServerHello-meddelandet som kräver indatamängds-eller besluts fattande.

Återanropet körs med inaktive ring av TLS-sessionens kontroll block och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt. Matrisen med tilläggs objekt är avsedd att skickas till en hjälp funktion som söker efter och tolkar ett särskilt tillägg. För närvarande finns det inga specifika tillägg som stöds i NetX säkra som kräver indataport av TLS-klienten, men motringningen är tillgänglig för programkonstruktörer för att hantera anpassade eller nya tillägg som kan bli tillgängliga. En exempel hjälp funktion som analyserar TLS-tillägg som finns i Hello-meddelanden finns *nx_secure_tls_session_sni_extension_parse*.

Klient återanrop kan också användas för att välja det aktiva identitets certifikatet med *nx_secure_tls_active_certificate_set* för TLS-klienten i händelse av att fjärrservern har begärt ett certifikat och angett information för att tillåta TLS-klienten att välja ett särskilt certifikat. Mer information finns i referensen för nx_secure_tls_active_certificate_set.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **func_ptr** Pekar mot funktionen motringning i TLS-klienten.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) allokering av funktions pekare.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Aktivera client X. 509-verifiering och allokera utrymme för klient certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar den valfria klientautentisering för X. 509 för en TLS-serverinstans. Den allokerar också utrymmet som krävs för att bearbeta inkommande certifikat kedjor från den fjärranslutna klient värden. De certifikat som anges av fjärrklienten verifieras mot betrodda certifikat för TLS-serverinstansen, tilldelade till tjänsten *nx_secure_tls_trusted_certificate_add.*

För TLS-klientcertifikat krävs fjärrtilldelning av certifikat och tjänsten *nx_secure_tls_remote_certificate_buffer_allocate* ska användas i stället. Att aktivera X. 509-klientautentisering på en TLS-klientsession har ingen påverkan.

*Certificate_buffer* -parametern pekar på utrymme som allokerats för att lagra inkommande fjärrcertifikat och kontroll block som behövs för dessa certifikat. Bufferten kommer att divideras med antalet certifikat (*certs_number*) med samma del som varje certifikat. Parametern *buffer_size* anger buffertens storlek. Utrymmet som behövs hittar du i följande formel:

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Typiska certifikat med RSA-nycklar på 2048-bitar som använder SHA-256 för signaturer är i intervallet 1000-2000 byte. Bufferten bör vara tillräckligt stor för att minst innehålla den storlek som används för varje certifikat, men beroende på fjärrdatorns certifikat kan vara betydligt mindre eller större. Observera att om bufferten är för liten för att rymma det inkommande certifikatet, avslutas TLS-handskakningen med ett fel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certs_number** Antal certifikat som ska allokeras från den angivna bufferten.
- **certificate_buffer** Pekar till en buffert för att lagra certifikat som tagits emot från en fjärrvärd.
- **buffer_size** Storlek på certifikatets buffert.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) allokering av certifikat har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session eller buffert pekare.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0X12D) den angivna bufferten var för liten.
- **NX_INVALID_PARAMETERS** (0X4D) bufferten var för liten för att rymma det önskade antalet certifikat.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Inaktivera autentisering av klient certifikat för en NetX säker TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar autentisering av klient certifikat för en angiven TLS-session. Se nx_secure_tls_session_client_verify_enable för mer information.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) status ändring har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Aktivera autentisering av klient certifikat för en NetX säker TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar autentisering av klient certifikat för en angiven TLS-session. Om du aktiverar autentisering av klient certifikat för en TLS-serverinstans kan TLS-servern begära ett certifikat från valfri fjärran sluten TLS-klient under den första TLS-handskakningen. Certifikatet som togs emot från fjärr-TLS-klienten åtföljs av ett CertificateVerify-meddelande som TLS-servern använder för att kontrol lera att klienten äger certifikatet (har åtkomst till den privata nyckel som är kopplad till certifikatet).

Om det tillhandahållna certifikatet kan verifieras och spåras tillbaka till ett certifikat i det betrodda certifikat arkivet i TLS-servern via en X. 509-certifikat kedja, autentiseras fjärr-TLS-klienten och hand skakningen fortsätter. Om det uppstår fel vid bearbetning av certifikatet eller CertificateVerify-meddelandet slutar TLS-handskakningen med ett fel.

> [!NOTE]
> *TLS-servern måste ha minst ett certifikat i det betrodda arkivet som har lagts till med nx_secure_tls_trusted_certificate_add eller autentiseringen fungerar alltid.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) status ändring har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en NX_SECURE_TLS_SESSION struktur instans som ska användas för att upprätta säker TLS-kommunikation över en nätverks anslutning.

Metoden tar ett NX_SECURE_TLS_CRYPTO-objekt som är ifyllt med de tillgängliga kryptografiska metoder som ska användas för TLS. *Encryption_metadata_area* pekar på en buffert som tilldelats för användning av TLS för "metadata" som används av kryptografiska metoder i NX_SECURE_TLS_CRYPTOs tabellen för beräkningar. Tabellens storlek kan fastställas med hjälp av nx_secure_tls_metadata_size_calculate tjänsten. Mer information finns i avsnittet "kryptografi i NetX Secure TLS" i kapitel 3.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **cipher_table** Pekare till TLS-kryptografiska metoder.
- **encryption_metadata_area** Pekar på plats för kryptografiska metadata.
- **encryption_metadata_size** Storlek på bufferten för metadata.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.
- **NX_INVALID_PARAMETERS** (0X4D) metadata-bufferten var för liten för de metoder som angavs.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) en obligatorisk cipher-metod för den aktiverade versionen av TLS angavs inte i tabellen Cipher.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en TLS-session som representeras av en NX_SECURE_TLS_SESSIONs struktur instans och frigör alla system resurser som ägs av den sessionen.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Avsluta en aktiv NetX säker TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten avslutar en TLS-session som representeras av en NX_SECURE_TLS_SESSION-struktur instans genom att skicka TLS CloseNotify-meddelandet till fjärrvärden. Tjänsten väntar sedan på att fjärrvärden ska svara med sitt eget CloseNotify-meddelande.

Om fjärrvärden inte skickar ett CloseNotify-meddelande, betraktas TLS som ett fel och en möjlig säkerhets överträdelse, så det är viktigt att kontrol lera returvärdet för en säker anslutning. Parametern **wait_option** kan användas för att styra hur länge tjänsten ska vänta på svaret innan kontrollen återgår till anrops tråden.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **wait_option** Anger hur länge tjänsten ska vänta på svar från den fjärranslutna värden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) fick inget svar från fjärrvärden innan tids gränsen nåddes.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0X111) kunde inte allokera ett paket för att skicka CloseNotify-meddelandet.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) kunde inte skicka CloseNotify-meddelandet via TCP-socketen.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ställ in bufferten för paket ommontering för en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten associerar en paket omassembly-buffert till en TLS-session. För att dekryptera och tolka inkommande TLS-poster måste data i varje post monteras från de underliggande TCP-paketen. TLS-poster kan vara upp till 16 KB i storlek (även om de ofta är mycket mindre) så att de inte får plats i ett enda TCP-paket.

Om du vet att det inkommande meddelandets storlek är mindre än TLS-postgränsen på 16 KB kan buffertstorleken bli mindre, men för att hantera okända inkommande data måste bufferten göras så stor som möjligt. Om en inkommande post är större än den angivna bufferten avslutas TLS-sessionen med ett fel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **buffer_ptr** Pekare för att buffra för TLS som ska användas för paket ommontering.
- **buffer_size** Storlek på angiven buffert i byte.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_INVALID_PARAMETERS** (0X4D) ogiltig buffert eller TLS-session pekare.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Åsidosätt standard versionen av TLS-protokollet för en NetX säker TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Beskrivning

Den här tjänsten åsidosätter standard versionen (nyaste) TLS-protokollet som används av en viss session. Detta gör att NetX Secure TLS kan använda en äldre version av TLS för en speciell TLS-session utan att inaktivera nya TLS-versioner vid kompilering. Detta kan vara användbart i program som kan behöva kommunicera med en äldre värd som inte stöder den senaste versionen av TLS.

> [!IMPORTANT]
> *Från och med version 5.11 SP3 stöder NetX Secure TLS RFC 7507 (se OBS! nedan) och alla åsidosättningar till en äldre version med detta API leder till att en återställnings SCSV skickas i sitt hälsnings. Om servern har stöd för en nyare version av TLS och återställnings SCSV ingår i sitt hälsnings, kommer servern att avbryta TLS-handskakningen med en "olämplig återställning"-avisering. SCSV skickas endast när den åsidosättande versionen är en äldre version av TLS än vad som är aktiverat (t. ex. om du åsidosätter versionen till TLS 1,2 kommer inga SCSV att skickas).*

Giltiga värden för parametern protocol_version är följande makron: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 och NX_SECURE_TLS_VERSION_TLS_1_2.

Makron NX_SECURE_TLS_DISABLE_TLS_1_1 och NX_SECURE_TLS_ENABLE_TLS_1_0 kan användas för att kontrol lera vilka versioner av TLS som kompileras i programmet. TLS version 1,2 är alltid aktiverat.

Observera att om fjärrvärden inte stöder den angivna versionen kommer anslutningen att Miss Miss läge – endast den angivna åsidosättning-versionen kommer att förhandlas av NetX Secure TLS.

> [!IMPORTANT]
> RFC 7507: TLS fallback SCSV. Den här RFC introducerades för att minimera ett säkerhets problem som ursprungligen orsakades av servrar som felaktigt hanterade protokoll nedgradering, och som i stället avvisade andra giltiga sitt hälsnings-meddelanden. I ett försök att fortsätta att vara kompatibelt med dessa gamla servrar startade vissa TLS-klientprogram att nya försök misslyckades med och äldre TLS-version (t. ex. TLS 1,2 misslyckades, så testa TLS 1,1). Den här lösningen introducerade dock ett nytt problem – en angripare kan tvinga en klient att nedgradera genom att artificiellt introducera ett nätverks-eller paket fel som orsakar att Server anslutningen kraschar – även om den nya TLS-versionen stöds av servern. Genom att nedgradera till en äldre version kan angriparen utnyttja svagheter i den versionen (SSLv3<sup>21</sup> är särskilt beroende av Poodle-attacken). För att förhindra den här situationen är RFC 7507 introdued "fallback SCSV", en pseudo-ciphersuite<sup>22</sup> som skickas i sitt hälsnings som meddelar en TLS-server när en TLS-klient använder en TLS-version som inte stöds av den senaste versionen. På så sätt kan en server som har stöd för en nyare version avvisa en sitt hälsnings som innehåller återställnings-SCSV och förhindra nedgradering av angrepp.

21. NetX Secure implementerar inte SSLv3 på grund av kända allvarliga svagheter som POODLE.

22. Ett pseudo-ciphersuite-eller SCSV-värde (Signaling cipher Suite) är ett reserverat ciphersuite-nummer som används för att signalera aktiverade TLS-implementeringar om funktioner som inte är tillgängliga i äldre TLS-versioner. Återställnings SCSV och TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) är exempel.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **protocol_version** TLS-version makro för den angivna TLS-versionen som ska användas.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) status ändring har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) känd men TLS-version som inte stöds.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ogiltig protokoll version.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar emot data från den angivna aktiva TLS-sessionen och hanterar Dekrypteringen av dessa data innan den tillhandahålls till anroparen i NX_PACKET-parametern. Om inga data har ställts i kö i den angivna sessionen pausas anropet baserat på det angivna wait-alternativet.

> [!IMPORTANT]
> *Om NX_SUCCESS returneras ansvarar programmet för att släppa det mottagna paketet när det inte längre behövs.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **packet_ptr** Pekare till en tilldelad TLS-paket-pekare.
- **wait_option** Anger hur länge tjänsten ska vänta på ett paket från den fjärranslutna värden innan den returneras.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_NO_PACKET** (0X01) inga data togs emot.
- **NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett mottaget meddelande misslyckades med en hash-kontroll för autentisering.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett mottaget meddelande innehöll en okänd protokoll version i huvudet.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) tog emot en TLS-avisering från fjärrvärden.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Tilldela ett återanrop som ska anropas i början av en omförhandling av en session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en motringning till en TLS-session som ska anropas varje gång det första meddelandet i en handhandlings hand skakning tas emot från den fjärranslutna värden.

Motringningsfunktionen är avsedd som ett meddelande till programmet som en handhandlings hand skakning startar – programmet kan välja att avsluta TLS-sessionen genom att returnera ett värde som inte är noll från återanropet, vilket gör att TLS avslutar TLS-sessionen med ett fel. Om programmet vill fortsätta med omförhandlingen bör återanropet returnera NX_SUCCESS.

> [!NOTE]
> *På grund av semantiken för TLS-omförhandling anropas återanropet för NetX-säkra TLS-klienter när en HelloRequest tas emot från fjärrservern, men inte när klienten initierar omförhandlingar. På NetX säkra TLS-servrar anropas återanropet varje gång en sitt hälsnings tas emot (alla sitt hälsnings som tas emot i kontexten för en aktiv TLS-session). Det innebär att återanropet anropas om fjärrvärden eller det lokala programmet har initierat omförhandlingaret eftersom TLS-servern skickar en HelloRequest som fjärrklienten svarar på.*

NetX Secure TLS implementerar tillägget för säker omförhandling inidication från RFC 5746 för att säkerställa att hand skaknings hand skakningar inte omfattas av man-in-the-middle-attacker.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till instans av TLS-session.
- **func_ptr** Pekare till callback-funktion.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) återanrops tilldelningen lyckades.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare för callback-funktionen eller TLS-sessionen.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Starta en handhandlings hand skakning med fjärrvärden

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en *handhandlings* hand skakning med en ansluten fjärran SLUTen TLS-värd. En omförhandling består av en andra TLS-handskakning inom kontexten för en tidigare upprättad TLS-session. Var och en av de nya hand skaknings meddelandena krypteras med TLS-sessionen tills nya sessionsnycklar skapas och ChangeCipherSpec-meddelanden byts ut, då de nya nycklarna används för att kryptera alla meddelanden.

En omförhandling kan initieras när som helst när en TLS-session har upprättats. Om det görs ett försök till en omförhandling vid en TLS-handskakning eller innan en TLS-session upprättas utförs ingen åtgärd.

> [!NOTE]
> *En hel TLS-handskakning kommer att utföras när den här tjänsten anropas så att statusen slutförd och returnerad status varierar beroende på de aktuella TLS-inställningarna och session parametrarna.*

NetX Secure TLS implementerar tillägget för säker omförhandling inidication från RFC 5746 för att säkerställa att hand skaknings hand skakningar inte omfattas av man-in-the-middle-attacker.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till instans av TLS-session.
- **wait_option** Anger hur länge tjänsten ska vänta på ett paket från den fjärranslutna värden innan den returneras. Detta skickas till alla NetX-tjänster i TLS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) omförhandlingar.
- **NX_NO_PACKET** (0X01) inga data togs emot.
- **NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett mottaget meddelande misslyckades med en hash-kontroll för autentisering.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett mottaget meddelande innehöll en okänd protokoll version i huvudet.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) tog emot en TLS-avisering från fjärrvärden.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0X134) den lokala eller fjärranslutna TLS-sessionen är inaktiv, vilket gör det omöjligt att göra en omförhandling.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) angavs inte fjärrvärden antingen SCSV eller säkert omförhandlat tillägg och därför kan omförhandla inte utföras.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) den underliggande paket tilldelningen misslyckades.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ta bort och Återställ en NetX säker TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar en TLS-session och återställer statusen som om sessionen hade skapats så att ett befintligt TLS-sessionsobjekt kan återanvändas för en ny session.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_INVALID_PARAMETERS** (0X4D) ogiltig TLS-session pekare.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten skickar data i den angivna NX_PACKET, använder den angivna aktiva TLS-sessionen och hanterar krypteringen av dessa data innan den skickas till fjärrvärden. Om mottagarens senaste annonserade fönster storlek är mindre än den här begäran, pausas tjänsten, om det finns ett alternativ för den angivna vänte tiden.

> [!IMPORTANT]
> *Om ett fel returneras ska programmet inte släppa paketet efter det här anropet. På så sätt kan oväntade resultat uppstå, eftersom nätverks driv rutinen kommer att släppa paketet efter överföringen.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **packet_ptr** Pekar på ett TLS-paket som innehåller data som ska skickas.
- **wait_option** Definierar hur tjänsten fungerar om begäran är större än mottagarens fönster storlek.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_NO_PACKET** (0X01) inga data togs emot.
- **NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0X109) den underliggande TCP-socketen kunde inte skickas.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0X101) den angivna TLS-sessionen initierades inte.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Konfigurera ett motanrop för TLS som ska anropas i början av en TLS-servers hand skakning

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar en funktion pekare till en TLS-session som TLS kommer att anropa när en TLS-servers hand skakning har tagit emot ett sitt hälsnings-meddelande. Funktionen motringning gör att ett program kan bearbeta alla TLS-tillägg från det mottagna sitt hälsnings-meddelandet som kräver indatamängds-eller besluts fattande.

Återanropet körs med inaktive ring av TLS-sessionens kontroll block och en matris med NX_SECURE_TLS_HELLO_EXTENSION objekt. Matrisen med tilläggs objekt är avsedd att skickas till en hjälp funktion som söker efter och tolkar ett särskilt tillägg. En exempel hjälp funktion som analyserar TLS-tillägg som finns i Hello-meddelanden finns *nx_secure_tls_session_sni_extension_parse*.

Server återanrop kan också användas för att välja det aktiva identitets certifikatet med hjälp av *nx_secure_tls_active_certificate_set* för TLS-servern. Detta inträffar ofta som svar på ett Servernamnindikator-tillägg (SNI), vilket gör att en TLS-klient kan ange vilken server som försöker kontaktas. Mer information finns i referenserna för *nx_secure_tls_session_sni_extension_parse* och *nx_secure_tls_active_certificate_set* .

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **func_ptr** Pekar till funktionen motringning för TLS-server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) allokering av funktions pekare.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Parsa ett Servernamnindikator-tillägg (SNI) som tagits emot från en TLS-klient

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är avsedd att anropas inifrån en motringning till en TLS-server som har lagts till i en TLS-session med hjälp av nx_secure_tls_session_server_callback_set. Återanropet anropas när ett sitt hälsnings-meddelande togs emot från en fjärran sluten TLS-klient och anges en matris med tillgängliga tillägg (och antalet tillägg i matrisen). Matrisen och dess längd kan skickas direkt till den här rutinen för att avgöra om det finns ett SNI-tillägg, annars returneras NX_SECURE_TLS_EXTENSION_NOT_FOUND som anger att klienten inte valde att Provice SNI-tillägget (detta är inte ett fel).

Om SNI-tillägget hittas returneras X. 509 DNS-namnet som anges av TLS-klienten i dns_names strukturen. För närvarande tillhandahåller SNI-tillägget endast en enda DNS-namns post som kan användas av TLS-servern för att avgöra vilket identitets certifikat som ska skickas till fjärrklienten. * *

NX_SECURE_X509_DNS_NAME strukturen innehåller bara DNS-namnet som en UCHAR-sträng i fältet *nx_secure_x509_dns_name* och längden på namn strängen i *nx_secure_x509_dns_name_length*. Makro NX_SECURE_X509_DNS_NAME_MAX kontrollerar storleken på nx_secure_x509_dns_name bufferten.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **tillägg** Pekar mot en matris med TLS Hello-tillägg (från motringning till session).
- **num_extensions** Antal tillägg i matrisen (från motringning till session).
- **dns_name** Returnera DNS-namnet som anges i SNI-tillägget.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) parsning av tillägget har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig tillägg mat ris eller TLS-session pekare.
- Det gick inte att hitta **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0X136) SNI-tillägget.
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0X137) SNI Extension-formatet var ogiltigt.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

### <a name="see-also"></a>Se även

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

Ange ett Servernamnindikator-tillägg (SNI) som ska skickas till en fjärrserver

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Beskrivning

Med den här tjänsten kan ett TLS-klientcertifikat tillhandahålla ett DNS-namn för önskad server till en fjärr-TLS-server med hjälp av tillägget Servernamnindikator (SNI) TLS. SNI-tillägget gör att servern kan välja rätt identitets certifikat och parametrar baserat på klientens angivna Server inställningar. SNI-tillägget har för närvarande endast stöd för ett enda DNS-namn som ska skickas, och därför parametern för singular Name. Parametern dns_name måste initieras med *nx_secure_x509_dns_name_initialize* och kommer att innehålla klientens primära server. Om du vill ta bort tilläggets namn, anropar du bara den här tjänsten med parametervärdet "dns_name" för NX_NULL.

NX_SECURE_X509_DNS_NAME strukturen innehåller bara DNS-namnet som en UCHAR-sträng i fältet  *nx_secure_x509_dns_name* och längden på namn strängen i *nx_secure_x509_dns_name_length*. Makro NX_SECURE_X509_DNS_NAME_MAX kontrollerar storleken på nx_secure_x509_dns_name bufferten.

> [!NOTE]
> *Den här rutinen måste anropas innan nx_secure_tls_session_start anropas eller så innehåller sitt hälsnings inte SNI-tillägget.*

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **dns_name** DNS-namnet som angavs av programmet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av DNS-servernamnet är klart.
- **NX_PTR_ERROR** (0X07) ogiltigt DNS-namn eller en TLS-session.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten startar en TLS-session med det angivna TLS-sessionens kontroll block och en ansluten TCP-socket. TCP-anslutningen måste redan ha slutförts efter ett lyckat anrop till antingen nx_tcp_client_socket_connect eller nx_tcp_server_socket_accept.

Den här tjänsten avgör typen av TLS-session (klient eller server) från TCP-socketen.

Alternativet wait definierar hur tjänsten fungerar medan TLS-handskakningen pågår.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **tcp_socket_ptr** Pekar till en ansluten TCP-socket.
- **wait_option** Definierar hur tjänsten fungerar medan TLS-handskakningen pågår.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) en mottagen TLS-meddelande typ är felaktig.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) ett chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Det gick inte att bearbeta meddelande bearbetningen under TLS-handskakningen.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett inkommande meddelande misslyckades med en hash Mac-kontroll.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Det gick inte att skicka en underliggande TCP-socket.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) ett inkommande meddelande hade ett ogiltigt längd fält.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) ett inkommande ChangeCipherSpec-meddelande var felaktigt.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0X10C) ett inkommande TLS-certifikat kan inte användas för att identifiera fjärr-TLS-servern.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0X10D) den offentliga nyckel chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) fjärrvärden har angett Inga krypteringssviter som stöds av netx Secure TLS-stacken.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett MOTTAGet TLS-meddelande hade en okänd TLS-version i huvudet.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) ett MOTTAGet TLS-meddelande hade en känd men TLS-version som inte stöds i huvudet.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att tilldela en intern TLS-paket.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) fjärrvärden tillhandahöll ett ogiltigt certifikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) den fjärranslutna värden skickade en avisering som indikerar ett fel och att TLS-sessionen avslutas.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0X13B) en post i ciphersuite-tabellen hade en funktion pekare till null.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0X146) en fjärr-TLS-sitt hälsnings inkluderade reserv SCSV andattempted en versions återställning.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Tilldela en timestamp-funktion till en NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Beskrivning

Den här funktionen ställer in en funktions pekare som TLS anropar när den måste hämta den aktuella tiden, som används i olika TLS-handskaknings meddelanden och för att verifiera certifikat.

Funktionen förväntas returnera aktuellt GMT i UNIX 32-bitars format (sekunder sedan den 1 januari 1970, UTC, som ignorerar skottår) enligt sitt hälsnings-kraven i TLS RFC 5246.

Om ingen tidsstämpel-funktion har tilldelats används värdet 0 för tidsstämpeln i TLS-handskakningen och kontroll av certifikatets giltighets tid fungerar inte.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en instans av TLS-session.
- **time_func_ptr** Pekar till en funktion som returnerar aktuell tid (GMT) i UNIX 32-bitars format.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_INVALID_PARAMETERS** (0X4D) ogiltig TLS-session pekare.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Lägg till betrott certifikat i NetX Secure TLS-session

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en initierad NX_SECURE_X509_CERT struktur instans till en TLS-session. Det här certifikatet används av TLS-stacken för att verifiera certifikat som tillhandahålls av fjärrvärden under TLS-handskakningen.

Betrodda certifikat krävs för TLS-klient läge.

Betrodda certifikat krävs bara för TLS server-läge om autentisering av klient certifikat är aktiverat.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **certificate_ptr** Pekar mot en initierad TLS-certifikat instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.
- **NX_INVALID_PARAMETERS** (0X4D) försökte lägga till ett ogiltigt certifikat.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort ett betrott certifikat från en TLS-session, som anges i fältet eget namn i certifikatet.

### <a name="parameters"></a>Parametrar

- **session_ptr** Pekare till en tidigare skapad TLS-session.
- **common_name** Värdet för eget namn för det certifikat som ska tas bort.
- **common_name_length** Längden på den gemensamma namn strängen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.
- **NX_PTR_ERROR** (0X07) ogiltig TLS-session pekare.
- Det gick inte att hitta **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** -certifikat (0x119).

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Initiera X. 509-certifikat för NetX Secure TLS

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

### <a name="description"></a>Beskrivning

Den här tjänsten initierar en NX_SECURE_X509_CERT-struktur från ett binärt kodat X. 509-certifikat för användning i en TLS-session.

Certifikat data **måste** vara ett giltigt X. 509-digitalt certifikat i der-kodat binärt format. Datan kan vara en del av vilken källa som helst (t. ex. fil system, kompilerad konstant buffert osv.) så länge en UCHAR pekar på dessa data.

Parametern *raw_data_buffer* och dess storlek är valfria parametrar som anger en dedikerad buffert som certifikat data kopieras till före parsning. Om raw_data_buffer skickas som NX_NULL kommer NX_SECURE_X509_CERTs strukturen att peka direkt i certificate_data matrisen (buffer_size ignoreras i det här fallet). Om raw_data_buffer skickas som NX_NULL ska du ***inte*** ändra de data som pekar på certificate_data pekare eller certifikat bearbetningen kommer troligen att Miss lyckat!

Den privata nyckel parametern är för lokala identitets certifikat – den privata nyckeln används av servrar för att dekryptera inkommande nyckel data från en klient (krypterad med serverns offentliga nyckel) och av klienter för att verifiera sin identitet på en server när servern begär ett klient certifikat. Om du lägger till en privat nyckel med det här API: et så markeras automatiskt det associerade certifikatet som ett identitets certifikat för ett TLS-program. Vid initiering av certifikat för andra syfte (t. ex. det betrodda arkivet) ska parametern *private_key_data* skickas som NULL, *private_key_data_length* som 0 och *private_key_type* ska skickas som NX_SECURE_X509_KEY_TYPE_NONE.

Parametern *private_key_type* anger formateringen för den privata nyckeln. Om den privata nyckeln till exempel är en DER-kodad PKCS # 1-format-RSA-nyckel, ska private_key_type skickas som NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, en typ som är känd för att tolkas omedelbart och sparas för senare användning.

Private_key_type har även stöd för användardefinierade nyckel typer<sup>23</sup> för plattformar och program som har vissa nyckel format eller andra behov. En maskinvarubaserad krypterings motor kan till exempel använda ett speciellt format som inte kan tolkas av NetX-säkra program, eller så kan en privat nyckel krypteras eller representeras av en kryptografisk token som kan vara fallet med en Trusted Platform Module (TPM) eller PKCS # 11-kryptografisk maskin vara. När en användardefinierad nyckel typ används skickas nyckel data till orda Grant till lämplig kryptografisk rutin – till exempel skulle en privat RSA-nyckel skickas, utan någon parsning eller bearbetning, direkt till den RSA-kryptografiska rutinen som tillhandahålls TLS i tabellen ciphersuite. Den användardefinierade nyckel typen skickas också till den kryptografiska rutinen (vad gäller RSA, detta är "OP"-parametern).

Intervallet för användardefinierade nycklar täcker den övre halvan av ett 32-bitars heltal utan tecken från 0x0001 0000-0xFFFF FFFF. Värden som är mindre än 0x0001 0000 är reserverade för NetX-säker användning.

Användardefinierade nyckel typer är en avancerad funktion som kräver anpassade kryptografiska rutiner för att hantera rå data för den privata nyckeln. Kontakta din Express Logic-representant om du behöver den här funktionen.

### <a name="parameters"></a>Parametrar

- **certificate_ptr** Pekar mot en oinitierad X. 509-certifikat instans.
- **certificate_data** Pekare till DER-kodade X. 509 binära data.
- **raw_data_buffer** Pekare till valfri dedikerad certifikat data buffert.
- **buffer_size** Storlek på valfri dedikerad certifikat data buffert.
- **certificate_data_length** Längden på certifikatets binära data i byte.
- **private_key_data** Pekare till valfria privata nyckel data.
- **private_key_data_length** Längd på data för privata nycklar.
- **private_key_type** Nyckel typs identifierare.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) tillägget av certifikatet har slutförts.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0X112) certifikat data innehöll inte något der-kodat X. 509-certifikat.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** -certifikatet (0x10D) saknar ett offentligt nyckels chiffer som stöds av netx Secure.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0X186) privat nyckel eller certifikat innehåller ingen giltig ASN. 1-sekvens.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0X18A) den angivna privata nyckeln var inte en giltig PKCS # 1 RSA-nyckel.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0X19D) den angivna privata nyckel typen var inte användardefinierad och matchade inte någon känd typ.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
- Importerar X. 509-certifikat till NetX Secure i kapitel 3.

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

Kontrol lera DNS-namn mot X. 509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kontrollerar ett certifikats nätverks namn mot ett topp domän namn (topp domän namn) som anroparen tillhandahåller för DNS-validering av en fjärrvärd. Den här verktygs funktionen är avsedd att anropas inifrån en rutin för återanrop från certifikat validering som tillhandahålls av programmet. Namn på TOPPnivå ska vara den övre delen av den URL som används för att komma åt fjärrvärden ("." -separerad sträng före det första snedstrecket. Om det egna namnet innehåller ett jokertecken (till exempel *. example.com) matchar jokertecknet alla med samma suffix. Observera att endast det första jokertecknet (*"") som påträffas (läsning från höger till vänster) kommer att beaktas för matchning av jokertecken, till exempel ABC. *. example. com matchar *alla* namn som slutar på ". example.com".

Om det egna namnet inte matchar den angivna strängen, parsas "subjectAltName"-tillägget (om det finns i certifikatet) och alla DNSName-poster också jämförs. Om ingen av dessa poster matchar returneras ett fel.

Det är viktigt att förstå formatet på det egna namnet (och subjectAltName-poster) i förväntade certifikat. Vissa certifikat kan till exempel använda en rå IP-adress eller ett jokertecken. DNS-topp strängen måste vara formaterad så att den matchar de förväntade värdena i mottagna certifikat.

### <a name="parameters"></a>Parametrar

- **certificate_ptr** Pekare till en X. 509-certifikat instans.
- **dns_tld** Top-Level domän namn som ska jämföras med.
- **dns_tld_length** Längd på TOPPnivå sträng.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) jämförelse med eget namn eller subjectAltName.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0X195) inget matchande namn hittades.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Kontrol lera X. 509-certifikatet mot en angiven lista över återkallade certifikat (CRL)

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar en DER-kodad lista över återkallade certifikat och söker efter ett särskilt certifikat i listan. Utfärdaren av listan över återkallade certifikat verifieras mot ett angivet certifikat arkiv. CRL-utfärdaren verifieras vara densamma som för det certifikat som kontrol leras och serie numret för det aktuella certifikatet används för att söka i listan över återkallade certifikat. Om utfärdarna matchar kontrollerar signaturen och certifikatet **inte** finns i listan. anropet lyckas. Alla andra fall orsakar att ett fel returneras.

### <a name="parameters"></a>Parametrar

- **crl_data** Pekare till en DER-kodad CRL.
- **crl_length** Längd i byte för CRL-data.
- **lagra** Pekar på ett X. 509-certifikat arkiv.
- **certificate_ptr** Pekare till en X. 509-certifikat instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) verifieringen av att certifikatet inte har återkallats.
- Det gick inte att hitta **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) för CRL-utfärdarcertifikat.
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Det gick inte att hitta certifikatet för certifikat utfärdare.
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0X182) CRL ASN. 1 innehåller ett ogiltigt längd-fält.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG (0x189)** Listan över återkallade certifikat innehöll ogiltig ASN. 1.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Det gick inte att verifiera certifikat kedjan.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0X197) CRL-och certifikat utfärdare matchade inte.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) signaturen för återkallade certifikat var ogiltig.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0X199) Det gick inte att hitta det certifikat som kontrol leras i CRL och därför återkallas.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Initiera en X. 509 DNS-namn struktur

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar ett X. 509 DNS-namn för användning med vissa API-tjänster som kräver ett specifikt namn format. *Nx_secure_tls_sni_extension_parses* tjänsten förväntar sig till exempel ett NX_SECURE_X509_DNS_NAME-objekt för att matcha namnet som tillhandahålls av en fjärrvärd i servernamnindikator tillägget under TLS-handskakningen. Ett DNS-namn är helt enkelt en charater-sträng med en längd – den maximalt tillåtna längden på ett DNS-namn (och storleken på den interna bufferten i NX_SECURE_X509_DNS_NAME) styrs av makro NX_SECURE_X509_DNS_NAME_MAX (standard 100 byte).

### <a name="parameters"></a>Parametrar

- **dns_name** DNS-namn strukturen att initiera.
- **name_string** DNS-namn sträng data.
- **längd** Namn strängens längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades.
- **NX_SECURE_X509_NAME_STRING_TOO_LONG** (0X19E) den tilldelade namn strängen överskred NX_SECURE_X509_DNS_NAME_MAX.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hitta och parsa ett tillägg för utökad nyckel användning i X. 509 i ett X. 509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är avsedd att anropas inifrån ett motanrop för certifikat verifiering (se *nx_secure_tls_session_certificate_callback_set)*. Den söker efter ett angivet OID för utökad nyckel användning i ett X. 509-certifikat och returnerar om OID finns. Parametern key_usage är en heltals mappning av OID: er som används internt av NetX Secure X. 509 och TLS för att undvika att skicka OID-strängar med variabel längd som parametrar.

Relevanta OID för tillägget för utökad nyckel användning anges i tabellen nedan. En typisk TLS-klientkonfiguration som vill kontrol lera den utökade nyckel användningen i ett mottaget TLS-servercertifikat skulle kunna söka efter förekomsten av OID-NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – om tillägget finns men att OID inte är det, skulle certifikatet anses vara ogiltigt för diskfel-värden som en TLS-server och återanropet av certifikat verifiering ska returnera ett fel. Om själva tillägget saknas är det upp till programmet om du vill fortsätta med TLS-handskakningen.

I återanropet av certifikat verifieringen är felet returkod NX_SECURE_X509_KEY_USAGE_ERROR reserverat för användning av program. Om det uppstår ett fel när nyckel användningen kontrol leras kan det här värdet returneras från återanropet för att indikera orsaken till felet.

| NetX Secure Identifier                                | OID-värde         | Beskrivning                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | Certifikat kan användas för att identifiera en TLS-server |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | Certifikat kan användas för att identifiera en TLS-klient |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | Certifikat kan användas för att signera kod             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | Certifikat kan användas för att signera e-postmeddelanden           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | Certifikat kan användas för att signera tidsstämplar       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | Certifikat kan användas för att signera OCSP-svar   |

OID och mappningar för tillägg för utökad nyckel användning i X. 509

### <a name="parameters"></a>Parametrar

- **certifikat** Pekare till certifikat som verifieras.
- **key_usage** OID-heltals mappning från tabellen ovan.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) angiven OID för nyckel användning hittades.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 kod för flera byte påträffades (certifikat som inte stöds).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) ett inidentifierat ASN. 1-fält påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) ogiltig ASN. 1-tagg klass påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0X192) ogiltigt tillägg påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0X19B) Det gick inte att hitta tillägget för utökad nyckel användning i det angivna certifikatet.
- **NX_PTR_ERROR** (0X07) ogiltig certifikat pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hitta och returnera ett X. 509-tillägg i ett X. 509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är avsedd att anropas inifrån ett motanrop för certifikat verifiering (se *nx_secure_tls_session_certificate_callback_set)* och är en avancerad X. 509-tjänst.

Funktionen söker efter ett särskilt tillägg i ett X. 509-certifikat baserat på en OID och returnerar om OID finns, tillsammans med en struktur som innehåller referenser till relevanta rå Extension-data. Parametern extension_id är en heltals mappning av OID: er som används internt av NetX Secure X. 509 och TLS för att undvika att skicka OID-strängar med variabel längd som parametrar.

Hjälp funktioner som tillhandahålls för vissa tillägg (till exempel *nx_secure_x509_key_usage_extension_parse*) anropa nx_secure_x509_extension_find internt för att hämta tilläggs data.

Relevanta OID för kända X. 509-tillägg anges i tabellen nedan.

NX_SECURE_X509_EXTENSION-strukturen innehåller pekare i X. 509-certifikatet som gör att hjälp funktioner som *nx_secure_x509_key_usage_extension_parse* snabbt kan avkoda de der-kodade ASN. 1-data som finns i RAW.

Information om vissa tillägg finns i RFC 5280 (X. 509 Specification) eller referens för lämpliga hjälp funktioner om det är tillgängligt.

Den aktuella versionen av NetX Secure X. 509 har begränsat stöd för X. 509-tillägg. Fler hjälp funktioner kommer att läggas till i framtiden.

> [!IMPORTANT]
> *Den här tjänsten är en avancerad funktion för användare som är bekanta med X. 509-tillägg och DER-kodat ASN. 1. Det ges möjlighet att ge dessa användare åtkomst till tillägg som NetX Secure X. 509 inte tillhandahåller hjälp funktioner för för närvarande. För dessa tillägg utan hjälp funktioner måste du själv parsa den råa DER-kodade ASN. 1.*

| NetX Secure Identifier                              | OID-värde | Beskrivning                                                                    | Hjälp funktion? |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | Katalogattribut – grundläggande information om certifikat ämne  | Inga               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | Används för att identifiera en enskild offentlig nyckel                                         | Inga               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | Innehåller information om giltiga användnings områden för certifikatets offentliga nyckel              | Ja              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | Innehåller alternativa DNS-namn för att identifiera certifikatet                     | Ja<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | Innehåller alternativa DNS-namn för att identifiera certifikat utfärdaren            | Inga               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | Tillhandahåller information om grundläggande användnings villkor för certifikat                        | Inga               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | Används för att begränsa certifikat namn till vissa domäner                        | Inga               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | Tillhandahåller URI: er för CRL-distribution                                             | Inga               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | Lista över certifikat principer för stora PKI-system                             | Inga               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | Lista över principer för certifikat utfärdare                                                | Inga               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | Används för att identifiera en enskild offentlig nyckel som är kopplad till en certifikatets signatur | Inga               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | Begränsningar för CA-principer                                                          | Inga               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | Ytterligare OID-baserad nyckel användnings information                                     | Ja              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Innehåller information om hur du hämtar delta-CRL: er                                  | Inga               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | Fältet CA-certifikat indikerar att AnyPolicy inte kan användas                  | Inga               |

OID och mappningar för X. 509-tillägg

24. SubjectAltName-tillägget parsas som en del av DNS-namns kontrollen i tjänst nx_secure_x509_common_name_dns_check.

### <a name="parameters"></a>Parametrar

- **certifikat** Pekare till certifikat som verifieras.
- **tillägg** Retur struktur som innehåller tilläggs data pekare och längd.
- **extension_id** OID-heltals mappning från tabellen ovan.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) angivet tillägg-OID hittades och returnerade data.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 kod för flera byte påträffades (certifikat som inte stöds).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) ett inidentifierat ASN. 1-fält påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) ogiltig ASN. 1-tagg klass påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0X192) ogiltigt tillägg påträffades
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0X19B) det angivna tilläggets OID hittades inte i det angivna certifikatet.
- **NX_PTR_ERROR** (0X07) ogiltig certifikat-eller tilläggs pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hitta och parsa ett tillägg för nyckel användning i X. 509 i ett X. 509-certifikat

### <a name="prototype"></a>Prototyp

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är avsedd att anropas inifrån ett motanrop för certifikat verifiering (se *nx_secure_tls_session_certificate_callback_set)*. Den söker efter tillägget för nyckel användning och returnerar den nyckel användnings bitfield som finns i parametern "bitfield".

Bitarna, som definieras av specifikationen X. 509 (RFC 5280), anges i tabellen nedan. En bitvis och med lämplig bitmask (och genom att kontrol lera om det inte är noll) ger värdet för varje bit.

Observera att DER-encoding för bitfield eliminerar extra nollor, så den faktiska positionen för bitarna i rå certifikat data kommer sannolikt att skilja sig från deras position i den avkodade bitfield. De angivna bitmaskna är endast avsedda att användas på de avkodade bitfield som returneras av *nx_secure_x509_key_usage_extension_parse* och inte med RAW der-kodade certifikat data.

I återanropet av certifikat verifieringen är felet returkod NX_SECURE_X509_KEY_USAGE_ERROR reserverat för användning av program. Om det uppstår ett fel när nyckel användningen kontrol leras kan det här värdet returneras från återanropet för att indikera orsaken till felet.

| NetX Secure Identifier                            | Bit position | Beskrivning                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | Certifikat kan användas för digitala signaturer                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | Certifikat kan användas för att verifiera digitala signaturer förutom dem för certifikat och CRL: er                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | Certifikat kan användas för att kryptera symmetriska nycklar (nyckel transport)                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | Certifikat kan användas för att kryptera rå användar data direkt (ovanligt)                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | Certifikat kan användas för nyckel avtal (som med Diffie-Hellman)                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | Certifikat kan användas för att signera och verifiera andra certifikat (certifikatet är ett CA-eller ICA-certifikat).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | Certifikatets offentliga nyckel används för att verifiera signaturer i listor över återkallade certifikat                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | Används med nyckel avtals bit (bit 4) – när den anges kan certifikat nyckeln endast användas för kryptering under nyckel avtal. Odefinierad om nyckel avtals bit inte har angetts. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | Används med nyckel avtals bit (bit 4) – när den anges kan certifikat nyckeln endast användas för att dekryptera under nyckel avtal. Odefinierad om nyckel avtals bit inte har angetts. |

Bitmask och värden för tillägg för nyckel användning i X. 509

### <a name="parameters"></a>Parametrar

- **certifikat** Pekare till certifikat som verifieras.
- **bitfield** Returnera hela bitfield från tillägget.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) nyckel användnings tillägg hittades och bitfield returnerades.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 kod för flera byte påträffades (certifikat som inte stöds).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) ett inidentifierat ASN. 1-fält påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) ogiltig ASN. 1-tagg klass påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0X192) ogiltigt tillägg påträffades (ogiltigt certifikat).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0X19B) Det gick inte att hitta nyckel användnings tillägget i det angivna certifikatet.
- **NX_PTR_ERROR** (0X07) ogiltig certifikat-eller bitfield-pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

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
