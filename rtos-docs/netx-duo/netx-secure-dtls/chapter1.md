---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Secure DTLS
description: Azure RTOS NetX Secure DTLS är en realtidsimplementering av Datagram Transport Layer Security-protokollet som utformats för inbäddade ThreadX-baserade program.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a7fe51fd1e141c0c525a98986ca3058732b61843f8bd79bf24fc5ac986147501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797049"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>Kapitel 1: Introduktion till Azure RTOS NetX Secure DTLS

Azure RTOS NetX Secure DTLS är en högpresterande realtidsimplementering av Datagram Transport Layer Security-protokollet som utformats exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX Secure DTLS och en beskrivning av dess program och fördelar.

## <a name="netx-secure-unique-features"></a>Unika funktioner i NetX Secure

Till skillnad från de flesta andra TLS/DTLS-implementeringar har NetX Secure utformats från grunden för att stödja en mängd olika inbäddade maskinvaruplattformar och skalas enkelt från små mikrostyrenhetsprogram till de mest kraftfulla inbäddade processorerna som är tillgängliga. Koden skrivs med de begränsade resurserna i inbäddade system i åtanke och innehåller ett antal konfigurationsalternativ för att minska det minnesfotavtryck som krävs för att tillhandahålla säker nätverkskommunikation via TLS eller DTLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC:er som stöds av NetX Secure

NetX Secure stöder följande protokoll som är relaterade till TLS och DTLS. Listan är inte nödvändigtvis omfattande eftersom det finns flera RFC:er som rör TLS/DTLS och kryptografi. NetX Secure följer alla allmänna rekommendationer och grundläggande krav inom begränsningarna i ett realtidsoperativsystemet med litet minnesfotavtryck och effektiv körning.


| RFC | Description |
| --- | ----------- |
| RFC 6347 | Datagram Transport Layer Security version 1.2. |
| RFC 2246 | TLS-protokollversion 1.0|
| RFC 4346 | Protokollet Transport Layer Security (TLS) version 1.1 |
| RFC 5246 | Protokollet Transport Layer Security (TLS) version 1.2 |
| RFC 5280 | X.509 PKI-certifikat (v3) |
| RFC 3268 | Advanced Encryption Standard (AES)-chiffer för Transport Layer Security (TLS) |
| RFC 3447 | Public-Key Cryptography Standards (PKCS) #1: RSA Cryptography Specifications Version 2.1 |
| RFC 2104 | HMAC: Keyed-Hashing för meddelandeautentisering |
| RFC 6234 | US Secure Hash Algorithms (SHA and SHA-based HMAC and HKDF) |
| RFC 4279 | Chifferutorer med i förväg delad nyckel för TLS |

## <a name="netx-secure-dtls-requirements"></a>Krav för NetX Secure DTLS

För att netX Secure-körningsbiblioteket ska fungera korrekt krävs att en NetX IP-instans redan har skapats. Beroende på programmet krävs dessutom ett eller flera DER-kodade digitala X.509-certifikat, antingen för att identifiera en TLS/DTLS-instans eller för att verifiera certifikat som kommer från en fjärrvärd. NetX Secure-paketet har inga ytterligare krav.

## <a name="netx-secure-dtls-constraints"></a>Begränsningar för NetX Secure DTLS

NetX Secure DTLS-protokollet implementerar kraven för RFC 6347 Standard(s) för DTLS 1.2. Det finns dock följande begränsningar:

1. På grund av inbäddade enheter har vissa program kanske inte de resurser som krävs för den maximala TLS/DTLS-poststorleken på 16 kB. NetX Secure kan hantera poster på 16 kB på enheter med tillräckligt med resurser.
2. Minimal verifiering av certifikat. NetX Secure utför grundläggande X.509-kedjeverifiering på ett certifikat för att säkerställa att certifikatet är giltigt och signerat av en betrodd certifikatutfärdare och kan ange certifikatets eget namn för programmet att jämföra med fjärrvärdens Top-Level-domännamn. Verifiering av certifikattillägg och andra data är dock programföre implementerarens ansvar.
3. Programvarubaserad kryptografi är processorintensiv. NetX Secures programvarubaserade kryptografiska rutiner har optimerats för prestanda, men beroende på målprocessorns kraft kan den prestandan resultera i mycket långa åtgärder. När maskinvarubaserad kryptografi är tillgänglig bör den användas för optimala prestanda för NetX Secure DTLS.
