---
title: Bilaga A – Azure RTOS NetX Secure retur/felkoder
description: NetX Secure Return/Error Codes
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3957075f2b2e83f70bbd5f267cac41f003eb7d93722a3b2247b2a33226b4dfc5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791762"
---
# <a name="appendix-a---azure-rtos-netx-secure-returnerror-codes"></a>Bilaga A – Azure RTOS NetX Secure retur/felkoder

## <a name="netx-secure-tls-return-codes"></a>Returkoder för NetX Secure TLS

I tabell 1 nedan visas möjliga felkoder som kan returneras av Azure RTOS NetX Secure TLS-tjänster. Observera att tjänsterna också kan returnera TCP/IP-felkoder – TLS-värden börjar vid 0x101 och TCP/IP-värdena är lägre än 0x100. X.509-returvärden börjar vid 0x181. Se NetX TCP/IP-dokumentationen för information om TCP/IP-returvärden och se nedan för X.509-värden.

| Felnamn                                             | Värde  | Beskrivning                                                                                                                                                    |
| ---------------------------------------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| NX_SECURE_TLS_SUCCESS                              | 0x00  | Funktionen returnerades. (Samma som NX_SUCCESS).                                                                                                         |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101  | TLS-huvudslinga anropas med en oiniterad socket.                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102  | TLS-postlagret tog emot en okänd meddelandetyp.                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103  | Internt fel – tillståndet känns inte igen.                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104  | Internt fel – det mottagna paketet innehöll inte TLS-data.                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105  | Det valda chiffersuite stöds inte – internt fel för servern, för klienten innebär det att fjärrvärden skickade ett felaktigt chiffer (fel eller attack).            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106  | Vid kryptering eller dekryptering är det valda chifferet inaktiverat eller otillgängligt.                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107  | Något i meddelandebearbetningen under handskakningen har misslyckats.                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108  | En inkommande post hade en MAC som inte matchar den som vi genererade.                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109  | Den utgående TCP-skickande av en post misslyckades av någon anledning.                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH            | 0x10A  | Ett inkommande meddelande hade en längd som var felaktig (vanligtvis en annan längd än en i rubriken, som i certifikatmeddelanden)                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B  | Ett inkommande ChangeCipherSpec-meddelande var felaktigt.                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C  | Ett inkommande servercertifikat parsade inte korrekt.                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D  | Ett certifikat som tillhandahålls av en server har angett en åtgärd med offentlig nyckel som vi inte stöder.                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E  | Tog emot en ClientHello utan chiffer som stöds.                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F  | En inkommande post hade en TLS-version som inte känns igen.                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110  | En inkommande post hade en giltig TLS-version, men en som inte stöds.                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111 | En intern paketallokering för ett TLS-meddelande misslyckades.                                                                                                        |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112  | Ett X509-certifikat parsade inte korrekt.                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113 | Under en TLS-session fick inte closeNotify från fjärrvärden.                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114 | Fjärrvärden skickade en avisering som anger ett fel och stänger anslutningen.                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115  | Hashen För att slutföra meddelandet matchar inte den lokala genererade hashen – handskakningsfel.                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM         | 0x116 | Ett certifikat under verifieringen hade en signaturalgoritm som inte stöds.                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED       | 0x117  | Verifieringskontrollen av certifikatsignaturen misslyckades – certifikatdata matchade inte signaturen.                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD              | 0x118  | Ett Hello-meddelande med en komprimeringsmetod som inte stöds har tagits emot.                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND               | 0x119  | I en åtgärd i en certifikatlista hittades inget matchande certifikat.                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT           | 0x11A  | Fjärrvärden skickade ett själv signerat certifikat och NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES har inte definierats.                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND       | 0x11B  | Ett fjärrcertifikat togs emot med en utfärdare som inte finns i det lokala betrodda arkivet.                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE               | 0x11C  | Ett DTLS-meddelande togs emot i fel ordning – ett borttaget datagram är sannolikt den som är skyldig.                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                 | 0x11D  | Ett paket togs emot från en fjärrvärd som vi inte känner igen.                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                        | 0x11E  | Ett DTLS-meddelande togs emot och matchades till en DTLS-session, men det hade fel epok och bör ignoreras.                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED             | 0x11F  | Ett DTLS-meddelande togs emot med ett sekvensnummer som vi redan har sett. Ignorera det.                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                   | 0x120  | En TLS-session användes i ett DTLS-API som inte initierades för DTLS.                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                    | 0x121  | En TLS-session användes i ett TLS-API som initierades för DTLS och inte TLS.                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH               | 0x122  | Anroparen försökte skicka data via en DTLS-session med en IP-adress eller port som inte matchar sessionen.                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS              | 0x123  | En ny anslutning försökte hämta en DTLS-session från cachen, men det fanns ingen kostnadsfri.                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                  | 0x124  | Anroparen sökte efter en DTLS-session, men den angivna IP-adressen och porten matchade inte några poster i cacheminnet.                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                  | 0x125  | Anroparen försökte lägga till en PSK i en TLS-session, men det fanns inget mer utrymme i den angivna sessionen.                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                     | 0x126  | En fjärrvärd tillhandahöll en PSK-identitetstips som inte matchade någon i vårt lokala arkiv.                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED               | 0x127  | En TLS-session tog emot en CloseNotify-avisering från fjärrvärden som anger att sessionen har slutförts.                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS               | 0x128  | Inga TLS-sessioner i ett TLS-objekt är tillgängliga för att hantera en anslutning.                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED            | 0x129  | Inget certifikatutrymme har allokerats för inkommande fjärrcertifikat.                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED                | 0x12A  | Krypteringsutfyllnaden i ett inkommande meddelande var felaktig.                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE         | 0x12B  | Vid bearbetning av en CertificateVerifyRequest tillhandahölls ingen certifikattyp som stöds av fjärrservern.                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG          | 0x12C  | Vid bearbetning av en CertificateVerifyRequest tillhandahölls ingen signaturalgoritm som stöds av fjärrservern.                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE             | 0x12D  | Det finns inte tillräckligt med allokerat certifikatbuffertutrymme för ett certifikat.                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED            | 0x12E  | Protokollversionen i en inkommande TLS-post matchade inte versionen av den etablerade sessionen.                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR              | 0x12F  | Ett HelloRequest-meddelande har tagits emot, men vi förhandlar inte om det på nytt.                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                  | 0x130  | En funktion som var inaktiverad påträffades under en TLS-session eller handskakning.                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE          | 0x131  | Ett CertificateVerify-meddelande från en fjärrklient kunde inte verifiera klientcertifikatet.                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED  | 0x132  | Fjärrvärden skickade ett tomt certifikatmeddelande.                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR       | 0x133  | Ett fel uppstod vid bearbetningen av eller sändningen av tillägget Säker omförhandlingsindikation.                                                                      |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE      | 0x134  | En omförhandling av sessionen gjordes med en TLS-session som inte var aktiv.                                                                                 |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL            | 0x135  | TLS tog emot en post som var för stor för den tilldelade paketbufferten. Det gick inte att bearbeta posten.                                                    |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                 | 0x136  | Ett angivet tillägg togs inte emot från fjärrvärden under TLS-handskakningen.                                                                          |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID               | 0x137  | TLS tog emot ett ogiltigt Servernamnindikator-tillägg.                                                                                                      |
| NX_SECURE_TLS_CERT_ID_INVALID                     | 0x138  | Programmet försökte lägga till ett servercertifikat med ett ogiltigt certifikat-ID-värde (troligen 0).                                                                 |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                   | 0x139  | Programmet försökte lägga till ett servercertifikat med ett certifikat-ID som redan finns i det lokala arkivet.                                                        |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE                | 0x13A  | Fjärrvärden har inte tillhandahåller tillägget för säker omförhandlingsindikation eller SCSV-pseudociphersuite, så säker omförhandling kan inte utföras.      |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE              | 0x13B  | Vid försök att utföra en kryptografisk åtgärd har en av posterna i chiffertabellen (eller någon av dess funktionspekare) felaktigt angetts till NULL. |
| NX_SECURE_TLS_EMPTY_EC_GROUP                      | 0x13C  | ECC-chiffer har angetts men ingen EC-grupp stöds.                                                                                                             |
| NX_SECURE_TLS_EMPTY_EC_POINT_FORMAT              | 0x13D  | ECC-chifferuten har angetts men inget EC-punktformat stöds.                                                                                                      |
| NX_SECURE_TLS_BAD_SERVERHELLO_KEYSHARE            | 0x13E  | I ett TLS 1.3 KeyShare-tillägg från en fjärrserver tillhandahöll servern något som vi inte förväntade oss.                                                         |
| NX_SECURE_TLS_INSUFFICIENT_METADATA_SPACE         | 0x13F  | Programmets "metadata" för kryptografiska TLS-rutiner var för små.                                                                             |
| NX_SECURE_TLS_POST_HANDSHAKE_RECEIVED             | 0x140  | Inte ett fel, men en indikation på att fortsätta bearbeta tills programdata tas emot.                                                                    |
| NX_SECURE_TLS_BAD_CLIENTHELLO_KEYSHARE            | 0x141  | I ett TLS 1.3 KeyShare-tillägg från en fjärrklient tillhandahöll klienten något som vi inte förväntade oss.                                                         |
| NX_SECURE_TLS_1_3_UNKNOWN_CIPHERSUITE            | 0x142  | Tog emot okänt chiffer när TLS 1.3 används.                                                                                                              |
| NX_SECURE_TLS_INVALID_SESSION_TICKET              | 0x143  | Tog emot ett NewSessionTicket-meddelande med felaktiga eller ogiltiga parametrar.                                                                                      |
| NX_SECURE_TLS_MISSING_EXTENSION                    | 0x144  | Ett visst tillägg missas i meddelandet.                                                                                                                  |
| NX_SECURE_TLS_CERTIFICATE_REQUIRED                 | 0x145  | Servern tog emot ett tomt certifikat.                                                                                                                         |
| NX_SECURE_TLS_UNEXPECTED_CLIENTHELLO               | 0x146  | TLS 1.3-servern tar emot ClientHello för omförhandling.                                                                                                         |
| NX_SECURE_TLS_INAPPROPRIATE_FALLBACK               | 0x147  | Fjärrklienten försökte nedgradera en olämplig TLS-version.                                                                                               |
| NX_SECURE_TLS_BAD_CLIENTHELLO_PSK_EXTENSION      | 0x148  | I ett TLS 1.3 PSK-tillägg från en fjärrklient tillhandahöll klienten något som vi inte förväntade oss.                                                              |
| NX_SECURE_TLS_PSK_BINDER_MISMATCH                 | 0x149  | I ett TLS 1.3 PSK-tillägg från en fjärrklient tillhandahöll klienten ett felaktigt PSK-binder-värde.                                                                  |
| NX_SECURE_TLS_CRYPTO_KEYS_TOO_LARGE              | 0x14A  | Vid försök att generera TLS-sessionsnycklar var nyckelbufferten för liten – öka NX_SECURE_TLS_KEY_MATERIAL_SIZE.                                     |
| NX_SECURE_TLS_UNSUPPORTED_ECC_CURVE               | 0x14B  | Fjärrvärden tillhandahöll ett certifikat eller valde ett chiffer med en ECC-kurva som inte stöds.                                                         |
| NX_SECURE_TLS_UNSUPPORTED_ECC_FORMAT              | 0x14C  | En kurva eller ECC-format som inte stöds påträffades.                                                                                                 |
| NX_SECURE_TLS_UNSUPPORTED_SIGNATURE_ALGORITHM     | 0x14D  | En signaturalgoritm som inte stöds påträffades (används i nyckelutbyte eller andra situationer som inte är certifikat).                                                |
| NX_SECURE_TLS_SIGNATURE_VERIFICATION_ERROR        | 0x14E  | En signaturverifieringskontroll misslyckades (används i nyckelutbyte eller andra situationer som inte är certifikat).                                                                    |
| NX_SECURE_TLS_UNEXPECTED_MESSAGE                   | 0x14F  | TLS tog emot ett oväntat meddelande från fjärrvärden.                                                                                                      |
| NX_SECURE_TLS_AEAD_DECRYPT_FAIL                   | 0x150  | En inkommande post passade inte integritetskontroll med AEAD-chiffer.                                                                                            |
| NX_SECURE_TLS_RECORD_OVERFLOW                      | 0x151  | Tog emot en TLSCiphertext-post som hade en för lång längd.                                                                                                   |
| NX_SECURE_TLS_HANDSHAKE_FRAGMENT_RECEIVED         | 0x152  | Tog emot ett fragmenterat handskakningsmeddelande – vidta lämpliga åtgärder på en högre nivå av tillståndsdatorn.                                                     |

| Felnamn                                             | Värde  | Beskrivning                                                                                                                                                    |
| ---------------------------------------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| NX_SECURE_TLS_SUCCESS                               | 0x00   | Funktionen returnerades. (Samma som NX_SUCCESS).                                                                                                         |
| NX_SECURE_TLS_SESSION_UNINITIALIZED                | 0x101  | TLS-huvudloop med en oiniterad socket.                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE           | 0x102  | TLS-postlagret tog emot en okänd meddelandetyp.                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                        | 0x103  | Internt fel – tillståndet känns inte igen.                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                       | 0x104  | Internt fel – det mottagna paketet innehöll inte TLS-data.                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                  | 0x105  | Det valda chiffersuite stöds inte – internt fel för servern. För klienten innebär det att fjärrvärden skickade ett felaktigt chiffer (fel eller attack).            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                   | 0x106  | Vid kryptering eller dekryptering är det valda chifferet inaktiverat eller otillgängligt.                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                    | 0x107  | Något i meddelandebearbetningen under handskakningen har misslyckats.                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE            | 0x108  | En inkommande post hade en MAC som inte matchar den som vi genererade.                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                     | 0x109  | Det utgående TCP-meddelandet för en post misslyckades av någon anledning.                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH            | 0x10A  | Ett inkommande meddelande hade en längd som var felaktig (vanligtvis en annan längd än en i rubriken, som i certifikatmeddelanden)                                |
| NX_SECURE_TLS_BAD_CIPHERSPEC                       | 0x10B  | Ett inkommande ChangeCipherSpec-meddelande var felaktigt.                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                 | 0x10C  | Ett inkommande servercertifikat parsade inte korrekt.                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER           | 0x10D  | Ett certifikat som tillhandahålls av en server har angett en åtgärd med offentlig nyckel som vi inte stöder.                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS                | 0x10E  | Tog emot en ClientHello utan chiffer som stöds.                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                 | 0x10F  | En inkommande post hade en TLS-version som inte känns igen.                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION             | 0x110  | En inkommande post hade en giltig TLS-version, men en som inte stöds.                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED              | 0x111  | En intern paketallokering för ett TLS-meddelande misslyckades.                                                                                                        |
| NX_SECURE_TLS_INVALID_CERTIFICATE                  | 0x112  | Ett X509-certifikat parsade inte korrekt.                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                   | 0x113  | Under en TLS-session fick inte closeNotify från fjärrvärden.                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                       | 0x114  | Fjärrvärden skickade en avisering som anger ett fel och stänger anslutningen.                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE               | 0x115  | Den mottagna finish-meddelandehashen matchar inte den lokala genererade hashen – handskakningsfel.                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM         | 0x116  | Ett certifikat under verifieringen hade en signaturalgoritm som inte stöds.                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED       | 0x117  | Verifieringskontrollen av certifikatsignaturen misslyckades – certifikatdata matchade inte signaturen.                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD              | 0x118  | Ett Hello-meddelande med en komprimeringsmetod som inte stöds har tagits emot.                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND               | 0x119  | I en åtgärd i en certifikatlista hittades inget matchande certifikat.                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT           | 0x11A  | Fjärrvärden skickade ett själv signerat certifikat och NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES har inte definierats.                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND       | 0x11B  | Ett fjärrcertifikat togs emot med en utfärdare som inte finns i det lokala betrodda arkivet.                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE               | 0x11C  | Ett DTLS-meddelande har tagits emot i fel ordning – ett borttaget datagram är sannolikt den som har fallit.                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                 | 0x11D  | Ett paket togs emot från en fjärrvärd som vi inte känner igen.                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                        | 0x11E  | Ett DTLS-meddelande togs emot och matchades till en DTLS-session, men det hade fel epok och bör ignoreras.                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED             | 0x11F  | Ett DTLS-meddelande togs emot med ett sekvensnummer som vi redan har sett. Ignorera det.                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                   | 0x120  | En TLS-session användes i ett DTLS-API som inte initierades för DTLS.                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                    | 0x121  | En TLS-session användes i ett TLS-API som initierades för DTLS och inte TLS.                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH               | 0x122  | Anroparen försökte skicka data via en DTLS-session med en IP-adress eller port som inte matchar sessionen.                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS              | 0x123  | En ny anslutning försökte hämta en DTLS-session från cachen, men det fanns ingen kostnadsfri.                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                  | 0x124  | Anroparen sökte efter en DTLS-session, men den angivna IP-adressen och porten matchade inte några poster i cacheminnet.                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                  | 0x125  | Anroparen försökte lägga till en PSK i en TLS-session, men det fanns inget mer utrymme i den angivna sessionen.                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                     | 0x126  | En fjärrvärd tillhandahöll en PSK-identitetstips som inte matchade någon i vårt lokala arkiv.                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED               | 0x127  | En TLS-session tog emot en CloseNotify-avisering från fjärrvärden som anger att sessionen har slutförts.                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS               | 0x128  | Inga TLS-sessioner i ett TLS-objekt är tillgängliga för att hantera en anslutning.                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED            | 0x129  | Inget certifikatutrymme har allokerats för inkommande fjärrcertifikat.                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED                | 0x12A  | Krypteringsutfyllnad i ett inkommande meddelande var inte korrekt.                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE         | 0x12B  | Vid bearbetningen av en CertificateVerifyRequest tillhandahölls ingen certifikattyp som stöds av fjärrservern.                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG          | 0x12C  | Vid bearbetningen av en CertificateVerifyRequest tillhandahölls ingen signaturalgoritm som stöds av fjärrservern.                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE             | 0x12D  | Det finns inte tillräckligt med allokerat certifikatbuffertutrymme för ett certifikat.                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED            | 0x12E  | Protokollversionen i en inkommande TLS-post matchade inte versionen av den etablerade sessionen.                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR              | 0x12F  | Ett HelloRequest-meddelande har tagits emot, men vi förhandlar inte om det på nytt.                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                  | 0x130  | En funktion som var inaktiverad påträffades under en TLS-session eller handskakning.                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE          | 0x131  | Ett CertificateVerify-meddelande från en fjärrklient kunde inte verifiera klientcertifikatet.                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED  | 0x132  | Fjärrvärden skickade ett tomt certifikatmeddelande.                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR       | 0x133  | Ett fel uppstod vid bearbetning av ett tillägg för säker omförhandlingsindikation eller sändning av en säker omförhandlingsindikering.                                                                      |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE      | 0x134  | En omförhandling av sessionen gjordes med en TLS-session som inte var aktiv.                                                                                 |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL            | 0x135  | TLS tog emot en post som var för stor för den tilldelade paketbufferten. Det gick inte att bearbeta posten.                                                    |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                 | 0x136  | Ett angivet tillägg togs inte emot från fjärrvärden under TLS-handskakningen.                                                                          |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID               | 0x137  | TLS tog emot ett ogiltigt Servernamnindikator tillägg.                                                                                                      |
| NX_SECURE_TLS_CERT_ID_INVALID                     | 0x138  | Programmet försökte lägga till ett servercertifikat med ett ogiltigt certifikat-ID-värde (troligen 0).                                                                 |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                   | 0x139  | Programmet försökte lägga till ett servercertifikat med ett certifikat-ID som redan finns i det lokala arkivet.                                                        |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE                | 0x13A  | Fjärrvärden tillhandahåller inte tillägget för säker omförhandlingsindikering eller SCSV-pseudociphersuite, så det går inte att utföra säker omförhandling.      |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE              | 0x13B  | Vid försök att utföra en kryptografisk åtgärd var en av posterna i chiffertabellen (eller någon av dess funktionspekare) felaktigt inställd på NULL. |
| NX_SECURE_TLS_EMPTY_EC_GROUP                      | 0x13C  | ECC-chiffer har angetts men ingen EC-grupp stöds.                                                                                                             |
| NX_SECURE_TLS_EMPTY_EC_POINT_FORMAT              | 0x13D  | ECC-chiffer har angetts men inget EC-punktformat stöds.                                                                                                      |
| NX_SECURE_TLS_BAD_SERVERHELLO_KEYSHARE            | 0x13E  | I TLS 1.3 KeyShare-tillägget från en fjärrserver tillhandahöll servern något som vi inte förväntade oss.                                                         |
| NX_SECURE_TLS_INSUFFICIENT_METADATA_SPACE         | 0x13F  | Programmets "metadata" för kryptografiska TLS-rutiner var för små.                                                                             |
| NX_SECURE_TLS_POST_HANDSHAKE_RECEIVED             | 0x140  | Inte ett fel, men en indikation på att fortsätta bearbeta tills programdata tas emot.                                                                    |
| NX_SECURE_TLS_BAD_CLIENTHELLO_KEYSHARE            | 0x141  | I ett TLS 1.3 KeyShare-tillägg från en fjärrklient tillhandahöll klienten något som vi inte förväntade oss.                                                         |
| NX_SECURE_TLS_1_3_UNKNOWN_CIPHERSUITE            | 0x142  | Tog emot okänt chiffer när TLS 1.3 används.                                                                                                              |
| NX_SECURE_TLS_INVALID_SESSION_TICKET              | 0x143  | Tog emot ett NewSessionTicket-meddelande med felaktiga eller ogiltiga parametrar.                                                                                      |
| NX_SECURE_TLS_MISSING_EXTENSION                    | 0x144  | Ett visst tillägg missas i meddelandet.                                                                                                                  |
| NX_SECURE_TLS_CERTIFICATE_REQUIRED                 | 0x145  | Servern tog emot ett tomt certifikat.                                                                                                                         |
| NX_SECURE_TLS_UNEXPECTED_CLIENTHELLO               | 0x146  | TLS 1.3-servern tar emot ClientHello för omförhandling.                                                                                                         |
| NX_SECURE_TLS_INAPPROPRIATE_FALLBACK               | 0x147  | Fjärrklienten försökte nedgradera en olämplig TLS-version.                                                                                               |
| NX_SECURE_TLS_BAD_CLIENTHELLO_PSK_EXTENSION      | 0x148  | I ett TLS 1.3 PSK-tillägg från en fjärrklient tillhandahöll klienten något som vi inte förväntade oss.                                                              |
| NX_SECURE_TLS_PSK_BINDER_MISMATCH                 | 0x149  | I ett TLS 1.3 PSK-tillägg från en fjärrklient tillhandahöll klienten ett felaktigt PSK-binder-värde.                                                                  |
| NX_SECURE_TLS_CRYPTO_KEYS_TOO_LARGE              | 0x14A  | Vid försök att generera TLS-sessionsnycklar var nyckelbufferten för liten – öka NX_SECURE_TLS_KEY_MATERIAL_SIZE.                                     |
| NX_SECURE_TLS_UNSUPPORTED_ECC_CURVE               | 0x14B  | Fjärrvärden tillhandahöll ett certifikat eller valde ett chiffer med en ECC-kurva som inte stöds.                                                         |
| NX_SECURE_TLS_UNSUPPORTED_ECC_FORMAT              | 0x14C  | En kurva eller ECC-format som inte stöds påträffades.                                                                                                 |
| NX_SECURE_TLS_UNSUPPORTED_SIGNATURE_ALGORITHM     | 0x14D  | En signaturalgoritm som inte stöds påträffades (används i nyckelutbyte eller andra situationer som inte är certifikat).                                                |
| NX_SECURE_TLS_SIGNATURE_VERIFICATION_ERROR        | 0x14E  | En signaturverifieringskontroll misslyckades (används i nyckelutbyte eller andra situationer som inte är certifikat).                                                                    |
| NX_SECURE_TLS_UNEXPECTED_MESSAGE                   | 0x14F  | TLS tog emot ett oväntat meddelande från fjärrvärden.                                                                                                      |
| NX_SECURE_TLS_AEAD_DECRYPT_FAIL                   | 0x150  | En inkommande post passade inte integritetskontroll med AEAD-chiffer.                                                                                            |
| NX_SECURE_TLS_RECORD_OVERFLOW                      | 0x151  | Tog emot en TLSCiphertext-post som hade en för lång längd.                                                                                                   |
| NX_SECURE_TLS_HANDSHAKE_FRAGMENT_RECEIVED         | 0x152  | Tog emot ett fragmenterat handskakningsmeddelande – vidta lämpliga åtgärder på en högre nivå av tillståndsdatorn.                                                     |

**Tabell 1 – Returkoder för NetX Secure TLS-fel**

## <a name="netx-secure-x509-return-codes"></a>NetX Secure X.509 returkoder

Tabell 2 nedan visar möjliga felkoder som kan returneras av NetX Secure X.509-tjänster. Observera att tjänsterna också kan returnera andra felkoder. X.509-returvärden börjar vid 0x181, TLS-värden börjar vid 0x101 och TCP/IP-värden är lägre än 0x100. Se NetX TCP/IP-dokumentationen för information om TCP/IP-returvärden och högre för TLS-returvärden.

| Felnamn                                   | Värde | Beskrivning                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | Lyckad returstatus. (Samma som NX_SUCCESS)                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | Vi påträffade en ASN.1-tagg med flera byte – stöds inte för närvarande.                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | Ett längdvärde som är längre än vad vi kan hantera påträffades.                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | Förväntat utfyllnadsvärde 0 – fick något annat.                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | X509 förväntade sig en offentlig nyckel men hittade ingen.                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | En offentlig nyckel hittades, men den är ogiltig eller har ett felaktigt format.                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | ASN.1-blocket på den översta nivån är inte en sekvens – ogiltigt X509-certifikat.                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | Det gick inte att hitta en signaturalgoritmidentifierare.                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | Certifikatidentitetsdata har ett ogiltigt format.                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | Vi förväntade oss en specifik ASN.1-tagg för X509-format, men vi fick något annat.                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | En privat nyckelfil för PKCS#1 skickades, men formateringen var felaktig.                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | En X509-certifikatkedja var för kort för att innehålla hela kedjan under kedjeskapandet.                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | Det gick inte att verifiera en X509-certifikatkedja (catch-all-fel).                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | Det gick inte att parsa en X.509 PKCS #7 kodad signatur.                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | När du letar upp ett certifikat hittades ingen matchande post.                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | Ett certifikat innehöll ett fält som inte är kompatibelt med den angivna versionen.                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | Ett certifikat innehöll en ASN.1-tagg med ett ogiltigt taggklassvärde.                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | Ett certifikat innehöll tilläggen TLV men som inte innehöll någon sekvens.                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | Ett certifikat innehöll en tilläggssekvens som var ogiltig X.509.                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | Ett certifikat hade ett "inte efter"-fält som var mindre än den aktuella tiden.                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | Ett certifikat hade fältet "not before" (inte före) som var större än den aktuella tiden.                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | Ett eget namn för certifikatet eller alt-namn för certifikatämnet matchade inte ett visst DNS-TLD.                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | Ett certifikat innehöll ett datumfält som inte är i ett rekognixerat format.                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | En a provided CRL och certificate har inte utfärdats av samma certifikatutfärdare.                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | En CRL-signaturkontroll misslyckades mot dess utfärdare.                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | Ett certifikat hittades i en giltig lista över återkallade certifikat och har därför återkallats.                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | Signaturmetoden matchade inte den förväntade metoden vid försök att verifiera en signatur.                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | När du letar efter ett tillägg hittades inget tillägg med ett matchande ID.                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | Ett namn genomsökdes efter i ett subjectAltName-tillägg men hittades inte.                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | Den angivna privata nyckeltypen var okänd eller ogiltig.                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | Skickade en namnsträng som var för lång för en intern buffert (DNS-namn osv.).                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | När du sökte i ett tillägg för utökad nyckelanvändning hittades inte det angivna nyckelanvändnings-OID:t.                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | Ska returneras av programmets återanrop om det uppstår ett fel i nyckelanvändningen under en certifikatverifieringskontroll. |

**Tabell 2 – NetX Secure X.509-felreturkoder**
