---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Crypto
description: NetX Crypto är en högpresterande realtidsimplementering av kryptografiska algoritmer som är utformade för att tillhandahålla tjänster för datakryptering och autentisering.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1b5ee0336ba9e867a628dc5db4f0c029f68ff45c81d68ceb6299e3469d5e2b49
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796811"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Crypto

Azure RTOS NetX Crypto är en högpresterande realtidsimplementering av kryptografiska algoritmer som är utformade för att tillhandahålla tjänster för datakryptering och autentisering. NetX Crypto är utformat för att ansluta till NetX Secure TLS-, DTLS- och IPsec-moduler. Program kan också använda NetX Crypto som en fristående modul utanför nätverkssäkerheten.

## <a name="netx-crypto-unique-features"></a>Unika funktioner i NetX Crypto

NetX Crypto implementeras i C-standardspråket (C99), som är kompatibelt med i stort sett alla C/C++-kompilatorer. Den modulära designen gör att ett program endast kan länka i de krypteringsalgoritmer som det behöver använda, vilket ger minimal kodstorlek. Implementeringen är utformad för att fungera med de flesta 32-bitars mikroprocessorer och använder endast de grundläggande matematikåtgärderna (addition, subtraktion, multiplikation, division, logiska AND-, OR-, NOR- och bitväxlingsåtgärder). Alla dessa åtgärder används med 32-bitars kvantiteter, vilket gör NetX Crypto portabel över de flesta 32-bitars mikroprocessorer. Implementeringen är särskilt optimerad för att köras på resursbegränsade mikroprocessorer med inriktning på djupt inbäddade program.

## <a name="algorithms-supported-by-netx-crypto"></a>Algoritmer som stöds av NetX Crypto

NetX Crypto stöder följande kryptografiska algoritmer. NetX Crypto följer alla allmänna rekommendationer och grundläggande krav inom begränsningarna för ett operativsystem och plattformar i realtid som kräver ett litet fotavtryck för minne och effektiv körning.

| Algoritm       | Nyckellängd (bitar)      |
| --------------- | ---------------------- |
| AES(CBC, CTR)   | 128, 192, 256          |
| AES (XCBC)       | 128                    |
| AES-CCM 8       | 128                    |
| 3DES(CBC)       | 192                    |
| HMAC-SHA1       | Valfri längd             |
| HMAC-SHA224     | Valfri längd             |
| HMAC-SHA256     | Valfri längd             |
| HMAC-SHA384     | Valfri längd             |
| HMAC-SHA512     | Valfri längd             |
| HMAC-SHA512/224 | Valfri längd             |
| HMAC-SHA512/256 | Valfri längd             |
| HMAC-MD5        | Valfri längd             |
| RSA             | 1024, 2048, 3072, 4096 |

| Algoritm       | Sammanfattad längd (bitar) | Blockstorlek (bitar) |
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
| Elliptic Curve  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>Krav för NetX-kryptografi

TBD: Minneskrav.. Avbryter/återerar säker? Diskussion om behov

## <a name="netx-crypto-constraints"></a>NetX Crypto-begränsningar

Inga.
