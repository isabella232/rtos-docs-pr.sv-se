---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Secure DTLS
description: Azure återställnings tider NetX Secure DTLS är en real tids implementering av Datagram Transport Layer Security-protokollet som är utformat för inbäddade ThreadX-baserade program.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbd81082524f50787765dfacf494248dda740fd6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826976"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>Kapitel 1: Introduktion till Azure återställnings tider NetX Secure DTLS

Azure återställnings tider NetX Secure DTLS är en real tids implementering av Datagram Transport Layer Security-protokollet som är utformad exklusivt för inbäddade ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX Secure DTLS och en beskrivning av dess program och fördelar.

## <a name="netx-secure-unique-features"></a>NetX säkra unika funktioner

Till skillnad från de flesta andra TLS/DTLS-implementeringar har NetX Secure utformats från grunden för att stödja en mängd olika inbäddade maskinvaruplattformar och skalas enkelt från små mikrokontrollants program till de mest kraftfulla inbäddade processorerna. Koden skrivs med begränsade resurser av inbäddade system i åtanke och innehåller ett antal konfigurations alternativ för att minska den minnes storlek som krävs för att tillhandahålla säker nätverkskommunikation via TLS eller DTLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC: er som stöds av NetX Secure

NetX Secure stöder följande protokoll som rör TLS och DTLS. Listan är inte nödvändigt vis omfattande eftersom det finns flera RFC: er som rör TLS/DTLS och kryptografi. NetX Secure följer alla allmänna rekommendationer och grundläggande krav inom begränsningar i ett operativ system i real tid med liten minnes storlek och effektiv körning.


| RFC | Beskrivning |
| --- | ----------- |
| RFC 6347 | Datagram Transport Layer Security version 1,2. |
| RFC 2246 | TLS-protokoll version 1,0|
| RFC 4346 | Transport Layer Security (TLS)-protokoll version 1,1 |
| RFC 5246 | Transport Layer Security (TLS)-protokoll version 1,2 |
| RFC 5280 | X. 509 PKI-certifikat (v3) |
| RFC 3268 | Advanced Encryption Standard (AES) krypteringssviter för Transport Layer Security (TLS) |
| RFC 3447 | Public-Key för kryptografi standarder (PKCS) #1: RSA Cryptography Specifications version 2,1 |
| RFC 2104 | HMAC: Keyed-Hashing för meddelandeautentisering |
| RFC 6234 | AMERIKANSKA säkra hash-algoritmer (SHA och SHA-baserad HMAC och HKDF) |
| RFC 4279 | Krypteringssviter i förväg delad nyckel för TLS |

## <a name="netx-secure-dtls-requirements"></a>NetX säkra DTLS-krav

För att kunna fungera korrekt kräver NetX-biblioteket för säker körning att en NetX-IP-instans redan har skapats. Och beroende på programmet, krävs ett eller flera DER-kodade X. 509-certifikat, antingen för att identifiera en TLS/DTLS-instans eller för att verifiera certifikat som kommer från en fjärrvärd. Det NetX säkra paketet har inga ytterligare krav.

## <a name="netx-secure-dtls-constraints"></a>NetX Secure DTLS-begränsningar

NetX Secure DTLS-protokollet implementerar kraven i RFC 6347-standarderna för DTLS 1,2. Det finns dock följande begränsningar:

1. På grund av typen av inbäddade enheter kanske vissa program inte har resurserna för att stödja den högsta TLS/DTLS-post storleken för 16 KB. NetX Secure kan hantera 16 KB-poster på enheter med tillräckligt med resurser.
2. Minimal certifikat verifiering. NetX Secure utför en grundläggande X. 509-på ett certifikat för att säkerställa att certifikatet är giltigt och signerat av en betrodd certifikat utfärdare, och kan ange certifikatets gemensamma namn för programmet som ska jämföras med Top-Level domän namnet för fjärrvärden. Verifiering av certifikat tillägg och andra data är dock ansvaret för program Implementeraren.
3. Programvarubaserad kryptografi är processor intensiv. NetX säkra programvarubaserade kryptografiska rutiner har optimerats för prestanda, men beroende på processor kraft, kan prestandan leda till mycket långa åtgärder. När maskinvarubaserad kryptografi är tillgängligt bör den användas för optimala prestanda för NetX Secure DTLS.
