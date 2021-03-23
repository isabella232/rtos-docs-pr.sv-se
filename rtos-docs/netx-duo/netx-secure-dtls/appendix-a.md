---
title: Bilaga A – Azure återställnings tider NetX Secure DTLS Return/Error Codes
description: Visar en lista över möjliga felkoder som kan returneras av Azure återställnings tider NetX Secure DTLS Services.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: reference
ms.service: rtos
ms.openlocfilehash: f14f27167a95a1b9d3ebbdf0d903be7b043ccb28
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825698"
---
# <a name="appendix-a-azure-rtos-netx-secure-dtls-returnerror-codes"></a>Bilaga A: Azure återställnings tider NetX Secure DTLS Return/Error Codes

## <a name="netx-secure-tlsdtls-return-codes"></a>NetX Secure TLS/DTLS retur koder

Tabell 1 nedan visar en lista över möjliga felkoder som kan returneras av Azure återställnings tider NetX Secure DTLS Services. Observera att tjänsterna även kan returnera UDP-eller IP-felkoder – TLS-värden som börjar vid 0x101 och TCP/IP/UDP-värden är lägre än 0x100. X. 509 returnerar värden som börjar på 0x181. Se NetX TCP/IP/UDP-dokumentationen för information om IP-och UDP-returer och se nedan för X. 509-värden.

| **Fel namn**                                        | **Värde** | **Beskrivning**                                                                                                                                               |
| ----------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_TLS_SUCCESS                              | 0x00      | Funktionen returnerades. (Samma som NX_SUCCESS).                                                                                                        |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101     | TLS-huvudloop anropade med oinitierad socket.                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102     | TLS-postskiktet fick en okänd meddelande typ.                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103     | Internt fel-tillstånd känns inte igen.                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104     | Internt fel-mottaget paket innehöll inte TLS-data.                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105     | Det valda ciphersuite stöds inte – internt fel för Server, för klient betyder det att fjärrvärden skickade en felaktig ciphersuite (fel eller attack).            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106     | Vid kryptering eller dekryptering inaktive ras den valda chiffrering eller är inte tillgänglig.                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107     | Något i meddelande bearbetning under hand skakningen misslyckades.                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108     | En inkommande post hade en MAC som inte matchade den som vi genererade.                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109     | Den utgående TCP-sändningen av en post misslyckades av någon anledning.                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH           | 0x10A     | Ett inkommande meddelande hade en längd som var felaktigt (vanligt vis en annan längd än ett i sidhuvudet, som i certifikat meddelanden)                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B     | Ett inkommande ChangeCipherSpec-meddelande var felaktigt.                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C     | Ett inkommande server certifikat kunde inte parsas korrekt.                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D     | Ett certifikat som tillhandahållits av en server angav en offentlig nyckel åtgärd som vi inte stöder.                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E     | Tog emot en sitt hälsnings utan stöd för krypteringssviter.                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F     | En inkommande post hade en TLS-version som inte känns igen.                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110     | En inkommande post hade en giltig TLS-version, men en som inte stöds.                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111     | Det gick inte att allokera intern paket för ett TLS-meddelande.                                                                                                       |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112     | Ett X509-certifikat kunde inte parsas korrekt.                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113     | Ingen CloseNotify togs emot från fjärrvärden när en TLS-session stängdes.                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114     | Fjärrvärden skickade en avisering, indikerar ett fel och stänger anslutningen.                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115     | Den mottagna hashen för slut meddelandet matchar inte den lokala genererade hash-hand skakningen.                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM        | 0x116     | Ett certifikat under verifieringen hade en signaturalgoritm som inte stöds.                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED      | 0x117     | Verifieringen av certifikatets signatur misslyckades – certifikat data matchade inte signaturen.                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD             | 0x118     | Ett hello-meddelande togs emot med en komprimerings metod som inte stöds.                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND              | 0x119     | Det gick inte att hitta något matchande certifikat i en åtgärd i en certifikat lista.                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT          | 0x11A     | Fjärrvärden skickade ett självsignerat certifikat och NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES har inte definierats.                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND      | 0x11B     | Ett fjärrcertifikat togs emot med en utfärdare som inte är i det lokala betrodda arkivet.                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE              | 0x11C     | Ett DTLS-meddelande togs emot i fel ordning-ett utelämnat datagram är den sannolika orsaken.                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                | 0x11D     | Ett paket togs emot från en fjärran sluten värd som vi inte känner igen.                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                       | 0x11E     | Ett DTLS-meddelande togs emot och matchades till en DTLS-session, men det hade fel epok och borde ignoreras.                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED            | 0x11F     | Ett DTLS-meddelande togs emot med ett sekvensnummer som vi redan har sett, ignorera det.                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                  | 0x120     | En TLS-session användes i ett DTLS-API som inte har initierats för DTLS.                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                   | 0x121     | En TLS-session användes i ett TLS-API som initierades för DTLS och inte TLS.                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH              | 0x122     | Anroparen försökte skicka data via en DTLS-session med en IP-adress eller port som inte matchar sessionen.                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS             | 0x123     | En ny anslutning försökte hämta en DTLS-session från cachen, men det var inget kostnads fritt.                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                 | 0x124     | Anroparen sökte efter en DTLS-session, men den tilldelade IP-adressen och porten matchade inte några poster i cacheminnet.                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                 | 0x125     | Anroparen försökte lägga till en PSK till en TLS-session, men det fanns inte mer utrymme i den aktuella sessionen.                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                    | 0x126     | En fjärrvärd tillhandahöll ett PSK-identitetsprogram som inte stämde med några i vårt lokala arkiv.                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED              | 0x127     | En TLS-session tog emot en CloseNotify-avisering från fjärrvärden som indikerar att sessionen är klar.                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS              | 0x128     | Inga TLS-sessioner i ett TLS-objekt är tillgängliga för att hantera en anslutning.                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED           | 0x129     | Inget certifikat utrymme har allokerats för inkommande fjärrcertifikat.                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED               | 0x12A     | Krypterings utfyllnad i ett inkommande meddelande var felaktig.                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE        | 0x12B     | Vid bearbetning av en CertificateVerifyRequest angavs ingen certifikat typ som stöds av fjärrservern.                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG         | 0x12C     | Vid bearbetning av en CertificateVerifyRequest angavs ingen Signeringsalgoritm som stöds av fjärrservern.                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE            | 0x12D     | Det finns inte tillräckligt med buffertutrymme allokerat för ett certifikat.                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED           | 0x12E     | Protokoll versionen i en inkommande TLS-post matchade inte versionen för den etablerade sessionen.                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR             | 0x12F     | Ett HelloRequest-meddelande togs emot, men vi omförhandlar inte.                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                 | 0x130     | En funktion som har inaktiverats påträffades under en TLS-session eller hand skakning.                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE         | 0x131     | Ett CertificateVerify-meddelande från en fjärran sluten klient kunde inte verifiera klient certifikatet.                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED | 0x132     | Fjärrvärden skickade ett tomt certifikat meddelande.                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR      | 0x133     | Ett fel uppstod vid bearbetning av ett säkert Renegotation-tillägg.                                                                     |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE     | 0x134     | En omförhandling av sessionen försökte utföra en TLS-session som inte var aktiv.                                                                                |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL           | 0x135     | TLS tog emot en post som var för stor för den tilldelade Packet-bufferten. Det gick inte att bearbeta posten.                                                   |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                | 0x136     | Ett angivet tillägg togs inte emot från fjärrvärden under TLS-handskakningen.                                                                         |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID              | 0x137     | TLS tog emot ett ogiltigt Servernamnindikator-tillägg.                                                                                                     |
| NX_SECURE_TLS_CERT_ID_INVALID                    | 0x138     | Programmet försökte lägga till ett Server certifikat med ett ogiltigt certifikat-ID-värde (troligt vis 0).                                                                |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                  | 0x139     | Programmet försökte lägga till ett Server certifikat med ett certifikat-ID som redan finns i det lokala arkivet.                                                       |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE               | 0x13A     | Fjärrvärden tillhandahöll inget säkert tillägg för säker omförhandling eller SCSV pseudo-ciphersuite, så det går inte att utföra säker omförhandling.     |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE             | 0x13B     | När en krypterings åtgärd skulle utföras har en av posterna i ciphersuite-tabellen (eller en av dess funktions pekare) felaktigt angetts till NULL. |

**Tabell 1 – NetX Secure TLS-fel retur koder**

## <a name="netx-secure-x509-return-codes"></a>NetX Secure X. 509 retur koder

Tabell 2 nedan visar de möjliga felkoder som kan returneras av NetX Secure X. 509-tjänsterna. Observera att tjänsterna även kan returnera andra felkoder. X. 509 returnerar värden som börjar vid 0x181, TLS-värden börjar vid 0x101 och TCP/IP-värden är under 0x100. I NetX TCP/IP-dokumentationen hittar du information om TCP/IP-retur värden och ovan för TLS-retur värden.

| **Fel namn**                                   | **Värde** | **Beskrivning**                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | Lyckad retur status. (Samma som NX_SUCCESS)                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | Vi har påträffat en ASN. 1-tagg med flera byte-stöds inte för närvarande.                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | Ett längd värde har uppstått längre än vad vi kan hantera.                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | Ett av värdena för utfyllnad förväntades vara 0.                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | X509 förväntade en offentlig nyckel men det gick inte att hitta någon.                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | En offentlig nyckel hittades, men den är ogiltig eller har ett felaktigt format.                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | Det översta ASN. 1-blocket är inte en sekvens-ogiltigt X509-certifikat.                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | Det gick inte att hitta algoritmen för signeringsalgoritmen.                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | Certifikat identitets data har ett ogiltigt format.                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | En speciell ASN. 1-tagg förväntades för X509-format men vi fick något annat.                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | En PKCS # 1-fil med privat nyckel skickades, men formateringen var felaktig.                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | En X509-certifikat kedja var för liten för att rymma hela kedjan under skapande av kedja.                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | Det gick inte att verifiera en X509-certifikat kedja (catch-all-fel).                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | Det gick inte att parsa en X. 509 PKCS # 7-kodad signatur.                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | Det gick inte att hitta någon matchande post i att leta upp ett certifikat.                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | Ett certifikat innehöll ett fält som inte är kompatibelt med den aktuella versionen.                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | Ett certifikat som ingår i en ASN. 1-tagg med ett ogiltigt tagg klass värde.                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | Ett certifikat har inkluderat ett tillägg-TLV men som inte innehöll någon sekvens.                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | Ett certifikat innehöll en tilläggsprovider som var ogiltig X. 509.                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | Ett certifikat hade ett "inte efter"-fält som var mindre än den aktuella tiden.                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | Ett certifikat hade ett "not före"-fält som var större än den aktuella tiden.                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | Ett eget certifikats namn eller ämnes alternativ namn matchade inte en specifik DNS-topp.                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | Ett certifikat innehåller ett datum fält som inte är i ett recognixed-format.                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | En angiven CRL och ett certifikat har inte utfärdats av samma certifikat utfärdare.                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | Det gick inte att kontrol lera CRL-signaturen mot utfärdaren.                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | Ett certifikat hittades i en giltig CRL och har därför återkallats.                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | Vid försök att verifiera signaturen matchades inte den förväntade metoden.                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | Vid sökning efter ett tillägg påträffades inget tillägg med ett matchande ID.                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | Ett namn har sökts efter i ett subjectAltName-tillägg men hittades inte.                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | Den privata nyckel typen som angetts var okänd eller ogiltig.                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | Skickade en namn sträng som var för lång för en intern buffert (DNS-namn osv...).                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | Vid sökning efter ett tillägg för utökad nyckel användning hittades inte det angivna OID-värdet för nyckel användning.                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | Ska returneras av program återanropet om det uppstår ett problem med nyckel användningen under en certifikat verifierings kontroll. |

**Tabell 2 – NetX Secure X. 509 fel retur koder**
