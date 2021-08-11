---
title: Kapitel 3 – Funktionsbeskrivning av Azure RTOS NetX Crypto
description: Det här kapitlet innehåller en funktionell beskrivning av NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8aa49c130dc2802e95620ccdd4f4d9398c3fd2e55f5896d004e47baa72829848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796766"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>Kapitel 3 – Funktionsbeskrivning av Azure RTOS NetX Crypto

## <a name="execution-overview"></a>Körningsöversikt

Det här kapitlet innehåller en funktionell beskrivning av Azure RTOS NetX Crypto. Det finns två primära typer av programkörning i ett NetX Crypto-program: initiering och anrop till programgränssnitt.

*NetX Crypto kan användas som ett fristående kryptografiskt bibliotek eller användas med ThreadX, NetX och/eller NetX Secure.*

## <a name="aes"></a>AES

- **Algoritmstandard:** NetX Crypto implementerar AES enligt NIST FIPS 197, som finns på: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- **Nyckellängder som stöds:** 128, 192, 256
- **Lägen som stöds:**
  - CBC, CTR, (Nyckellängd 128-, 192-, 256-bitars)
  - XCBC (nyckellängd endast 128 bitar),
  - CCM8 (nyckellängd endast 128 bitar)
- **Minneskrav:** Programmet anger indatabuffert och utdatabuffert och en AES-kontrollstruktur. AES-kontrollstrukturen upprätthåller AES-algoritmtillståndet mellan anrop till API:et. Indatabufferten innehåller data som ska krypteras eller dekrypteras och kan vara godtycklig storlek. Utdatabufferten används av AES för att lagra data som bearbetas av AES. Utdatabuffertens storlek får inte vara mindre än indatabuffertens storlek och måste vara en multipel på 16 byte, AES-blockstorleken. Indata- och utdatabuffertarna måste vara sammanhängande minne och får inte överlappa varandra, förutom i det särskilda fallet med kryptering på plats (med samma minne för indata och utdata). När du krypterar på plats börjar utdatabufferten på exakt samma plats som indatabufferten och får inte vara mindre än indatabufferten. När AES-kryptering fungerar på plats krävs inget extra minne.

## <a name="3des"></a>3DES

- **Algoritmstandard:** NetX Crypto implementerar Tripple DES(TDES, även kallat 3DES) enligt NIST Special Publication 800-67 rev 2: *"Recommendataion for the Triple Data Encryption Algorithm (TDES) Block Cipher"*, som finns på: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)
- **Nyckellängd som** stöds: 64 * 3 = 192
- **Minnesrequreiment:**: Ingen

I NetX Crypto används termen "3DES" synonymt med "TDES".

## <a name="md5"></a>MD5

- **Algoritmstandard:** NetX Crypto implementerar MD5 enligt RFC 1321: *"The MD5 Message-Digest Algorithm"*
- **Minneskrav:** Programmet måste tillhandahålla en MD5-kontrollblocksstruktur som används för att upprätthålla tillståndet mellan MD5-åtgärder.

## <a name="sha1-sha256512"></a>SHA1, SHA256/512

- **Algoritmstandard:** NetX Crypto implementerar SHA1/256/512 enligt NIST FIPS publication 180-4: "*Secure Hash Standard*", som finns på: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- **Hash-blockstorlek:**:
  - SHA1: 160-bitars hash-värde
  - SHA 224: 224-bitars hashvärde
  - SHA 256: 256-bitars hashvärde
  - SHA 384: 384-bitars hashvärde
  - SHA 512: 512-bitars hashvärde
  - SHA 512/224: 224-bitars hashvärde
  - SHA 512/256: 256-bitars hashvärde

  I NetX Crypto används SHA256-rutiner för SHA256 och SHA224. SHA512-rutiner används för att handa SHA512, SHA384, SHA512/224 och SHA512/256.
- **Minneskrav:** Programmet måste tillhandahålla en SHA-kontrollblocksstruktur för att upprätthålla tillståndet mellan åtgärder.

## <a name="rsa"></a>RSA

- **Standard:** NetX Crypto implementerar RSA enligt standarden "*PKCS #1 v2.2: RSA Cryptography Standard*", som publiceras som RFC 8017 och finns också på: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)
- **Minneskrav:** Programmet måste tillhandahålla en RSA-kontrollblockstruktur för att upprätthålla tillståndet mellan åtgärder och för att tillhandahålla nödvändigt "scratch"-buffertutrymme för mellanliggande beräkningar.

## <a name="hmac"></a>Hmac

- **Standard:** NetX Crypto implementerar HMAC enligt FIPS PUB 198-1: "*The Keyed-Hash Message Authentication Code (HMAC)*", som finns på: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)
- **Minneskrav:** Programmet måste tillhandahålla en HMAC-kontrollblocksstruktur för att upprätthålla tillståndet mellan åtgärder. Det faktiska kontrollblocket som tillhandahålls beror på den önskade underliggande hash-åtgärden (t.ex. SHA1, MD5).

## <a name="elliptic-curve"></a>Elliptic Curve

- **Standard:** NetX Crypto implementerar Elliptic Curve. De namngivna kurvor som stöds är (endast primtalsfält):
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > Okomprimerat format stöds. Se avsnitt 2.3.3 och 2.3.4 i SEC1-v1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)

- **Minneskrav:** Ingen

## <a name="ecdsa"></a>ECDSA

- **Standard:** NetX Crypto implementerar ECDSA enligt FIPS PUB 186-4: "*Digital Signature Standard (DSS)*", som finns på: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)
- **Minneskrav:** Programmet måste tillhandahålla en ECDSA-kontrollblockstruktur för att upprätthålla tillståndet mellan åtgärder.

## <a name="ecdh"></a>ECDH

> [!IMPORTANT]
> I Azure RTOS 6.0 bör ECDH-rutiner endast användas för ECDHE-kryptografi eftersom ECDH med en statisk privat nyckel kräver att valideringen av indatapunkten är säker.

- **Standard:** NetX Crypto implementerar ECDH enligt FIPS PUB 800-56Ar2: "Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography", som finns på: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)
- **Minneskrav:** Programmet måste tillhandahålla en ECDH-kontrollblocksstruktur för att upprätthålla tillståndet mellan åtgärder.

## <a name="drbg"></a>DRBG

- **Standard:** NetX Crypto implementerar DRBG enligt FIPS PUB 800-90Ar1: "Recommendation for Random Number Generation Using Deterministic Random Bit Generators", som finns på: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)
- **Minneskrav:** Programmet måste tillhandahålla en DRBG-kontrollblocksstruktur för att upprätthålla tillståndet mellan åtgärder.

## <a name="fips-compliant"></a>FIPS-Compliant

NetX Crypto FIPS 140-2