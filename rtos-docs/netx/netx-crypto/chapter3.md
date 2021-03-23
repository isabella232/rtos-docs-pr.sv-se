---
title: Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX-kryptografi
description: Det här kapitlet innehåller en funktions Beskrivning av NetX-kryptering.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4ecdbfe99daa000d109908f834b139dcaf321491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825593"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX-kryptografi

## <a name="execution-overview"></a>Översikt över körning

Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX-kryptografi. Det finns två primära typer av program körning i ett NetX-krypto-program: initierings-och program gränssnitts anrop.

*NetX-kryptografi kan användas som ett fristående kryptografiskt bibliotek eller användas med ThreadX, NetX och/eller NetX Secure.*

## <a name="aes"></a>AES

- **Algoritm standard:**: netx-kryptografi implementerar AES enligt NIST FIPS 197, som finns på: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- **Nyckel längder som stöds**: 128, 192, 256
- **Lägen som stöds**:
  - CBC,/maskin, (nyckel längd 128-, 192-, 256-bitar)
  - XCBC (nyckel längd 128-endast bit),
  - CCM8 (nyckel längd 128-endast bit)
- **Minnes krav**: Application anger indatabufferten och utdatabufferten och en AES-kontroll struktur. AES-kontroll strukturen upprätthåller AES-algoritmen mellan anrop till API: et. Indatabufferten innehåller data som ska krypteras eller dekrypteras och kan vara godtyckliga. Utdatabufferten används av AES för att lagra data som bearbetas av AES. Buffertens storlek får inte vara mindre än den angivna buffertstorleken och måste vara en multipel av 16 byte, AES-blockets storlek. Indata-och utdatabuffert måste vara sammanhängande minne och får inte överlappa varandra, förutom i det särskilda fallet med kryptering på plats (med samma minne för indata och utdata). Vid kryptering på plats startar utdatabufferten på exakt samma plats som indatabufferten och får inte vara mindre än indatabufferten. När AES-kryptering fungerar på plats krävs inget extra minne.

## <a name="3des"></a>3DES

- **Algoritm standard**: netx-kryptografi implementerar Tripple des (TDES, även kallat 3DES) enligt NIST Special publikation 800-67 rev 2: *"Recommendataion för tredubbel data krypteringsalgoritm (TDES) block chiffer"*, som finns på: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)
- **Nyckel längd som stöds**: 64 * 3 = 192
- **Requreiment för minne:**: ingen

I NetX-kryptering används termen "3DES" med "TDES".

## <a name="md5"></a>MD5

- **Algoritm standard**: netx-kryptografi implementerar MD5 enligt RFC 1321: *"MD5 Message-Digest algorithm"*
- **Minnes krav**: programmet måste tillhandahålla en MD5-kontroll block struktur som används för att underhålla tillstånd mellan MD5-åtgärder.

## <a name="sha1-sha256512"></a>SHA1, SHA256/512

- **Algoritm standard:** NetX-kryptering implementerar SHA1/256/512 enligt NIST FIPS-publikation 180-4: "*Secure hash standard*", som finns på: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- **Hash-block storlek:**:
  - SHA1:160 bitar hash-värde
  - SHA 224:224 bitar hash-värde
  - SHA 256:256 bitar hash-värde
  - SHA 384:384 bitar hash-värde
  - SHA 512:512 bitar hash-värde
  - SHA 512/224:224-bitars hash-värde
  - SHA 512/256:256-bitars hash-värde

  I NetX-kryptering används SHA256-rutiner för hadn SHA256 och SHA224. SHA512-rutiner används för att SHA512, SHA384, SHA512/224 och SHA512/256.
- **Minnes krav:** Programmet måste tillhandahålla en SHA Control Block-struktur för att bibehålla tillstånd mellan åtgärder.

## <a name="rsa"></a>RSA

- **Standard:** NetX-kryptering implementerar RSA enligt standarden "*PKCS #1 v 2.2: RSA Cryptography Standard*", som publiceras som RFC 8017 och finns på: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)
- **Minnes krav:** Programmet måste tillhandahålla en RSA Control Block-struktur för att bibehålla tillstånd mellan åtgärder och för att tillhandahålla nödvändigt "Scratch" buffertutrymme för mellanliggande beräkningar.

## <a name="hmac"></a>HMAC

- **Standard:** NetX-kryptografi implementerar HMAC enligt FIPS PUB 198-1: "*Keyed-Hash Message Authentication Code (HMAC)*", som finns på: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)
- **Minnes krav:** Programmet måste tillhandahålla en block struktur för HMAC-kontroll för att bibehålla tillstånd mellan åtgärder. Själva kontroll blocket som anges beror på den önskade underliggande hash-åtgärden (t. ex. SHA1, MD5).

## <a name="elliptic-curve"></a>Elliptic kurva

- **Standard:** NetX-kryptografi implementerar Elliptic-kurvan. Namngivna kurvor som stöds är (endast primärt fält):
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > Okomprimerat format stöds. Se avsnitt 2.3.3 och 2.3.4 i SEC1-V1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)

- **Minnes krav:** Alternativet

## <a name="ecdsa"></a>ECDSA

- **Standard:** NetX-kryptografi implementerar ECDSA enligt FIPS PUB 186-4: "*Digital Signature standard (DSS)*", som finns på: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)
- **Minnes krav:** Programmet måste tillhandahålla en ECDSA-kontroll block struktur för att bibehålla tillstånd mellan åtgärder.

## <a name="ecdh"></a>ECDH

> [!IMPORTANT]
> I Azure återställnings tider 6,0 bör ECDH-rutiner endast användas för ECDHE-kryptografi eftersom ECDH med en statisk privat nyckel kräver att ingångs punkts verifiering är säker.

- **Standard:** NetX-kryptografi implementerar ECDH enligt FIPS PUB 800-56Ar2: "rekommendation för Pair-Wise nyckel etablerings scheman som använder diskret logaritmisk kryptering", som finns på: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)
- **Minnes krav:** Programmet måste tillhandahålla en ECDH-kontroll block struktur för att bibehålla tillstånd mellan åtgärder.

## <a name="drbg"></a>DRBG

- **Standard:** NetX-kryptografi implementerar DRBG enligt FIPS PUB 800-90Ar1: "rekommendation för slumpmässig numrering med deterministiska slumpmässiga bit generatorer", som finns på: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)
- **Minnes krav:** Programmet måste tillhandahålla en DRBG-kontroll block struktur för att bibehålla tillstånd mellan åtgärder.

## <a name="fips-compliant"></a>FIPS-Compliant

NetX krypto FIPS 140-2