---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX-kryptografi
description: NetX-kryptografi är en real tids implementering av kryptografiska algoritmer som har utformats för att tillhandahålla data krypterings-och autentiserings tjänster.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0bde9be472584308894cfd702ccd014578afe753
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825596"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX-kryptografi

Azure återställnings tider NetX-kryptografi är en real tids implementering av kryptografiska algoritmer som är utformad för att tillhandahålla data krypterings-och autentiserings tjänster. NetX-kryptografi är utformat för att ansluta för NetX säkra TLS-, DTLS-och IPsec-moduler. Program kan också använda NetX-kryptografi som en fristående modul utanför nätverks säkerheten.

## <a name="netx-crypto-unique-features"></a>Unika funktioner för NetX-kryptografi

NetX-kryptering implementeras på standard språket C (C99), kompatibel med praktiskt taget alla C/C++-kompilatorer. Den modulära designen gör det möjligt för ett program att endast länka i de krypteringsalgoritmer som den behöver använda, vilket ger minimal kod storlek. Implementeringen har utformats för att fungera med de flesta 32-bitars mikroprocessorer och använder bara de grundläggande matematiska åtgärderna (addition, subtraktion, multiplikation, Division, logisk och, eller, eller, eller, och bit växlings åtgärder). Alla dessa åtgärder används med 32-bitars mängder, vilket gör NetX-kryptering portabelt över de flesta 32-bitars mikroprocessorer. Implementeringen är särskilt optimerad för att köras på resurs begränsade mikroprocessorer, vilket riktar sig till djupt inbäddade program.

## <a name="algorithms-supported-by-netx-crypto"></a>Algoritmer som stöds av NetX-kryptografi

NetX-kryptering stöder följande krypteringsalgoritmer. NetX-kryptering följer alla allmänna rekommendationer och grundläggande krav inom begränsningar i ett operativ system med real tid och plattformar som kräver liten minnes storlek och effektiv körning.

| Integritetsalgoritm       | Nyckel längd (bitar)      |
| --------------- | ---------------------- |
| AES (CBC,/MASKIN)   | 128, 192, 256          |
| AES (XCBC)       | 128                    |
| AES-CCM 8       | 128                    |
| 3DES (CBC)       | 192                    |
| HMAC-SHA1       | Valfri längd             |
| HMAC-SHA224     | Valfri längd             |
| HMAC-SHA256     | Valfri längd             |
| HMAC-SHA384     | Valfri längd             |
| HMAC-SHA512     | Valfri längd             |
| HMAC-SHA512/224 | Valfri längd             |
| HMAC-SHA512/256 | Valfri längd             |
| HMAC-MD5        | Valfri längd             |
| RSA             | 1024, 2048, 3072, 4096 |

| Integritetsalgoritm       | Digest-längd (bitar) | Block storlek (bitar) |
| --------------- | -------------------- | ----------------- |
| SHA1            | 160                  | 512               |
| SHA224          | 224                  | 512               |
| SHA256          | 256                  | 512               |
| SHA384          | 384                  | 1024              |
| SHA512          | 512                  | 1024              |
| MD5             | 128                  | 512               |
| HMAC-SHA1       | 160                  | 512               |
| HMAC-SHA224     | 224                  | 512               |
| HMAC-SHA256     | 256                  | 512               |
| HMAC-SHA384     | 384                  | 1024              |
| HMAC-SHA512     | 512                  | 1024              |
| HMAC-SHA512/224 | 224                  | 1024              |
| HMAC-SHA512/256 | 256                  | 1024              |
| HMAC-MD5        | 128                  | 512               |
| Elliptic kurva  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>Krav för NetX-kryptering

TBD: minnes krav.. Vill du avbryta/återställa? Behöver diskussion

## <a name="netx-crypto-constraints"></a>Begränsningar för NetX-kryptografi

Inga.
