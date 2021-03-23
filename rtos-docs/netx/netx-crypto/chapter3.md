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
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a><span data-ttu-id="65e66-103">Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX-kryptografi</span><span class="sxs-lookup"><span data-stu-id="65e66-103">Chapter 3 - Functional description of Azure RTOS NetX Crypto</span></span>

## <a name="execution-overview"></a><span data-ttu-id="65e66-104">Översikt över körning</span><span class="sxs-lookup"><span data-stu-id="65e66-104">Execution Overview</span></span>

<span data-ttu-id="65e66-105">Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX-kryptografi.</span><span class="sxs-lookup"><span data-stu-id="65e66-105">This chapter contains a functional description of Azure RTOS NetX Crypto.</span></span> <span data-ttu-id="65e66-106">Det finns två primära typer av program körning i ett NetX-krypto-program: initierings-och program gränssnitts anrop.</span><span class="sxs-lookup"><span data-stu-id="65e66-106">There are two primary types of program execution in a NetX Crypto application: initialization and application interface calls.</span></span>

<span data-ttu-id="65e66-107">*NetX-kryptografi kan användas som ett fristående kryptografiskt bibliotek eller användas med ThreadX, NetX och/eller NetX Secure.*</span><span class="sxs-lookup"><span data-stu-id="65e66-107">*NetX Crypto can be used as a standalone cryptographic library, or can be used with ThreadX, NetX, and/or NetX Secure.*</span></span>

## <a name="aes"></a><span data-ttu-id="65e66-108">AES</span><span class="sxs-lookup"><span data-stu-id="65e66-108">AES</span></span>

- <span data-ttu-id="65e66-109">**Algoritm standard:**: netx-kryptografi implementerar AES enligt NIST FIPS 197, som finns på: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-109">**Algorithm Standard:**:  NetX Crypto implements AES according to NIST FIPS 197, which can be found at: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)</span></span>
- <span data-ttu-id="65e66-110">**Nyckel längder som stöds**: 128, 192, 256</span><span class="sxs-lookup"><span data-stu-id="65e66-110">**Key Lengths Supported**: 128, 192, 256</span></span>
- <span data-ttu-id="65e66-111">**Lägen som stöds**:</span><span class="sxs-lookup"><span data-stu-id="65e66-111">**Modes Supported**:</span></span>
  - <span data-ttu-id="65e66-112">CBC,/maskin, (nyckel längd 128-, 192-, 256-bitar)</span><span class="sxs-lookup"><span data-stu-id="65e66-112">CBC, CTR, (Key length 128-, 192-, 256-bit)</span></span>
  - <span data-ttu-id="65e66-113">XCBC (nyckel längd 128-endast bit),</span><span class="sxs-lookup"><span data-stu-id="65e66-113">XCBC (key length 128-bit only),</span></span>
  - <span data-ttu-id="65e66-114">CCM8 (nyckel längd 128-endast bit)</span><span class="sxs-lookup"><span data-stu-id="65e66-114">CCM8 (key length 128-bit only)</span></span>
- <span data-ttu-id="65e66-115">**Minnes krav**: Application anger indatabufferten och utdatabufferten och en AES-kontroll struktur.</span><span class="sxs-lookup"><span data-stu-id="65e66-115">**Memory Requirements**: Application specifies input buffer and output buffer and an AES control structure.</span></span> <span data-ttu-id="65e66-116">AES-kontroll strukturen upprätthåller AES-algoritmen mellan anrop till API: et.</span><span class="sxs-lookup"><span data-stu-id="65e66-116">The AES control structure maintains AES algorithm state between calls to the API.</span></span> <span data-ttu-id="65e66-117">Indatabufferten innehåller data som ska krypteras eller dekrypteras och kan vara godtyckliga.</span><span class="sxs-lookup"><span data-stu-id="65e66-117">The input buffer contains data to be encrypted or decrypted, and can be arbitrary size.</span></span> <span data-ttu-id="65e66-118">Utdatabufferten används av AES för att lagra data som bearbetas av AES.</span><span class="sxs-lookup"><span data-stu-id="65e66-118">The output buffer is used by AES to store data being processed by AES.</span></span> <span data-ttu-id="65e66-119">Buffertens storlek får inte vara mindre än den angivna buffertstorleken och måste vara en multipel av 16 byte, AES-blockets storlek.</span><span class="sxs-lookup"><span data-stu-id="65e66-119">The output buffer size must be no smaller than the input buffer size, and must be a multiple of 16 bytes, the AES block size.</span></span> <span data-ttu-id="65e66-120">Indata-och utdatabuffert måste vara sammanhängande minne och får inte överlappa varandra, förutom i det särskilda fallet med kryptering på plats (med samma minne för indata och utdata).</span><span class="sxs-lookup"><span data-stu-id="65e66-120">The input and output buffers must be contiguous memory and may not overlap, except in the special case of encrypting in-place (using the same memory for input and output).</span></span> <span data-ttu-id="65e66-121">Vid kryptering på plats startar utdatabufferten på exakt samma plats som indatabufferten och får inte vara mindre än indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="65e66-121">When encrypting in-place, the output buffer starts at exactly the same location as the input buffer, and must be no smaller than the input buffer.</span></span> <span data-ttu-id="65e66-122">När AES-kryptering fungerar på plats krävs inget extra minne.</span><span class="sxs-lookup"><span data-stu-id="65e66-122">When AES encryption operates in-place no extra scratch memory is required.</span></span>

## <a name="3des"></a><span data-ttu-id="65e66-123">3DES</span><span class="sxs-lookup"><span data-stu-id="65e66-123">3DES</span></span>

- <span data-ttu-id="65e66-124">**Algoritm standard**: netx-kryptografi implementerar Tripple des (TDES, även kallat 3DES) enligt NIST Special publikation 800-67 rev 2: *"Recommendataion för tredubbel data krypteringsalgoritm (TDES) block chiffer"*, som finns på: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)</span><span class="sxs-lookup"><span data-stu-id="65e66-124">**Algorithm Standard**: NetX Crypto implements Tripple DES(TDES, also known as 3DES) according to NIST Special Publication 800-67 rev 2: *"Recommendataion for the Triple Data Encryption Algorithm (TDES) Block Cipher"*, which can be found at: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)</span></span>
- <span data-ttu-id="65e66-125">**Nyckel längd som stöds**: 64 \* 3 = 192</span><span class="sxs-lookup"><span data-stu-id="65e66-125">**Key Length Supported**: 64 \* 3 = 192</span></span>
- <span data-ttu-id="65e66-126">**Requreiment för minne:**: ingen</span><span class="sxs-lookup"><span data-stu-id="65e66-126">**Memory Requreiment:**: None</span></span>

<span data-ttu-id="65e66-127">I NetX-kryptering används termen "3DES" med "TDES".</span><span class="sxs-lookup"><span data-stu-id="65e66-127">In NetX Crypto, the term "3DES" is used interchangeably with "TDES".</span></span>

## <a name="md5"></a><span data-ttu-id="65e66-128">MD5</span><span class="sxs-lookup"><span data-stu-id="65e66-128">MD5</span></span>

- <span data-ttu-id="65e66-129">**Algoritm standard**: netx-kryptografi implementerar MD5 enligt RFC 1321: *"MD5 Message-Digest algorithm"*</span><span class="sxs-lookup"><span data-stu-id="65e66-129">**Algorithm Standard**: NetX Crypto implements MD5 according to RFC 1321: *"The MD5 Message-Digest Algorithm"*</span></span>
- <span data-ttu-id="65e66-130">**Minnes krav**: programmet måste tillhandahålla en MD5-kontroll block struktur som används för att underhålla tillstånd mellan MD5-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="65e66-130">**Memory Requirement**: The application must supply an MD5 control block structure, used to maintain state between MD5 operations.</span></span>

## <a name="sha1-sha256512"></a><span data-ttu-id="65e66-131">SHA1, SHA256/512</span><span class="sxs-lookup"><span data-stu-id="65e66-131">SHA1, SHA256/512</span></span>

- <span data-ttu-id="65e66-132">**Algoritm standard:** NetX-kryptering implementerar SHA1/256/512 enligt NIST FIPS-publikation 180-4: "*Secure hash standard*", som finns på: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-132">**Algorithm Standard:** NetX Crypto implements SHA1/256/512 according to NIST FIPS publication 180-4: "*Secure Hash Standard*", which can be found at: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)</span></span>
- <span data-ttu-id="65e66-133">**Hash-block storlek:**:</span><span class="sxs-lookup"><span data-stu-id="65e66-133">**Hash block size:**:</span></span>
  - <span data-ttu-id="65e66-134">SHA1:160 bitar hash-värde</span><span class="sxs-lookup"><span data-stu-id="65e66-134">SHA1: 160 bits hash value</span></span>
  - <span data-ttu-id="65e66-135">SHA 224:224 bitar hash-värde</span><span class="sxs-lookup"><span data-stu-id="65e66-135">SHA 224: 224 bits hash value</span></span>
  - <span data-ttu-id="65e66-136">SHA 256:256 bitar hash-värde</span><span class="sxs-lookup"><span data-stu-id="65e66-136">SHA 256: 256 bits hash value</span></span>
  - <span data-ttu-id="65e66-137">SHA 384:384 bitar hash-värde</span><span class="sxs-lookup"><span data-stu-id="65e66-137">SHA 384: 384 bits hash value</span></span>
  - <span data-ttu-id="65e66-138">SHA 512:512 bitar hash-värde</span><span class="sxs-lookup"><span data-stu-id="65e66-138">SHA 512: 512 bits hash value</span></span>
  - <span data-ttu-id="65e66-139">SHA 512/224:224-bitars hash-värde</span><span class="sxs-lookup"><span data-stu-id="65e66-139">SHA 512/224: 224 bits hash value</span></span>
  - <span data-ttu-id="65e66-140">SHA 512/256:256-bitars hash-värde</span><span class="sxs-lookup"><span data-stu-id="65e66-140">SHA 512/256: 256 bits hash value</span></span>

  <span data-ttu-id="65e66-141">I NetX-kryptering används SHA256-rutiner för hadn SHA256 och SHA224.</span><span class="sxs-lookup"><span data-stu-id="65e66-141">In NetX Crypto, SHA256 routines are used to hadn SHA256 and SHA224.</span></span> <span data-ttu-id="65e66-142">SHA512-rutiner används för att SHA512, SHA384, SHA512/224 och SHA512/256.</span><span class="sxs-lookup"><span data-stu-id="65e66-142">SHA512 routines are used to hand SHA512, SHA384, SHA512/224 and SHA512/256.</span></span>
- <span data-ttu-id="65e66-143">**Minnes krav:** Programmet måste tillhandahålla en SHA Control Block-struktur för att bibehålla tillstånd mellan åtgärder.</span><span class="sxs-lookup"><span data-stu-id="65e66-143">**Memory Requirement:** The application must provide a SHA control block structure for maintaining state between operations.</span></span>

## <a name="rsa"></a><span data-ttu-id="65e66-144">RSA</span><span class="sxs-lookup"><span data-stu-id="65e66-144">RSA</span></span>

- <span data-ttu-id="65e66-145">**Standard:** NetX-kryptering implementerar RSA enligt standarden "*PKCS #1 v 2.2: RSA Cryptography Standard*", som publiceras som RFC 8017 och finns på: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-145">**Standard:** NetX Crypto implements RSA according to the standard "*PKCS #1 v2.2: RSA Cryptography Standard*", which is published as RFC 8017 and can also be found at: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)</span></span>
- <span data-ttu-id="65e66-146">**Minnes krav:** Programmet måste tillhandahålla en RSA Control Block-struktur för att bibehålla tillstånd mellan åtgärder och för att tillhandahålla nödvändigt "Scratch" buffertutrymme för mellanliggande beräkningar.</span><span class="sxs-lookup"><span data-stu-id="65e66-146">**Memory Requirement:** The application must provide an RSA control block structure for maintaining state between operations and to provide necessary "scratch" buffer space for intermediate calculations.</span></span>

## <a name="hmac"></a><span data-ttu-id="65e66-147">HMAC</span><span class="sxs-lookup"><span data-stu-id="65e66-147">HMAC</span></span>

- <span data-ttu-id="65e66-148">**Standard:** NetX-kryptografi implementerar HMAC enligt FIPS PUB 198-1: "*Keyed-Hash Message Authentication Code (HMAC)*", som finns på: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-148">**Standard:** NetX Crypto implements HMAC according to FIPS PUB 198-1: "*The Keyed-Hash Message Authentication Code (HMAC)*", which can be found at: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)</span></span>
- <span data-ttu-id="65e66-149">**Minnes krav:** Programmet måste tillhandahålla en block struktur för HMAC-kontroll för att bibehålla tillstånd mellan åtgärder.</span><span class="sxs-lookup"><span data-stu-id="65e66-149">**Memory Requirement:** The application must provide an HMAC control block structure for maintaining state between operations.</span></span> <span data-ttu-id="65e66-150">Själva kontroll blocket som anges beror på den önskade underliggande hash-åtgärden (t. ex. SHA1, MD5).</span><span class="sxs-lookup"><span data-stu-id="65e66-150">The actual control block supplied depends on the desired underlying hash operation (e.g. SHA1, MD5).</span></span>

## <a name="elliptic-curve"></a><span data-ttu-id="65e66-151">Elliptic kurva</span><span class="sxs-lookup"><span data-stu-id="65e66-151">Elliptic Curve</span></span>

- <span data-ttu-id="65e66-152">**Standard:** NetX-kryptografi implementerar Elliptic-kurvan.</span><span class="sxs-lookup"><span data-stu-id="65e66-152">**Standard:** NetX Crypto implements Elliptic Curve.</span></span> <span data-ttu-id="65e66-153">Namngivna kurvor som stöds är (endast primärt fält):</span><span class="sxs-lookup"><span data-stu-id="65e66-153">The supported named curves are (prime field only):</span></span>
  - <span data-ttu-id="65e66-154">P-192</span><span class="sxs-lookup"><span data-stu-id="65e66-154">P-192</span></span>
  - <span data-ttu-id="65e66-155">P-224</span><span class="sxs-lookup"><span data-stu-id="65e66-155">P-224</span></span>
  - <span data-ttu-id="65e66-156">P-256</span><span class="sxs-lookup"><span data-stu-id="65e66-156">P-256</span></span>
  - <span data-ttu-id="65e66-157">P-384</span><span class="sxs-lookup"><span data-stu-id="65e66-157">P-384</span></span>
  - <span data-ttu-id="65e66-158">P-521</span><span class="sxs-lookup"><span data-stu-id="65e66-158">P-521</span></span>

   > [!TIP]
   > <span data-ttu-id="65e66-159">Okomprimerat format stöds.</span><span class="sxs-lookup"><span data-stu-id="65e66-159">Uncompressed format is supported.</span></span> <span data-ttu-id="65e66-160">Se avsnitt 2.3.3 och 2.3.4 i SEC1-V1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-160">See section 2.3.3 and 2.3.4 of SEC1-v1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)</span></span>

- <span data-ttu-id="65e66-161">**Minnes krav:** Alternativet</span><span class="sxs-lookup"><span data-stu-id="65e66-161">**Memory Requirement:** None</span></span>

## <a name="ecdsa"></a><span data-ttu-id="65e66-162">ECDSA</span><span class="sxs-lookup"><span data-stu-id="65e66-162">ECDSA</span></span>

- <span data-ttu-id="65e66-163">**Standard:** NetX-kryptografi implementerar ECDSA enligt FIPS PUB 186-4: "*Digital Signature standard (DSS)*", som finns på: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-163">**Standard:** NetX Crypto implements ECDSA according to FIPS PUB 186-4: "*Digital Signature Standard (DSS)*", which can be found at: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)</span></span>
- <span data-ttu-id="65e66-164">**Minnes krav:** Programmet måste tillhandahålla en ECDSA-kontroll block struktur för att bibehålla tillstånd mellan åtgärder.</span><span class="sxs-lookup"><span data-stu-id="65e66-164">**Memory Requirement:** The application must provide an ECDSA control block structure for maintaining state between operations.</span></span>

## <a name="ecdh"></a><span data-ttu-id="65e66-165">ECDH</span><span class="sxs-lookup"><span data-stu-id="65e66-165">ECDH</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65e66-166">I Azure återställnings tider 6,0 bör ECDH-rutiner endast användas för ECDHE-kryptografi eftersom ECDH med en statisk privat nyckel kräver att ingångs punkts verifiering är säker.</span><span class="sxs-lookup"><span data-stu-id="65e66-166">In Azure RTOS 6.0, ECDH routines should only be used for ECDHE cryptography as ECDH with a static private key requires input point validation to be secure.</span></span>

- <span data-ttu-id="65e66-167">**Standard:** NetX-kryptografi implementerar ECDH enligt FIPS PUB 800-56Ar2: "rekommendation för Pair-Wise nyckel etablerings scheman som använder diskret logaritmisk kryptering", som finns på: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-167">**Standard:** NetX Crypto implements ECDH according to FIPS PUB 800-56Ar2: "Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography", which can be found at: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)</span></span>
- <span data-ttu-id="65e66-168">**Minnes krav:** Programmet måste tillhandahålla en ECDH-kontroll block struktur för att bibehålla tillstånd mellan åtgärder.</span><span class="sxs-lookup"><span data-stu-id="65e66-168">**Memory Requirement:** The application must provide an ECDH control block structure for maintaining state between operations.</span></span>

## <a name="drbg"></a><span data-ttu-id="65e66-169">DRBG</span><span class="sxs-lookup"><span data-stu-id="65e66-169">DRBG</span></span>

- <span data-ttu-id="65e66-170">**Standard:** NetX-kryptografi implementerar DRBG enligt FIPS PUB 800-90Ar1: "rekommendation för slumpmässig numrering med deterministiska slumpmässiga bit generatorer", som finns på: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)</span><span class="sxs-lookup"><span data-stu-id="65e66-170">**Standard:** NetX Crypto implements DRBG according to FIPS PUB 800-90Ar1: "Recommendation for Random Number Generation Using Deterministic Random Bit Generators", which can be found at: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)</span></span>
- <span data-ttu-id="65e66-171">**Minnes krav:** Programmet måste tillhandahålla en DRBG-kontroll block struktur för att bibehålla tillstånd mellan åtgärder.</span><span class="sxs-lookup"><span data-stu-id="65e66-171">**Memory Requirement:** The application must provide an DRBG control block structure for maintaining state between operations.</span></span>

## <a name="fips-compliant"></a><span data-ttu-id="65e66-172">FIPS-Compliant</span><span class="sxs-lookup"><span data-stu-id="65e66-172">FIPS-Compliant</span></span>

<span data-ttu-id="65e66-173">NetX krypto FIPS 140-2</span><span class="sxs-lookup"><span data-stu-id="65e66-173">NetX Crypto FIPS 140-2</span></span>