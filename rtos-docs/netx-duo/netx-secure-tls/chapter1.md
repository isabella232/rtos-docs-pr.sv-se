---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Secure
description: Det här kapitlet innehåller en introduktion till Azure RTOS NetX Secure och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d6b0f23d7353626f340fe0ab93ee1e04800edaaa1f00da49afd83f84339df86
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791609"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-secure"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Secure

Azure RTOS NetX Secure är en högpresterande realtidsimplementering av säkerhetsstandarder för kryptografiska nätverk, inklusive TLS/SSL som utformats exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX Secure och en beskrivning av dess program och fördelar.

## <a name="netx-secure-unique-features"></a>Unika funktioner i NetX Secure

Till skillnad från de flesta andra TLS-implementeringar har NetX Secure utformats från grunden för att stödja en mängd olika inbäddade maskinvaruplattformar och skalas enkelt från små mikrostyrenhetsprogram till de mest kraftfulla inbäddade processorerna som är tillgängliga. Koden skrivs med de begränsade resurserna i inbäddade system i åtanke och tillhandahåller ett antal konfigurationsalternativ för att minska det minnesfotavtryck som krävs för att tillhandahålla säker nätverkskommunikation via TLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC:er som stöds av NetX Secure 

NetX Secure stöder följande protokoll som är relaterade till TLS. Listan är inte nödvändigtvis omfattande eftersom det finns flera RFC:er som rör TLS och kryptografi. NetX Secure följer alla allmänna rekommendationer och grundläggande krav inom begränsningarna i ett realtidsoperativsystemet med litet minnesfotavtryck och effektiv körning.

| RFC      | Description                                                                                                 | Sida |
|----------|-------------------------------------------------------------------------------------------------------------|------|
| RFC 2104 | HMAC: Keyed-Hashing för meddelandeautentisering                                                              | 33   |
| RFC 2246 | TLS-protokollversion 1.0                                                                                | 19   |
| RFC 3268 | Advanced Encryption Standard (AES)-chiffer för Transport Layer Security (TLS)                          | 31   |
| RFC 3447 | Public-Key Cryptography Standards (PKCS) #1: RSA Cryptography Specifications Version 2.1                    | 32   |
| RFC 4279 | Chifferutorer med i förväg delad nyckel för TLS                                                                         | 39   |
| RFC 4346 | Protokollet Transport Layer Security (TLS) version 1.1                                                     | 19   |
| RFC 5246 | Protokollet Transport Layer Security (TLS) version 1.2                                                     | 19   |
| RFC 5280 | X.509 PKI-certifikat (v3)                                                                                 | 41   |
| RFC 5746 | Transport Layer Security (TLS) Tillägg för omförhandlings indikation                                           |      |
| RFC 5869 | HMAC-baserad funktion för extrahering och expandering av nycklar (HKDF)                                                | 19   |
| RFC 6066<sup>1</sup> | Transport Layer Security (TLS)-tillägg: tilläggsdefinitioner                                            | 19   |
| RFC 6234 | US Secure Hash Algorithms (SHA and SHA-based HMAC and HKDF)                                                 | 33   |
| RFC 8443 | Elliptic Curve Cryptography (ECC) Chiffersviter för Transport Layer Security (TLS) version 1.2 och tidigare |      |
| RFC 8446 | Protokollet Transport Layer Security (TLS) version 1.3                                                     | 19   |

1. Från och med version 6.0 stöds Servernamnindikator (SNI)-tillägget från RFC 6066 fullt ut.

## <a name="netx-secure-requirements"></a>NetX-säkra krav

För att netX Secure-körningsbiblioteket ska fungera korrekt krävs att en NetX IP-instans redan har skapats. Beroende på programmet krävs dessutom ett eller flera DER-kodade digitala X.509-certifikat, antingen för att identifiera en TLS-instans eller för att verifiera certifikat som kommer från en fjärrvärd. NetX Secure-paketet har inga ytterligare krav.

## <a name="netx-secure-constraints"></a>Begränsningar för NetX-säkerhet

NetX Secure-protokollet implementerar kraven för RFC 5246 Standard(s) för TLS 1.2 och RFC 8446 för TLS 1.3, samt tillhandahåller valfri (inaktiverad som standard) bakåtkompatibilitet med RFCs 4346 (TLS 1.1) och 2246 (TLS 1.0). Det finns dock följande begränsningar:

- Endast chiffer som använder SHA-256 stöds för TLS 1.2 och TLS 1.3. I versioner före TLS 1.2 använder TLS-handskakningen en fast hash-rutin för att verifiera att TLS-handskakningsmeddelanden inte har manipulerats. Från och med version 1.2 använder handskakningen den hashrutin som medföljer chiffer. TLS vet inte i förväg vilken hashrutin som ska användas och måste cachelagra handskakningsmeddelandena. Genom att korrigera hashen till SHA-256 kan NetX Secure TLS fungera med ett mindre RAM-fotavtryck än andra TLS-implementeringar. Den här begränsningen tas bort i en framtida version när minnesanvändningen kan åtgärdas korrekt. *VIKTIGT! Den här **begränsningen** gäller endast för chifferval. X.509-certifikatsignaturer omfattas inte av samma begränsning och någon av de hash-rutiner som stöds kan användas.
- På grund av inbäddade enheter har vissa program kanske inte de resurser som krävs för den maximala TLS-poststorleken på 16 kB. NetX Secure kan hantera poster på 16 kB på enheter med tillräckligt med resurser. TLS-återmonteringsbufferten (se API-referens för *nx_secure_tls_session_packet_buffer_set* **)** kan anges till en storlek som är mindre än 16 kB, med risk för interoperabilitetsproblem. Om en giltig TLS-post tas emot som är större än bufferten för återmontering avbryter NetX Secure TLS TLS-sessionen med ett fel. I allmänhet bör bufferten alltid anges till minst 18 kB (16 kB TLS-poststorlek + 2 kB för krypteringsutfyllnad) och endast göras mindre i kontrollerade inställningar (t.ex. att fjärrvärden garanterar en maximal TLS-poststorlek).
  > [!NOTE]
  > I allmänhet bör paketbufferten aldrig vara mindre än den maximala TLS-poststorleken. Men om fjärrvärdens egenskaper är välkända (t.ex. i ett helt stängt system) kan storleken minskas för att återfå lite RAM-utrymme.
- Minimal certifikatverifiering. NetX Secure utför grundläggande X.509-kedjeverifiering på ett certifikat för att säkerställa att certifikatet är giltigt och signerat av en betrodd certifikatutfärdare och kan ange certifikatets eget namn för programmet att jämföra med Top-Level-domännamnet för fjärrvärden. Om en realtidsklocka är tillgänglig kan den användas för att verifiera certifikatets förfallodatum (se API-nx_secure_tls_session_time_function_set). Verifiering av certifikattillägg och andra data är dock programföre implementerarens ansvar.
- Programvarubaserad kryptografi är processorintensiv. NetX Secures programvarubaserade kryptografiska rutiner har optimerats för prestanda, men beroende på målprocessorns kraft kan den prestandan resultera i mycket långa åtgärder. När maskinvarubaserad kryptografi är tillgänglig bör den användas för optimala prestanda i NetX Secure TLS.
- Fragmentering av TLS-handskakningspost stöds inte. Om vissa TLS-handskakningspostmeddelanden är för stora kan de delas upp över flera TLS-poster – NetX Secure TLS behandlar för närvarande detta som ett fel. Minneskraven för inbäddade system innebär att det större meddelandet med handskakningsposten förmodligen inte kan hanteras ändå, men begränsningen kan leda till fel vid kommunikation med vissa TLS-värdar som använder alltför stora certifikatkedjor.
- TLS-servern stöder inte dynamiskt certifikaturval när det finns flera certifikat i det lokala arkivet. 
- X509-certifikatnyckelAnvändarcertifikat observeras inte. 
- ECDH-baserade chiffer stöds inte. Använd ECDHE i stället.
