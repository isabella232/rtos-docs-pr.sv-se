---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Secure
description: Det här kapitlet innehåller en introduktion till Azure återställnings tider NetX Secure och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f4c7a97564cd2f702f9887181b36297b42fa492
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825683"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-secure"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Secure

Azure återställnings tider NetX Secure är en real tids implementering av kryptografiska nätverks säkerhets standarder, inklusive TLS/SSL, som är utformad exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX Secure och en beskrivning av dess program och fördelar.

## <a name="netx-secure-unique-features"></a>NetX säkra unika funktioner

Till skillnad från de flesta andra TLS-implementeringar har NetX Secure utformats från grunden för att stödja en mängd olika inbäddade maskinvaruplattformar och skalas enkelt från små mikrokontrollants program till de mest kraftfulla inbäddade processorerna. Koden skrivs med begränsade resurser av inbäddade system i åtanke och innehåller ett antal konfigurations alternativ för att minska den minnes storlek som krävs för att tillhandahålla säker nätverkskommunikation över TLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC: er som stöds av NetX Secure 

NetX Secure stöder följande protokoll relaterade till TLS. Listan är inte nödvändigt vis omfattande eftersom det finns många RFC: er som rör TLS och kryptografi. NetX Secure följer alla allmänna rekommendationer och grundläggande krav inom begränsningar i ett operativ system i real tid med liten minnes storlek och effektiv körning.

| RFC      | Beskrivning                                                                                                 | Sida |
|----------|-------------------------------------------------------------------------------------------------------------|------|
| RFC 2104 | HMAC: Keyed-Hashing för meddelandeautentisering                                                              | 33   |
| RFC 2246 | TLS-protokoll version 1,0                                                                                | 19   |
| RFC 3268 | Advanced Encryption Standard (AES) krypteringssviter för Transport Layer Security (TLS)                          | 31   |
| RFC 3447 | Public-Key för kryptografi standarder (PKCS) #1: RSA Cryptography Specifications version 2,1                    | 32   |
| RFC 4279 | Krypteringssviter i förväg delad nyckel för TLS                                                                         | 39   |
| RFC 4346 | Transport Layer Security (TLS)-protokoll version 1,1                                                     | 19   |
| RFC 5246 | Transport Layer Security (TLS)-protokoll version 1,2                                                     | 19   |
| RFC 5280 | X. 509 PKI-certifikat (v3)                                                                                 | 41   |
| RFC 5746 | Tillägg för Transport Layer Security (TLS) omförhandlings indikering                                           |      |
| RFC 5869 | HMAC-baserad extrahera-och-expandera nyckel Härlednings funktion (HKDF)                                                | 19   |
| RFC 6066<sup>1</sup> | Transport Layer Security-tillägg (TLS): tilläggs definitioner                                            | 19   |
| RFC 6234 | AMERIKANSKA säkra hash-algoritmer (SHA och SHA-baserad HMAC och HKDF)                                                 | 33   |
| RFC 8443 | Elliptic Curve Cryptography (ECC) chiffersviter för Transport Layer Security (TLS) version 1,2 och tidigare |      |
| RFC 8446 | Transport Layer Security (TLS)-protokoll version 1,3                                                     | 19   |

1. Från och med version 6,0 stöds inte tillägget Servernamnindikator (SNI) från RFC 6066 fullt ut.

## <a name="netx-secure-requirements"></a>NetX säkra krav

För att kunna fungera korrekt kräver NetX-biblioteket för säker körning att en NetX-IP-instans redan har skapats. Och beroende på programmet, krävs ett eller flera DER-kodade X. 509-certifikat, antingen för att identifiera en TLS-instans eller verifiera certifikat som kommer från en fjärrvärd. Det NetX säkra paketet har inga ytterligare krav.

## <a name="netx-secure-constraints"></a>NetX säkra begränsningar

NetX Secure-protokollet implementerar kraven i RFC 5246-standarderna för TLS 1,2 och RFC 8446 för TLS 1,3, samt för att tillhandahålla valfria (inaktiverade som standard) bakåtkompatibla-kompatibilitet med RFC 4346 (TLS 1,1) och 2246 (TLS 1,0). Det finns dock följande begränsningar:

- Endast krypteringssviter som använder SHA-256 stöds för TLS 1,2 och TLS 1,3. I tidigare versioner än TLS 1,2 använder TLS-handskakning en fast hash-rutin för att verifiera att TLS-handskaknings meddelanden inte manipuleras. Från och med version 1,2 använder hand skakningen hash-rutinen som medföljer ciphersuite. TLS vet inte i förväg vilken hash-rutin som ska användas och måste cachelagra hand skaknings meddelandena. Genom att åtgärda hashen till SHA-256 kan NetX Secure TLS fungera med mindre RAM-minne än andra TLS-implementeringar. Den här begränsningen tas bort i en framtida version när minnes användningen kan åtgärdas korrekt. * VIKTIGT meddelande: den här begränsningen gäller **endast** för ciphersuite Choice. X. 509-Certifikatets signaturer omfattas inte av samma begränsning och alla hash-rutiner som stöds kan användas.
- På grund av typen av inbäddade enheter kanske vissa program inte har resurserna som stöder den maximala TLS-poststorleken för 16 KB. NetX Secure kan hantera 16 KB-poster på enheter med tillräckligt med resurser. TLS-omassembly-bufferten (se API-referens för *nx_secure_tls_session_packet_buffer_set*) kan ha en storlek som **är** mindre än 16 KB vid risken för problem med samverkan. Om en giltig TLS-post som är större än omassembly-bufferten tas emot avbryts TLS-sessionen med ett fel i NetX Secure TLS. I allmänhet bör bufferten alltid vara inställd på minst 18KB (16 KB TLS-poststorlek + 2KB för Encryption utfyllnad) och endast göras mindre i kontrollerade inställningar (t. ex. fjärrvärden garanterar en maximal TLS-post storlek).
  > [!NOTE]
  > I allmänhet bör paket omsammansättnings bufferten aldrig vara mindre än den största tillåtna storleken för TLS-poster. Men om egenskaperna för fjärrvärden är välkända (t. ex. i ett helt stängt system) kan storleken minskas för att få lite RAM-minne.
- Minimal certifikat verifiering. NetX Secure utför en grundläggande X. 509-på ett certifikat för att säkerställa att certifikatet är giltigt och signerat av en betrodd certifikat utfärdare, och kan ange certifikatets gemensamma namn för programmet som ska jämföras med Top-Level domän namnet för fjärrvärden. Om det finns en real tids klocka kan du använda den för att kontrol lera certifikatets förfallo datum (se API nx_secure_tls_session_time_function_set). Verifiering av certifikat tillägg och andra data är dock ansvaret för program Implementeraren.
- Programvarubaserad kryptografi är processor intensiv. NetX säkra programvarubaserade kryptografiska rutiner har optimerats för prestanda, men beroende på processor kraft, kan prestandan leda till mycket långa åtgärder. När maskinvarubaserad kryptografi är tillgängligt bör den användas för optimala prestanda för NetX Secure TLS.
- Det finns inte stöd för att registrera fragmentering i TLS-handskakning. Om vissa meddelanden om TLS-handskakning är för stora kan de delas upp i flera TLS-poster – NetX Secure TLS behandlar för närvarande detta som ett fel. Minnes kraven för inbäddade system innebär att det större handskaknings meddelandet troligen inte kan hanteras trots att begränsningen kan leda till fel vid kommunikation med vissa TLS-värdar som använder mycket stora certifikat kedjor.
- TLS-servern har inte stöd för val av dynamiskt certifikat när det finns flera certifikat i det lokala arkivet. 
- Felaktig användning av X509-certifikat observeras inte. 
- ECDH-baserade krypteringssviter stöds inte. Använd ECDHE i stället.
