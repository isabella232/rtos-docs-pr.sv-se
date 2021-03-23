---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX krypto API
description: Beskrivning av Azure återställnings tider NetX-kryptografi-API
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826811"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a><span data-ttu-id="c23c4-103">Kapitel 4 – Beskrivning av Azure återställnings tider NetX krypto API</span><span class="sxs-lookup"><span data-stu-id="c23c4-103">Chapter 4 - Azure RTOS NetX Crypto API description</span></span>

## <a name="nx_crypto_initialize"></a><span data-ttu-id="c23c4-104">nx_crypto_initialize</span><span class="sxs-lookup"><span data-stu-id="c23c4-104">nx_crypto_initialize</span></span>

<span data-ttu-id="c23c4-105">Initierar NetX säkra bibliotek</span><span class="sxs-lookup"><span data-stu-id="c23c4-105">Initializes the NetX Secure Library</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-106">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-106">Prototype</span></span>

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="c23c4-107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-107">Description</span></span>

<span data-ttu-id="c23c4-108">Den här funktionen initierar modulen Azure återställnings tider NetX krypto-bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-108">This function initializes the Azure RTOS NetX Crypto library module.</span></span> <span data-ttu-id="c23c4-109">Innan du använder någon av de andra krypterings funktionerna måste programmet anropa den här funktionen för att utföra initiering och för att verifiera bibliotekets integritet.</span><span class="sxs-lookup"><span data-stu-id="c23c4-109">Before using any of the other cryptographic functions, the application must call this function to perform initialization and to validate the integrity of the library.</span></span> <span data-ttu-id="c23c4-110">Om du inte anropar den här funktionen innan du använder andra NetX-krypto-tjänster leder det till att fel returneras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-110">Failure to call this function before using other NetX Crypto services will result in errors being returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-111">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-111">Parameters</span></span>

- <span data-ttu-id="c23c4-112">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="c23c4-112">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-113">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-113">Return Values</span></span>

- <span data-ttu-id="c23c4-114">**NX_CRYPTO_SUCCESS** (0x00) initiering av netx-kryptografi bibliotek lyckades.</span><span class="sxs-lookup"><span data-stu-id="c23c4-114">**NX_CRYPTO_SUCCESS** (0x00) Successful initialized NetX Crypto library.</span></span> <span data-ttu-id="c23c4-115">Biblioteks funktionerna är nu klara och kan användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-115">The library functions are now ready, and can be used.</span></span>
- <span data-ttu-id="c23c4-116">**NX_CRYPTO_INVALID_LIBRARY** (0X20001) Det gick inte att initiera kryptografi biblioteket eller också går det inte att utföra integritets kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library fails to initialize, or fails the integrity check.</span></span> <span data-ttu-id="c23c4-117">Programmet kan inte använda det här biblioteket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-117">Application cannot use this library.</span></span>

### <a name="example"></a><span data-ttu-id="c23c4-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="c23c4-118">Example</span></span>

<span data-ttu-id="c23c4-119">ATT göra</span><span class="sxs-lookup"><span data-stu-id="c23c4-119">TODO</span></span>

## <a name="nx_crypto_module_state_get"></a><span data-ttu-id="c23c4-120">nx_crypto_module_state_get</span><span class="sxs-lookup"><span data-stu-id="c23c4-120">nx_crypto_module_state_get</span></span>

<span data-ttu-id="c23c4-121">Hämta aktuell status för den FIPS-aktiverade modulen</span><span class="sxs-lookup"><span data-stu-id="c23c4-121">Retrieve the current status of the FIPS-enabled module</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-122">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-122">Prototype</span></span>

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a><span data-ttu-id="c23c4-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-123">Description</span></span>

<span data-ttu-id="c23c4-124">Den här tjänsten är bara tillgänglig i FIPS build-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-124">This service is only available in the FIPS build library.</span></span> <span data-ttu-id="c23c4-125">Den returnerar statusen för det aktuella läget för NetX-krypto-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-125">It returns the state of the current state of the NetX Crypto library.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-126">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-126">Parameters</span></span>

- <span data-ttu-id="c23c4-127">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="c23c4-127">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-128">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-128">Return Values</span></span>

- <span data-ttu-id="c23c4-129">**Status flagga:**</span><span class="sxs-lookup"><span data-stu-id="c23c4-129">**Status Flag:**</span></span>
  - <span data-ttu-id="c23c4-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span><span class="sxs-lookup"><span data-stu-id="c23c4-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span></span>
  - <span data-ttu-id="c23c4-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span><span class="sxs-lookup"><span data-stu-id="c23c4-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span></span>
  - <span data-ttu-id="c23c4-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span><span class="sxs-lookup"><span data-stu-id="c23c4-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span></span>
  - <span data-ttu-id="c23c4-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span><span class="sxs-lookup"><span data-stu-id="c23c4-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span></span>
  - <span data-ttu-id="c23c4-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span><span class="sxs-lookup"><span data-stu-id="c23c4-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span></span>
- <span data-ttu-id="c23c4-135">**Alla andra värden är ogiltiga.**</span><span class="sxs-lookup"><span data-stu-id="c23c4-135">**All other values are invalid.**</span></span>

### <a name="example"></a><span data-ttu-id="c23c4-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="c23c4-136">Example</span></span>

<span data-ttu-id="c23c4-137">ATT göra</span><span class="sxs-lookup"><span data-stu-id="c23c4-137">TODO</span></span>

## <a name="_nx_crypto_method_aes_init"></a><span data-ttu-id="c23c4-138">_nx_crypto_method_aes_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-138">_nx_crypto_method_aes_init</span></span>

<span data-ttu-id="c23c4-139">Initierar kontroll block för AES-kryptografi</span><span class="sxs-lookup"><span data-stu-id="c23c4-139">Initializes the AES crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-140">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-140">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-141">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-141">Description</span></span>

<span data-ttu-id="c23c4-142">Den här funktionen initierar AES-kontroll-blocket med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-142">This function initializes the AES control block with the given key string.</span></span> <span data-ttu-id="c23c4-143">När AES-Kontrollpanelen har initierats använder den efterföljande AES-åtgärden samma nyckel och nyckel storlek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-143">Once the AES control block is initialized, subsequent AES operation will be using the same key and key size.</span></span>

<span data-ttu-id="c23c4-144">Programmet kan skapa flera AES-kontroll block, som representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-144">Application may create multiple AES control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-145">En nyckel tilldelas ett kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-145">A key is assigned to a control block.</span></span> <span data-ttu-id="c23c4-146">Efterföljande krypterings-eller krypterings åtgärder kan referera till samma AES-kontroll block utan att behöva initiera AES-kontroll blocket igen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-146">Subsequent encryption or decryption operation can reference to the same AES control block without the need to re-initialize the AES control block.</span></span> <span data-ttu-id="c23c4-147">Om nyckeln för sessionen har ändrats måste programmet initiera om AES-kontrolls-blocket med den uppdaterade nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-147">If the key for the session is changed, application needs to re-initialize AES control block with the updated key.</span></span>

<span data-ttu-id="c23c4-148">Anrop _ *nx_crypto_method_aes_init ()* uppdaterar automatiskt en tidigare konfigurerad nyckel och nyckel storlek till den nya nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-148">Calling _ *nx_crypto_method_aes_init()* automatically updates a previously configured key and key size to the new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-149">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-149">Parameters</span></span>

- <span data-ttu-id="c23c4-150">**metod** Pekar på ett giltigt kontroll block för AES-krypto.</span><span class="sxs-lookup"><span data-stu-id="c23c4-150">**method** Pointer to a valid AES crypto method control block.</span></span> <span data-ttu-id="c23c4-151">Följande fördefinierade AES-krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-151">The following pre-defined AES crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-152">*crypto_method_aes_cbc_128*</span><span class="sxs-lookup"><span data-stu-id="c23c4-152">*crypto_method_aes_cbc_128*</span></span>
  - <span data-ttu-id="c23c4-153">*crypto_method_aes_cbc_192*</span><span class="sxs-lookup"><span data-stu-id="c23c4-153">*crypto_method_aes_cbc_192*</span></span>
  - <span data-ttu-id="c23c4-154">*crypto_method_aes_cbc_256*</span><span class="sxs-lookup"><span data-stu-id="c23c4-154">*crypto_method_aes_cbc_256*</span></span>
  - <span data-ttu-id="c23c4-155">*crypto_method_aes_ctr_128*</span><span class="sxs-lookup"><span data-stu-id="c23c4-155">*crypto_method_aes_ctr_128*</span></span>
  - <span data-ttu-id="c23c4-156">*crypto_method_aes_ctr_192*</span><span class="sxs-lookup"><span data-stu-id="c23c4-156">*crypto_method_aes_ctr_192*</span></span>
  - <span data-ttu-id="c23c4-157">*crypto_method_aes_ctr_256*</span><span class="sxs-lookup"><span data-stu-id="c23c4-157">*crypto_method_aes_ctr_256*</span></span>
  - <span data-ttu-id="c23c4-158">*crypto_method_aes_xcbc_128*</span><span class="sxs-lookup"><span data-stu-id="c23c4-158">*crypto_method_aes_xcbc_128*</span></span>
  - <span data-ttu-id="c23c4-159">*crypto_method_aes_ccm_8_128*</span><span class="sxs-lookup"><span data-stu-id="c23c4-159">*crypto_method_aes_ccm_8_128*</span></span>
- <span data-ttu-id="c23c4-160">**nyckel** Pekar på en buffert som innehåller AES-nyckeln</span><span class="sxs-lookup"><span data-stu-id="c23c4-160">**key** Points to a buffer containing the AES key</span></span>
- <span data-ttu-id="c23c4-161">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-161">**key_size_in_bits** Size of the key, in bits.</span></span> <span data-ttu-id="c23c4-162">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-162">Valid values are:</span></span>
  - <span data-ttu-id="c23c4-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span><span class="sxs-lookup"><span data-stu-id="c23c4-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span></span>
  - <span data-ttu-id="c23c4-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span><span class="sxs-lookup"><span data-stu-id="c23c4-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span></span>
  - <span data-ttu-id="c23c4-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span><span class="sxs-lookup"><span data-stu-id="c23c4-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span></span>
  - <span data-ttu-id="c23c4-166">**Alla andra värden är ogiltiga.**</span><span class="sxs-lookup"><span data-stu-id="c23c4-166">**All other values are invalid.**</span></span>
- <span data-ttu-id="c23c4-167">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-167">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-168">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-168">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-169">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-169">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-170">**crypto_metadata** Pekar på ett giltigt minnes utrymme för AES-kontroll-blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-170">**crypto_metadata** Pointer to a valid memory space for the AES control block.</span></span> <span data-ttu-id="c23c4-171">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-171">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-172">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-172">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-173">För AES måste metadatans storlek vara *sizeof (NX_AES)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-173">For AES, the metadata size must be *sizeof(NX_AES)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-174">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-174">Return Values</span></span>

- <span data-ttu-id="c23c4-175">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera AES-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-175">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the AES control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-177">**NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-177">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-178">Nyckel storleken för **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) är inte giltig för AES.</span><span class="sxs-lookup"><span data-stu-id="c23c4-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for AES.</span></span>

## <a name="_nx_crypto_method_aes_operation"></a><span data-ttu-id="c23c4-179">_nx_crypto_method_aes_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-179">_nx_crypto_method_aes_operation</span></span>

<span data-ttu-id="c23c4-180">Utföra en AES-åtgärd (kryptering eller dekryptering).</span><span class="sxs-lookup"><span data-stu-id="c23c4-180">Perform an AES operation (encryption or decryption).</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-181">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-181">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="c23c4-182">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-182">Description</span></span>

<span data-ttu-id="c23c4-183">Den här funktionen utför AES-kryptering eller dekrypteringsåtgärder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-183">This function performs AES encryption or decryption operation.</span></span> <span data-ttu-id="c23c4-184">AES-kontroll blocket måste ha initierats med _ *nx_crypto_method_aes_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-184">The AES control block must have been initialized with _ *nx_crypto_method_aes_init()*.</span></span> <span data-ttu-id="c23c4-185">AES-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-185">The AES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-186">Den angivna buffertstorleken måste vara en multipel av 16 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-186">The input buffer size must be a multiple of 16 bytes.</span></span> <span data-ttu-id="c23c4-187">Storleken på dekrypterade data är samma storlek som storleken på indata.</span><span class="sxs-lookup"><span data-stu-id="c23c4-187">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="c23c4-188">Om krypterade data har fyllts ut för att uppnå en jämnt multipel av AES-blocket, kommer utfyllnaden att inkluderas i utdatabufferten och måste hanteras av programmet.</span><span class="sxs-lookup"><span data-stu-id="c23c4-188">If the encrypted data was padded to achieve an even multiple of the AES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="c23c4-189">Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckel materialet i AES-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-189">This operation does not keep state information, and does not alter the key material in the AES control block.</span></span>

<span data-ttu-id="c23c4-190">När op är NX_CRYPTO_SET_ADDITIONAL_DATA och algoritm är AES-CCM8 är indata punkter till ytterligare data och input_length_in_byte längden på ytterligare data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-190">When the op is NX_CRYPTO_SET_ADDITIONAL_DATA and algoritm is AES-CCM8, the input points to additional data and input_length_in_byte is the length of additional data.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-191">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-191">Parameters</span></span>

- <span data-ttu-id="c23c4-192">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-192">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-193">Giltiga kundgrupper är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-193">Valid opertions are:</span></span>
  - <span data-ttu-id="c23c4-194">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="c23c4-194">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="c23c4-195">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="c23c4-195">*NX_CRYPTO_DECRYPT*</span></span>
  - <span data-ttu-id="c23c4-196">*NX_CRYPTO_AUTHENTICATE (endast AES-XCBC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC only)*</span></span>
  - <span data-ttu-id="c23c4-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (endast AES-CCM8)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 only)*</span></span>
- <span data-ttu-id="c23c4-198">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-198">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-199">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-199">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-200">**metod** Pekare till giltig AES-kryptografi metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-200">**method** Pointer to the valid AES crypto method.</span></span> <span data-ttu-id="c23c4-201">Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_aes_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-201">The crypto method used here must be the same used in the *nx_crypto_method_aes_init().*</span></span>
- <span data-ttu-id="c23c4-202">**input_data** Pekar på en buffert som innehåller krypterade text data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-202">**input_data** Points to a buffer containing encrypted text data.</span></span> <span data-ttu-id="c23c4-203">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-203">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-204">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-204">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="c23c4-205">Storleken på indata måste vara en multipel av 16 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-205">The input data size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="c23c4-206">**iv_ptr** Pekar mot den inledande vektorn.</span><span class="sxs-lookup"><span data-stu-id="c23c4-206">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="c23c4-207">Det finns inga begränsningar för IV-bufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-207">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="c23c4-208">**iv_size** Storlek på det inledande vektor blocket, i byte det här fältet måste vara 16.</span><span class="sxs-lookup"><span data-stu-id="c23c4-208">**iv_size** Size of the Initial Vector block, in bytes This field must be 16.</span></span>
- <span data-ttu-id="c23c4-209">**output_buffer** Pekar på minnes området för AES för att lagra klartext-data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-209">**output_buffer** Pointer to the memory area for AES to store the clear text data.</span></span> <span data-ttu-id="c23c4-210">Programmet måste allokera utrymme för utdatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-210">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="c23c4-211">Utdatabufferten kan överlappa med indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-211">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="c23c4-212">Utdatabufferten kan överlappa med indatabufferten om de delar samma start adress.</span><span class="sxs-lookup"><span data-stu-id="c23c4-212">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="c23c4-213">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-213">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c23c4-214">Storleken på utdatabufferten måste vara minst samma som storleken på indatabufferten och utdatabufferten måste vara en multipel av 16 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-214">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="c23c4-215">**crypto_metadata** Pekar på det AES-kontroll block som används i *_nx_crypto_method_aes_init () \* . \**</span><span class="sxs-lookup"><span data-stu-id="c23c4-215">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>
- <span data-ttu-id="c23c4-216">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-216">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-217">För AES måste metadatans storlek *sizeof (NX_AES)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-217">For AES, the metadata size must *sizeof(NX_AES)*</span></span>
- <span data-ttu-id="c23c4-218">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-218">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-219">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-219">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-220">**nx_crypto_hw_process_callback** – det här fältet används inte i program implementeringen för netx-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-220">**nx_crypto_hw_process_callback** - This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-221">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-221">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-222">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-222">Return Values</span></span>

- <span data-ttu-id="c23c4-223">**NX_CRYPTO_SUCCESS** (0x00) körde AES-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-223">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the AES operation.</span></span>
- <span data-ttu-id="c23c4-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-225">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-225">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-226">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig AES-algoritm har angetts \* \*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid AES algorithm being specified\*\*.</span></span>

## <a name="_nx_crypto_method_aes_cleanup"></a><span data-ttu-id="c23c4-227">_nx_crypto_method_aes_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-227">_nx_crypto_method_aes_cleanup</span></span>

<span data-ttu-id="c23c4-228">Rensa AES-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-228">Clean up the AES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-229">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-229">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-230">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-230">Description</span></span>

<span data-ttu-id="c23c4-231">Programmet anropar den här funktionen för att rensa AES-kontroll blocket när den har bedömt att den här AES-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-231">Application calls this function to clean up the AES control block after it determines this AES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-232">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-232">Parameters</span></span>

- <span data-ttu-id="c23c4-233">**crypto_metadata** Pekar på det AES-kontroll block som används i *_nx_crypto_method_aes_init () \* . \**</span><span class="sxs-lookup"><span data-stu-id="c23c4-233">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-234">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-234">Return Values</span></span>

- <span data-ttu-id="c23c4-235">**NX_CRYPTO_SUCCESS** (0X00) har rensat AES-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-235">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the AES session.</span></span>
- <span data-ttu-id="c23c4-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_3des_init"></a><span data-ttu-id="c23c4-237">_nx_crypto_method_3des_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-237">_nx_crypto_method_3des_init</span></span>

<span data-ttu-id="c23c4-238">Initiera 3DES-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-238">Initialize the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-239">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-239">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-240">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-240">Description</span></span>

<span data-ttu-id="c23c4-241">Den här funktionen initierar kontroll blocket Triple DES (3DES) med de tre nyckel strängarna.</span><span class="sxs-lookup"><span data-stu-id="c23c4-241">This function initializes the Triple DES (3DES) control block with the given three key strings.</span></span> <span data-ttu-id="c23c4-242">Nyckel strängarna måste vara 8 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-242">The key strings must be 8 bytes each.</span></span> <span data-ttu-id="c23c4-243">De tre DES-nycklarna måste sammanfogas i sammanhängande minne med 24 byte-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-243">The three DES keys must be concatenated into contiguous memory of 24-byte buffer.</span></span> <span data-ttu-id="c23c4-244">För FIPS-kompatibla build-versioner måste de tre nycklarna vara olika från var och en av funktionerna, annars returneras NX_CRYPTO_INVALID_KEY fel.</span><span class="sxs-lookup"><span data-stu-id="c23c4-244">For FIPS-compliant build, the three keys must be different from each or the function will return the NX_CRYPTO_INVALID_KEY error.</span></span> <span data-ttu-id="c23c4-245">När 3DES-kontroll blocket initieras använder efterföljande 3DES-åtgärder samma nycklar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-245">Once the 3DES control block is initialized, subsequent 3DES operations will use the same keys.</span></span>

<span data-ttu-id="c23c4-246">Ett program kan skapa flera 3DES-kontroll block som representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-246">An application may create multiple 3DES control blocks, each representing a session.</span></span> <span data-ttu-id="c23c4-247">En nyckel tilldelas ett kontroll block och efterföljande krypterings-eller dekrypterings åtgärder kan referera till samma kontroll block utan att behöva initieras på nytt.</span><span class="sxs-lookup"><span data-stu-id="c23c4-247">A key is assigned to a control block and subsequent encryption or decryption operations can reference the same control block without needing to re-initialize.</span></span> <span data-ttu-id="c23c4-248">Om nyckeln för en session ändras måste programmet initiera kontroll blocket igen med den uppdaterade nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-248">If the key for a session is changed, the application will need to re-initialize the control block with the updated key.</span></span>

<span data-ttu-id="c23c4-249">Anrop _ *nx_crypto_method_3des_init ()* uppdaterar automatiskt en tidigare konfigurerad nyckel till de nya nycklarna.</span><span class="sxs-lookup"><span data-stu-id="c23c4-249">Calling _ *nx_crypto_method_3des_init()* automatically updates a previously configured key to the new keys.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-250">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-250">Parameters</span></span>

- <span data-ttu-id="c23c4-251">**metod** Pekar på ett giltigt kontroll block för 3DES-kryptografisk metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-251">**method** Pointer to a valid 3DES crypto method control block.</span></span> <span data-ttu-id="c23c4-252">Följande fördefinierade metod för 3DES-kryptering är tillgänglig: ***crypto_method_3des***</span><span class="sxs-lookup"><span data-stu-id="c23c4-252">The following pre-defined 3DES crypto method is available: ***crypto_method_3des***</span></span>
- <span data-ttu-id="c23c4-253">**nyckel** Pekar på en buffert som innehåller den tre (3) DES-nyckeln</span><span class="sxs-lookup"><span data-stu-id="c23c4-253">**key** Points to a buffer containing the three (3) DES key</span></span>
- <span data-ttu-id="c23c4-254">**key_size_in_bits** Måste vara 192 (3 nycklar, varje 64 bitar).</span><span class="sxs-lookup"><span data-stu-id="c23c4-254">**key_size_in_bits** Must be 192 (3 keys, each 64 bits).</span></span>
- <span data-ttu-id="c23c4-255">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-255">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-256">Referensen identifierar det 3DES-kontroll block som initieras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-256">The handle identifies the 3DES control block being initialized.</span></span> <span data-ttu-id="c23c4-257">Efterföljande 3DES-åtgärder (kryptering, dekryptering och rensning) använder den här referensen för att få åtkomst till 3DES-kontroll blocket</span><span class="sxs-lookup"><span data-stu-id="c23c4-257">Subsequent 3DES operations (encryption, decryption, and cleanup) use this handle to access the 3DES control block</span></span>
- <span data-ttu-id="c23c4-258">**crypto_metadata** Pekar på ett giltigt minnes utrymme för 3DES-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-258">**crypto_metadata** Pointer to a valid memory space for the 3DES control block.</span></span> <span data-ttu-id="c23c4-259">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-259">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-260">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-260">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-261">För 3DES måste storleken på metadata vara *sizeof (NX_3DES)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-261">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>

### <a name="return-value"></a><span data-ttu-id="c23c4-262">Returvärde</span><span class="sxs-lookup"><span data-stu-id="c23c4-262">Return Value</span></span>

- <span data-ttu-id="c23c4-263">**NX_CRYPTO_SUCCESS** (0X00) slutförde initieringen av 3DES-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-263">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-265">**NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-265">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-266">Nyckel storleken för **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) är inte giltig för 3DES.</span><span class="sxs-lookup"><span data-stu-id="c23c4-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for 3DES.</span></span>

## <a name="_nx_crypto_method_3des_operation"></a><span data-ttu-id="c23c4-267">_nx_crypto_method_3des_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-267">_nx_crypto_method_3des_operation</span></span>

<span data-ttu-id="c23c4-268">Kryptera eller dekryptera med 3DES.</span><span class="sxs-lookup"><span data-stu-id="c23c4-268">Encrypt or Decrypt with 3DES.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-269">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-269">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-270">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-270">Description</span></span>

<span data-ttu-id="c23c4-271">Den här funktionen utför 3DES-kryptering eller dekrypteringsåtgärder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-271">This function performs 3DES encryption or decryption operation.</span></span> <span data-ttu-id="c23c4-272">3DES-kontroll blocket måste ha initierats med _ *nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-272">The 3DES control block must have been initialized with _ *nx_crypto_method_3des_init()*.</span></span> <span data-ttu-id="c23c4-273">3DES-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-273">The 3DES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-274">Den angivna buffertstorleken måste vara en multipel av 8 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-274">The input buffer size must be a multiple of 8 bytes.</span></span> <span data-ttu-id="c23c4-275">Storleken på dekrypterade data är samma storlek som storleken på indata.</span><span class="sxs-lookup"><span data-stu-id="c23c4-275">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="c23c4-276">Om krypterade data har fyllts ut för att uppnå en jämn multipel av 3DES-blocket, inkluderas utfyllnaden i utdatabufferten och måste hanteras av programmet.</span><span class="sxs-lookup"><span data-stu-id="c23c4-276">If the encrypted data was padded to achieve an even multiple of the 3DES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="c23c4-277">Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckel materialet i 3DES-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-277">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-278">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-278">Parameters</span></span>

- <span data-ttu-id="c23c4-279">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-279">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-280">Giltiga åtgärder är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-280">Valid operations are:</span></span>
  - <span data-ttu-id="c23c4-281">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="c23c4-281">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="c23c4-282">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="c23c4-282">*NX_CRYPTO_DECRYPT*</span></span>
- <span data-ttu-id="c23c4-283">**Hantera** Referensen initierades av *_nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-283">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="c23c4-284">**metod** Pekar på giltig 3DES-kryptografi metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-284">**method** Pointer to the valid 3DES crypto method.</span></span> <span data-ttu-id="c23c4-285">Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_3des_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-285">The crypto method used here must be the same used in the *nx_crypto_method_3des_init().*</span></span>
- <span data-ttu-id="c23c4-286">**input_data** Pekar på en buffert som innehåller krypterade text data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-286">**input_data** Points to a buffer containing encrypted text data.</span></span>
<span data-ttu-id="c23c4-287">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-287">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-288">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-288">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="c23c4-289">Storleken på indata måste vara en multipel av 8 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-289">The input data size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="c23c4-290">**iv_ptr** Pekar mot den inledande vektorn.</span><span class="sxs-lookup"><span data-stu-id="c23c4-290">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="c23c4-291">Det finns inga begränsningar för IV-bufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-291">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="c23c4-292">**iv_size** Storleken på det inledande vektor blocket, i byte det här fältet måste vara 8.</span><span class="sxs-lookup"><span data-stu-id="c23c4-292">**iv_size** Size of the Initial Vector block, in bytes This field must be 8.</span></span>
- <span data-ttu-id="c23c4-293">**output_buffer** Pekar på minnes området för 3DES för att lagra rensade text data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-293">**output_buffer** Pointer to the memory area for 3DES to store the clear text data.</span></span> <span data-ttu-id="c23c4-294">Programmet måste allokera utrymme för utdatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-294">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="c23c4-295">Utdatabufferten kan överlappa med indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-295">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="c23c4-296">Utdatabufferten kan överlappa med indatabufferten om de delar samma start adress.</span><span class="sxs-lookup"><span data-stu-id="c23c4-296">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="c23c4-297">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-297">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c23c4-298">Storleken på utdatabufferten måste vara minst samma som storleken på indatabufferten och utdatabufferten måste vara en multipel av 8 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-298">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="c23c4-299">**crypto_metadata** Pekare till det 3DES-kontroll block som används i *_nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-299">**crypto_metadata** Pointer to the 3DES control block used in *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="c23c4-300">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-300">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-301">För 3DES måste storleken på metadata vara *sizeof (NX_3DES)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-301">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>
- <span data-ttu-id="c23c4-302">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-302">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-303">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-303">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-304">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-304">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-305">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-305">Any values passed in are silently ignored.</span></span>

### <a name="description"></a><span data-ttu-id="c23c4-306">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-306">Description</span></span>

<span data-ttu-id="c23c4-307">Den här funktionen utför 3DES-kryptering.</span><span class="sxs-lookup"><span data-stu-id="c23c4-307">This function performs 3DES encryption.</span></span> <span data-ttu-id="c23c4-308">3DES-kontroll blocket måste ha initierats med _ *nx_crypto_moethod_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-308">The 3DES control block must have been initialized with _ *nx_crypto_moethod_3des_init()*.</span></span> <span data-ttu-id="c23c4-309">Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckel materialet i 3DES-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-309">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span> <span data-ttu-id="c23c4-310">Observera att utfyllnad inte läggs till av den här funktionen, så att anroparen måste hantera utfyllnad innan du anropar krypterings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-310">Note that padding is not added by this function so the caller will need to handle padding before invoking the encryption operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-311">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-311">Return Values</span></span>

- <span data-ttu-id="c23c4-312">**NX_CRYPTO_SUCCESS** (0X00) slutförde initieringen av 3DES-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-312">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-314">**NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-314">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_3des_cleanup"></a><span data-ttu-id="c23c4-315">_nx_crypto_method_3des_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-315">_nx_crypto_method_3des_cleanup</span></span>

<span data-ttu-id="c23c4-316">Rensa 3DES-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-316">Clean up the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-317">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-317">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-318">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-318">Description</span></span>

<span data-ttu-id="c23c4-319">Programmet anropar den här funktionen för att rensa 3DES-kontroll blocket efter att den här 3DES-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-319">Application calls this function to clean up the 3DES control block after it determines this 3DES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-320">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-320">Parameters</span></span>

- <span data-ttu-id="c23c4-321">**Hantera** Referensen initierades av *_nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-321">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-322">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-322">Return Values</span></span>

- <span data-ttu-id="c23c4-323">**NX_CRYPTO_SUCCESS** (0x00) rensade 3DES-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-323">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the 3DES session.</span></span>
- <span data-ttu-id="c23c4-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_drbg_init"></a><span data-ttu-id="c23c4-325">_nx_crypto_method_drbg_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-325">_nx_crypto_method_drbg_init</span></span>

<span data-ttu-id="c23c4-326">Initierar kontroll block för DRBG-kryptografi</span><span class="sxs-lookup"><span data-stu-id="c23c4-326">Initializes the DRBG crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-327">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-327">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-328">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-328">Description</span></span>

<span data-ttu-id="c23c4-329">Den här funktionen initierar kontroll blocket DRBG med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-329">This function initializes the DRBG control block with the given key string.</span></span> <span data-ttu-id="c23c4-330">När DRBG-kontroll blocket initieras, ska efterföljande DRBG-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-330">Once the DRBG control block is initialized, subsequent DRBG operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-331">Programmet kan skapa flera DRBG-kontroll block, som var och en representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-331">Application may create multiple DRBG control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-332">Initieringen av DRBG Control Block startar en ny session med hash-beräkning.</span><span class="sxs-lookup"><span data-stu-id="c23c4-332">Initializing the DRBG control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-333">Ominitieringen av kontroll blocket DRBG överger den aktuella sessionen och använder stjärnorna som en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-333">Re-initializing the DRBG control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-334">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-334">Parameters</span></span>

- <span data-ttu-id="c23c4-335">**metod** Pekar på ett giltigt kontroll block för DRBG-kryptografiska metoder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-335">**method** Pointer to a valid DRBG crypto method control block.</span></span> <span data-ttu-id="c23c4-336">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-336">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-337">*crypto_method_drbg*</span><span class="sxs-lookup"><span data-stu-id="c23c4-337">*crypto_method_drbg*</span></span>
- <span data-ttu-id="c23c4-338">**nyckel** Det här fältet används inte för DRBG.</span><span class="sxs-lookup"><span data-stu-id="c23c4-338">**key** This field is not used for DRBG.</span></span>
- <span data-ttu-id="c23c4-339">**key_size_in_bits** Det här fältet används inte för DRBG.</span><span class="sxs-lookup"><span data-stu-id="c23c4-339">**key_size_in_bits** This field is not used for DRBG.</span></span>
- <span data-ttu-id="c23c4-340">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-340">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-341">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-341">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-342">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-342">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-343">**crypto_metadata** Pekar på ett giltigt minnes utrymme för DRBG-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-343">**crypto_metadata** Pointer to a valid memory space for the DRBG control block.</span></span> <span data-ttu-id="c23c4-344">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-344">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-345">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-345">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-346">För DRBG måste storleken på metadata vara *sizeof (NX_CRYPTO_DRBG)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-346">For DRBG, the metadata size must be *sizeof(NX_CRYPTO_DRBG)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-347">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-347">Return Values</span></span>

- <span data-ttu-id="c23c4-348">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera DRBG-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-348">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the DRBG control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-350">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-350">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_drbg_operation"></a><span data-ttu-id="c23c4-351">_nx_crypto_method_drbg_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-351">_nx_crypto_method_drbg_operation</span></span>

<span data-ttu-id="c23c4-352">Utför DRBG-åtgärd</span><span class="sxs-lookup"><span data-stu-id="c23c4-352">Perform DRBG operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-353">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-353">Prototype</span></span>

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-354">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-354">Description</span></span>

<span data-ttu-id="c23c4-355">Den här funktionen utför DRBG-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-355">This function performs DRBG operation.</span></span> <span data-ttu-id="c23c4-356">Kontroll blocket DRBG måste ha initierats med _ *nx_crypto_method_drbg_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-356">The DRBG control block must have been initialized with _ *nx_crypto_method_drbg_init()*.</span></span> <span data-ttu-id="c23c4-357">DRBG-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-357">The DRBG algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span> <span data-ttu-id="c23c4-358">Som standard används AES-128 för DRBG.</span><span class="sxs-lookup"><span data-stu-id="c23c4-358">By default AES-128 is used for DRBG.</span></span>

<span data-ttu-id="c23c4-359">När åtgärden NX_CRYPTO_DRBG_OPTIONS_SETs pekar ingångarna till NX_CRYPTO_DRBG_OPTIONS-strukturen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-359">When the operation is NX_CRYPTO_DRBG_OPTIONS_SET, the input points to NX_CRYPTO_DRBG_OPTIONS structure.</span></span> <span data-ttu-id="c23c4-360">När åtgärden är NX_CRYPTO_DRBG_INSTANTIATE, kommer nyckeln till nonce, ingångs punkter till anpassnings strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-360">When the operation is NX_CRYPTO_DRBG_INSTANTIATE, the key points to nonce, input points to personalization string.</span></span> <span data-ttu-id="c23c4-361">När åtgärden är NX_CRYPTO_DRBG_RESEED eller NX_CRYPTO_DRBG_GENERATE, så pekar ingångarna till ytterligare indatatyper.</span><span class="sxs-lookup"><span data-stu-id="c23c4-361">When the operation is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, the input points to additional input.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-362">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-362">Parameters</span></span>

- <span data-ttu-id="c23c4-363">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-363">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-364">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-364">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span><span class="sxs-lookup"><span data-stu-id="c23c4-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span></span>
  - <span data-ttu-id="c23c4-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span></span>
  - <span data-ttu-id="c23c4-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span></span>
- <span data-ttu-id="c23c4-368">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-368">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-369">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-369">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-370">**metod** Pekare till den giltiga DRBG-kryptografi metoden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-370">**method** Pointer to the valid DRBG crypto method.</span></span> <span data-ttu-id="c23c4-371">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_drbg_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-371">The crypto method used here must be the same used in the _ *nx_crypto_method_drbg_init().*</span></span>
- <span data-ttu-id="c23c4-372">**nyckel** Pekar till nonce för initierings åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-372">**key** Pointer to the the nonce for the instantiate operation.</span></span> <span data-ttu-id="c23c4-373">Det här fältet används inte för andra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-373">This field is not used for other operations.</span></span>
- <span data-ttu-id="c23c4-374">**key_size_in_bits** Storleken på nonce i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-374">**key_size_in_bits** Size of the nonce, in bits.</span></span> <span data-ttu-id="c23c4-375">Det här fältet används inte för andra åtgärder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-375">This field is not used for other operations.</span></span>
- <span data-ttu-id="c23c4-376">**mata in** När op är NX_CRYPTO_DRBG_OPTIONS_SET pekar det här fältet på DRBG-alternativ.</span><span class="sxs-lookup"><span data-stu-id="c23c4-376">**input** When op is NX_CRYPTO_DRBG_OPTIONS_SET, this field points to DRBG options.</span></span> <span data-ttu-id="c23c4-377">När op är NX_CRYPTO_DRBG_INSTANTIATE pekar detta fält på anpassnings sträng.</span><span class="sxs-lookup"><span data-stu-id="c23c4-377">When op is NX_CRYPTO_DRBG_INSTANTIATE, this field points to personalization string.</span></span> <span data-ttu-id="c23c4-378">När op är NX_CRYPTO_DRBG_RESEED eller NX_CRYPTO_DRBG_GENERATE, pekar det här fältet på ytterligare indata.</span><span class="sxs-lookup"><span data-stu-id="c23c4-378">When op is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, this field points to additional input data.</span></span>
- <span data-ttu-id="c23c4-379">**input_length_in_byte** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-379">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-380">**iv_ptr** Det här fältet används inte för DRBG.</span><span class="sxs-lookup"><span data-stu-id="c23c4-380">**iv_ptr** This field is not used for DRBG.</span></span>
- <span data-ttu-id="c23c4-381">**utdata** När op är NX_CRYPTO_DRBG_GENERATE, pekar det här fältet på minnes området för den genererade DRBG.</span><span class="sxs-lookup"><span data-stu-id="c23c4-381">**output** When op is NX_CRYPTO_DRBG_GENERATE, this field points to the memory area for the generated DRBG.</span></span> <span data-ttu-id="c23c4-382">Annars används inte det här fältet.</span><span class="sxs-lookup"><span data-stu-id="c23c4-382">Otherwise, this field is not used.</span></span>
- <span data-ttu-id="c23c4-383">**output_length_in_byte** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-383">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c23c4-384">**crypto_metadata** Pekare till DRBG-kontroll blocket som används i *_nx_crypto_method_drbg_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-384">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>
- <span data-ttu-id="c23c4-385">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-385">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-386">För DRBG måste metadata *-storleken sizeof (NX_CRYPTO_DRBG)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-386">For DRBG, the metadata size must *sizeof(NX_CRYPTO_DRBG)*</span></span>
- <span data-ttu-id="c23c4-387">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-387">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-388">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-388">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-389">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-389">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-390">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-390">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-391">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-391">Return Values</span></span>

- <span data-ttu-id="c23c4-392">**NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden DRBG.</span><span class="sxs-lookup"><span data-stu-id="c23c4-392">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the DRBG operation.</span></span>
- <span data-ttu-id="c23c4-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-394">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-394">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-395">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig DRBG-algoritm anges.</span><span class="sxs-lookup"><span data-stu-id="c23c4-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid DRBG algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_drbg_cleanup"></a><span data-ttu-id="c23c4-397">_nx_crypto_method_drbg_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-397">_nx_crypto_method_drbg_cleanup</span></span>

<span data-ttu-id="c23c4-398">Rensa kontroll blocket DRBG.</span><span class="sxs-lookup"><span data-stu-id="c23c4-398">Clean up the DRBG control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-399">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-399">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-400">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-400">Description</span></span>

<span data-ttu-id="c23c4-401">Programmet anropar den här funktionen för att rensa DRBG-kontroll blocket när den har bedömt att den här DRBG-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-401">Application calls this function to clean up the DRBG control block after it determines this DRBG session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-402">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-402">Parameters</span></span>

- <span data-ttu-id="c23c4-403">**crypto_metadata** Pekare till DRBG-kontroll blocket som används i *_nx_crypto_method_drbg_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-403">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-404">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-404">Return Values</span></span>

- <span data-ttu-id="c23c4-405">**NX_CRYPTO_SUCCESS** (0X00) har rensat DRBG-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-405">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the DRBG session.</span></span>
- <span data-ttu-id="c23c4-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdh_init"></a><span data-ttu-id="c23c4-407">_nx_crypto_method_ecdh_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-407">_nx_crypto_method_ecdh_init</span></span>

<span data-ttu-id="c23c4-408">Initierar kontroll block för ECDH-kryptografi</span><span class="sxs-lookup"><span data-stu-id="c23c4-408">Initializes the ECDH crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-409">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-409">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-410">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-410">Description</span></span>

<span data-ttu-id="c23c4-411">Den här funktionen initierar kontroll blocket ECDH med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-411">This function initializes the ECDH control block with the given key string.</span></span> <span data-ttu-id="c23c4-412">När ECDH-kontroll blocket initieras, ska efterföljande ECDH-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-412">Once the ECDH control block is initialized, subsequent ECDH operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-413">Programmet kan skapa flera ECDH-kontroll block, som var och en representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-413">Application may create multiple ECDH control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-414">Initieringen av ECDH Control Block startar en ny session med hash-beräkning.</span><span class="sxs-lookup"><span data-stu-id="c23c4-414">Initializing the ECDH control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-415">Ominitieringen av kontroll blocket ECDH överger den aktuella sessionen och använder stjärnorna som en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-415">Re-initializing the ECDH control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-416">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-416">Parameters</span></span>

- <span data-ttu-id="c23c4-417">**metod** Pekar på ett giltigt kontroll block för ECDH-kryptografiska metoder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-417">**method** Pointer to a valid ECDH crypto method control block.</span></span> <span data-ttu-id="c23c4-418">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-418">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-419">*crypto_method_ecdh*</span><span class="sxs-lookup"><span data-stu-id="c23c4-419">*crypto_method_ecdh*</span></span>
- <span data-ttu-id="c23c4-420">**nyckel** Det här fältet används inte för ECDH.</span><span class="sxs-lookup"><span data-stu-id="c23c4-420">**key** This field is not used for ECDH.</span></span>
- <span data-ttu-id="c23c4-421">**key_size_in_bits** Det här fältet används inte för ECDH.</span><span class="sxs-lookup"><span data-stu-id="c23c4-421">**key_size_in_bits** This field is not used for ECDH.</span></span>
- <span data-ttu-id="c23c4-422">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-422">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-423">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-423">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-424">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-424">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-425">**crypto_metadata** Pekar på ett giltigt minnes utrymme för ECDH-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-425">**crypto_metadata** Pointer to a valid memory space for the ECDH control block.</span></span> <span data-ttu-id="c23c4-426">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-426">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-427">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-427">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-428">För ECDH måste storleken på metadata vara *sizeof (NX_CRYPTO_ECDH)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-428">For ECDH, the metadata size must be *sizeof(NX_CRYPTO_ECDH)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-429">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-429">Return Values</span></span>

- <span data-ttu-id="c23c4-430">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera ECDH-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-430">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDH control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-432">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-432">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdh_operation"></a><span data-ttu-id="c23c4-433">_nx_crypto_method_ecdh_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-433">_nx_crypto_method_ecdh_operation</span></span>

<span data-ttu-id="c23c4-434">Utför ECDH-åtgärd</span><span class="sxs-lookup"><span data-stu-id="c23c4-434">Perform ECDH operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-435">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-435">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-436">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-436">Description</span></span>

<span data-ttu-id="c23c4-437">Den här funktionen utför ECDH-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-437">This function performs ECDH operation.</span></span> <span data-ttu-id="c23c4-438">Kontroll blocket ECDH måste ha initierats med _ *nx_crypto_method_ecdh_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-438">The ECDH control block must have been initialized with _ *nx_crypto_method_ecdh_init()*.</span></span> <span data-ttu-id="c23c4-439">ECDH-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-439">The ECDH algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-440">När åtgärden NX_CRYPTO_EC_CURVE_SETs, pekar ingångarna på Elliptic Curve-krypterings metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-440">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c23c4-441">När åtgärden är NX_CRYPTO_EC_KEY_PAIR_GENERATE kopieras utdata till NX_CRYPTO_EXTENDED_OUTPUT-strukturen och nyckel paret kopieras till nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-441">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="c23c4-442">När åtgärden NX_CRYPTO_DH_SETUP returneras den offentliga nyckeln till nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-442">When the operation is NX_CRYPTO_DH_SETUP, the public key is returned to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="c23c4-443">När åtgärden NX_CRYPTO_DH_KEY_PAIR_IMPORTs pekar ingångarna på offentlig nyckel och nyckel punkter till privat nyckel.</span><span class="sxs-lookup"><span data-stu-id="c23c4-443">When the operation is NX_CRYPTO_DH_KEY_PAIR_IMPORT, the input points to public key and key points to private key.</span></span> <span data-ttu-id="c23c4-444">När åtgärden NX_CRYPTO_DH_PRIVATE_KEY_EXPORT kopieras den privata nyckeln till nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-444">When the operation is NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, the private key is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="c23c4-445">När åtgärden är NX_CRYPTO_DH_CALCULATE kopieras ingångs punkterna till den offentliga fjärrnyckeln och den delade hemligheten till nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-445">When the operation is NX_CRYPTO_DH_CALCULATE, the input points to remote public key and the shared secret is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-446">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-446">Parameters</span></span>

- <span data-ttu-id="c23c4-447">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-447">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-448">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-448">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-449">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="c23c4-449">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="c23c4-450">*NX_CRYPTO_DH_SETUP*</span><span class="sxs-lookup"><span data-stu-id="c23c4-450">*NX_CRYPTO_DH_SETUP*</span></span>
  - <span data-ttu-id="c23c4-451">*NX_CRYPTO_DH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-451">*NX_CRYPTO_DH_CALCULATE*</span></span>
  - <span data-ttu-id="c23c4-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span><span class="sxs-lookup"><span data-stu-id="c23c4-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span></span>
  - <span data-ttu-id="c23c4-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span></span>
  - <span data-ttu-id="c23c4-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span><span class="sxs-lookup"><span data-stu-id="c23c4-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span></span>
- <span data-ttu-id="c23c4-455">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-455">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-456">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-456">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-457">**metod** Pekare till den giltiga ECDH-kryptografi metoden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-457">**method** Pointer to the valid ECDH crypto method.</span></span> <span data-ttu-id="c23c4-458">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_ecdh_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-458">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdh_init().*</span></span>
- <span data-ttu-id="c23c4-459">**nyckel** När op är NX_CRYPTO_DH_IMPORT_KEY_PAIR pekar detta fält på privat nyckel.</span><span class="sxs-lookup"><span data-stu-id="c23c4-459">**key** When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to private key.</span></span> <span data-ttu-id="c23c4-460">Annars används inte det här fältet för ECDH.</span><span class="sxs-lookup"><span data-stu-id="c23c4-460">Otherwise, this field is not used for ECDH.</span></span>
- <span data-ttu-id="c23c4-461">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-461">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-462">**mata in** När op är NX_CRYPTO_EC_CURVE_SET pekar detta fält på kryptografi metoden för Elliptic-kurvan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-462">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c23c4-463">När op är NX_CRYPTO_DH_SETUP används inte det här fältet.</span><span class="sxs-lookup"><span data-stu-id="c23c4-463">When op is NX_CRYPTO_DH_SETUP, this field is not used.</span></span> <span data-ttu-id="c23c4-464">När op är NX_CRYPTO_DH_CALCULATE pekar det här fältet på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-464">When op is NX_CRYPTO_DH_CALCULATE, this field points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-465">När op är NX_CRYPTO_DH_IMPORT_KEY_PAIR, pekar detta fält på offentlig nyckel.</span><span class="sxs-lookup"><span data-stu-id="c23c4-465">When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to public key.</span></span>
- <span data-ttu-id="c23c4-466">**input_length_in_byte** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-466">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-467">**iv_ptr** Det här fältet används inte för ECDH.</span><span class="sxs-lookup"><span data-stu-id="c23c4-467">**iv_ptr** This field is not used for ECDH.</span></span>
- <span data-ttu-id="c23c4-468">**utdata** När op är NX_CRYPTO_EC_CURVE_SET eller NX_CRYPTO_DH_IMPORT_KEY_PAIR används inte det här fältet.</span><span class="sxs-lookup"><span data-stu-id="c23c4-468">**output** When op is NX_CRYPTO_EC_CURVE_SET or NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field is not used.</span></span> <span data-ttu-id="c23c4-469">När op är NX_CRYPTO_DH_SETUP pekar det här fältet på minnes området för den genererade offentliga nyckeln ECDH.</span><span class="sxs-lookup"><span data-stu-id="c23c4-469">When op is NX_CRYPTO_DH_SETUP, this field points to the memory area for the generated ECDH public key.</span></span> <span data-ttu-id="c23c4-470">När op är NX_CRYPTO_DH_CALCULATE, pekar det här fältet på minnes området för den genererade ECDH delade hemligheten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-470">When op is NX_CRYPTO_DH_CALCULATE, this field points to the memory area for the generated ECDH shared secret.</span></span>
- <span data-ttu-id="c23c4-471">**output_length_in_byte** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-471">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c23c4-472">**crypto_metadata** Pekare till ECDH-kontroll blocket som används i *_nx_crypto_method_ecdh_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-472">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>
- <span data-ttu-id="c23c4-473">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-473">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-474">För ECDH måste metadata *-storleken sizeof (NX_CRYPTO_ECDH)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-474">For ECDH, the metadata size must *sizeof(NX_CRYPTO_ECDH)*</span></span>
- <span data-ttu-id="c23c4-475">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-475">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-476">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-476">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-477">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-477">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-478">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-478">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-479">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-479">Return Values</span></span>

- <span data-ttu-id="c23c4-480">**NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden ECDH.</span><span class="sxs-lookup"><span data-stu-id="c23c4-480">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDH operation.</span></span>
- <span data-ttu-id="c23c4-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-482">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-482">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-483">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig ECDH-algoritm anges.</span><span class="sxs-lookup"><span data-stu-id="c23c4-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDH algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdh_cleanup"></a><span data-ttu-id="c23c4-485">_nx_crypto_method_ecdh_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-485">_nx_crypto_method_ecdh_cleanup</span></span>

<span data-ttu-id="c23c4-486">Rensa kontroll blocket ECDH.</span><span class="sxs-lookup"><span data-stu-id="c23c4-486">Clean up the ECDH control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-487">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-487">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-488">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-488">Description</span></span>

<span data-ttu-id="c23c4-489">Programmet anropar den här funktionen för att rensa ECDH-kontroll blocket när den har bedömt att den här ECDH-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-489">Application calls this function to clean up the ECDH control block after it determines this ECDH session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-490">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-490">Parameters</span></span>

- <span data-ttu-id="c23c4-491">**crypto_metadata** Pekare till ECDH-kontroll blocket som används i *_nx_crypto_method_ecdh_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-491">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-492">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-492">Return Values</span></span>

- <span data-ttu-id="c23c4-493">**NX_CRYPTO_SUCCESS** (0X00) har rensat ECDH-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-493">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDH session.</span></span>
- <span data-ttu-id="c23c4-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdsa_init"></a><span data-ttu-id="c23c4-495">_nx_crypto_method_ecdsa_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-495">_nx_crypto_method_ecdsa_init</span></span>

<span data-ttu-id="c23c4-496">Initierar kontroll block för ECDSA-kryptografi</span><span class="sxs-lookup"><span data-stu-id="c23c4-496">Initializes the ECDSA crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-497">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-497">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-498">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-498">Description</span></span>

<span data-ttu-id="c23c4-499">Den här funktionen initierar kontroll blocket ECDSA med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-499">This function initializes the ECDSA control block with the given key string.</span></span> <span data-ttu-id="c23c4-500">När ECDSA-kontroll blocket initieras, ska efterföljande ECDSA-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-500">Once the ECDSA control block is initialized, subsequent ECDSA operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-501">Programmet kan skapa flera ECDSA-kontroll block, som var och en representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-501">Application may create multiple ECDSA control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-502">Initieringen av ECDSA Control Block startar en ny session med hash-beräkning.</span><span class="sxs-lookup"><span data-stu-id="c23c4-502">Initializing the ECDSA control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-503">Ominitieringen av kontroll blocket ECDSA överger den aktuella sessionen och använder stjärnorna som en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-503">Re-initializing the ECDSA control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-504">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-504">Parameters</span></span>

- <span data-ttu-id="c23c4-505">**metod** Pekar på ett giltigt kontroll block för ECDSA-kryptografiska metoder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-505">**method** Pointer to a valid ECDSA crypto method control block.</span></span> <span data-ttu-id="c23c4-506">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-506">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-507">*crypto_method_ecdsa*</span><span class="sxs-lookup"><span data-stu-id="c23c4-507">*crypto_method_ecdsa*</span></span>
- <span data-ttu-id="c23c4-508">**nyckel** Det här fältet används inte för ECDSA.</span><span class="sxs-lookup"><span data-stu-id="c23c4-508">**key** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="c23c4-509">**key_size_in_bits** Det här fältet används inte för ECDSA.</span><span class="sxs-lookup"><span data-stu-id="c23c4-509">**key_size_in_bits** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="c23c4-510">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-510">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-511">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-511">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-512">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-512">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-513">**crypto_metadata** Pekar på ett giltigt minnes utrymme för ECDSA-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-513">**crypto_metadata** Pointer to a valid memory space for the ECDSA control block.</span></span> <span data-ttu-id="c23c4-514">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-514">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-515">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-515">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-516">För ECDSA måste storleken på metadata vara *sizeof (NX_CRYPTO_ECDSA)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-516">For ECDSA, the metadata size must be *sizeof(NX_CRYPTO_ECDSA)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-517">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-517">Return Values</span></span>

- <span data-ttu-id="c23c4-518">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera ECDSA-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-518">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDSA control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-520">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-520">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdsa_operation"></a><span data-ttu-id="c23c4-521">_nx_crypto_method_ecdsa_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-521">_nx_crypto_method_ecdsa_operation</span></span>

<span data-ttu-id="c23c4-522">Utför ECDSA-åtgärd</span><span class="sxs-lookup"><span data-stu-id="c23c4-522">Perform ECDSA operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-523">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-523">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-524">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-524">Description</span></span>

<span data-ttu-id="c23c4-525">Den här funktionen utför ECDSA-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-525">This function performs ECDSA operation.</span></span> <span data-ttu-id="c23c4-526">Kontroll blocket ECDSA måste ha initierats med _ *nx_crypto_method_ecdsa_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-526">The ECDSA control block must have been initialized with _ *nx_crypto_method_ecdsa_init()*.</span></span> <span data-ttu-id="c23c4-527">ECDSA-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-527">The ECDSA algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-528">När åtgärden NX_CRYPTO_EC_CURVE_SETs, pekar ingångarna på Elliptic Curve-krypterings metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-528">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c23c4-529">När åtgärden är NX_CRYPTO_EC_KEY_PAIR_GENERATE kopieras utdata till NX_CRYPTO_EXTENDED_OUTPUT-strukturen och nyckel paret kopieras till nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="c23c4-529">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-530">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-530">Parameters</span></span>

- <span data-ttu-id="c23c4-531">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-531">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-532">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-532">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-533">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="c23c4-533">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="c23c4-534">*NX_CRYPTO_AUTHENTICATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-534">*NX_CRYPTO_AUTHENTICATE*</span></span>
  - <span data-ttu-id="c23c4-535">*NX_CRYPTO_VERIFY*</span><span class="sxs-lookup"><span data-stu-id="c23c4-535">*NX_CRYPTO_VERIFY*</span></span>
- <span data-ttu-id="c23c4-536">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-536">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-537">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-537">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-538">**metod** Pekare till den giltiga ECDSA-kryptografi metoden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-538">**method** Pointer to the valid ECDSA crypto method.</span></span> <span data-ttu-id="c23c4-539">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_ecdsa_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-539">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdsa_init().*</span></span>
- <span data-ttu-id="c23c4-540">**nyckel** Pekar på nyckeln när op är NX_CRYPTO_VERIFY.</span><span class="sxs-lookup"><span data-stu-id="c23c4-540">**key** Points to the key when op is NX_CRYPTO_VERIFY.</span></span> <span data-ttu-id="c23c4-541">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-541">There are not restrictions on key buffer.</span></span> <span data-ttu-id="c23c4-542">Det här fältet används inte för andra värden på op.</span><span class="sxs-lookup"><span data-stu-id="c23c4-542">This field is not used for other values of op.</span></span>
- <span data-ttu-id="c23c4-543">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-543">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-544">**mata in** När op är NX_CRYPTO_EC_CURVE_SET pekar detta fält på kryptografi metoden för Elliptic-kurvan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-544">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c23c4-545">Annars pekar det här fältet på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-545">Otherwise, this field points to a buffer containing input text data.</span></span>
- <span data-ttu-id="c23c4-546">**input_length_in_byte** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-546">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-547">**iv_ptr** Det här fältet används inte för ECDSA.</span><span class="sxs-lookup"><span data-stu-id="c23c4-547">**iv_ptr** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="c23c4-548">**utdata** När op är NX_CRYPTO_EC_CURVE_SET används inte det här fältet.</span><span class="sxs-lookup"><span data-stu-id="c23c4-548">**output** When op is NX_CRYPTO_EC_CURVE_SET, this field is not used.</span></span> <span data-ttu-id="c23c4-549">När op är NX_CRYPTO_AUTHENTICATE, pekar det här fältet på minnes området för den genererade ECDSA-signaturen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-549">When op is NX_CRYPTO_AUTHENTICATE, this field points to the memory area for the generated ECDSA signature.</span></span> <span data-ttu-id="c23c4-550">När op är NX_CRYPTO_VERIFY, pekar det här fältet på minnes området för den verifierade ECDSA-signaturen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-550">When op is NX_CRYPTO_VERIFY, this field points to the memory area for the verified ECDSA signature.</span></span>
- <span data-ttu-id="c23c4-551">**output_length_in_byte** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-551">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c23c4-552">**crypto_metadata** Pekare till ECDSA-kontroll blocket som används i *_nx_crypto_method_ecdsa_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-552">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>
- <span data-ttu-id="c23c4-553">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-553">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-554">För ECDSA måste metadata *-storleken sizeof (NX_CRYPTO_ECDSA)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-554">For ECDSA, the metadata size must *sizeof(NX_CRYPTO_ECDSA)*</span></span>
- <span data-ttu-id="c23c4-555">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-555">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-556">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-556">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-557">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-557">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-558">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-558">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-559">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-559">Return Values</span></span>

- <span data-ttu-id="c23c4-560">**NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden ECDSA.</span><span class="sxs-lookup"><span data-stu-id="c23c4-560">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDSA operation.</span></span>
- <span data-ttu-id="c23c4-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-562">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-562">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-563">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig ECDSA-algoritm anges.</span><span class="sxs-lookup"><span data-stu-id="c23c4-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDSA algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdsa_cleanup"></a><span data-ttu-id="c23c4-565">_nx_crypto_method_ecdsa_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-565">_nx_crypto_method_ecdsa_cleanup</span></span>

<span data-ttu-id="c23c4-566">Rensa kontroll blocket ECDSA.</span><span class="sxs-lookup"><span data-stu-id="c23c4-566">Clean up the ECDSA control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-567">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-567">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-568">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-568">Description</span></span>

<span data-ttu-id="c23c4-569">Programmet anropar den här funktionen för att rensa ECDSA-kontroll blocket när den har bedömt att den här ECDSA-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-569">Application calls this function to clean up the ECDSA control block after it determines this ECDSA session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-570">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-570">Parameters</span></span>

- <span data-ttu-id="c23c4-571">**crypto_metadata** Pekare till ECDSA-kontroll blocket som används i *_nx_crypto_method_ecdsa_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-571">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-572">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-572">Return Values</span></span>

- <span data-ttu-id="c23c4-573">**NX_CRYPTO_SUCCESS** (0X00) har rensat ECDSA-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-573">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDSA session.</span></span>
- <span data-ttu-id="c23c4-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_md5_init"></a><span data-ttu-id="c23c4-575">_nx_crypto_method_hmac_md5_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-575">_nx_crypto_method_hmac_md5_init</span></span>

<span data-ttu-id="c23c4-576">Initierar kryptografi kontroll block för HMAC MD5</span><span class="sxs-lookup"><span data-stu-id="c23c4-576">Initializes the HMAC MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-577">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-577">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-578">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-578">Description</span></span>

<span data-ttu-id="c23c4-579">Med den här funktionen initieras det HMAC MD5-kontroll blocket med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-579">This function initializes the HMAC MD5 control block with the given key string.</span></span> <span data-ttu-id="c23c4-580">När HMAC MD5-kontroll blocket initieras, ska efterföljande HMAC MD5-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-580">Once the HMAC MD5 control block is initialized, subsequent HMAC MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-581">Programmet kan skapa flera HMAC MD5-kontroll block, som representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-581">Application may create multiple HMAC MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-582">Initiering av HMAC MD5-kontroll block startar en ny hash-beräknings session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-582">Initializing the HMAC MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-583">Ominitieringen av HMAC MD5 Control Block överger den aktuella sessionen och använder stjärnor som en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-583">Re-initializing the HMAC MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-584">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-584">Parameters</span></span>

- <span data-ttu-id="c23c4-585">**metod** Pekar på en giltig kontroll block för HMAC MD5-kryptografi metoden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-585">**method** Pointer to a valid HMAC MD5 crypto method control block.</span></span>
<span data-ttu-id="c23c4-586">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-586">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-587">*crypto_method_hmac_md5*</span><span class="sxs-lookup"><span data-stu-id="c23c4-587">*crypto_method_hmac_md5*</span></span>
- <span data-ttu-id="c23c4-588">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-588">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-589">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-589">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-590">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-590">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-591">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-591">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-592">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-592">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-593">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-593">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-594">**crypto_metadata** Pekar på ett giltigt minnes utrymme för det HMAC MD5-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-594">**crypto_metadata** Pointer to a valid memory space for the HMAC MD5 control block.</span></span> <span data-ttu-id="c23c4-595">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-595">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-596">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-596">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-597">För HMAC-MD5 måste storleken på metadata vara *sizeof (NX_CRYPTO_MD5_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-597">For HMAC MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-598">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-598">Return Values</span></span>

- <span data-ttu-id="c23c4-599">**NX_CRYPTO_SUCCESS** (0X00) lyckades initieras av HMAC MD5-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-599">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-601">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-601">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_md5_operation"></a><span data-ttu-id="c23c4-602">_nx_crypto_method_hmac_md5_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-602">_nx_crypto_method_hmac_md5_operation</span></span>

<span data-ttu-id="c23c4-603">Utför en HMAC MD5-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-603">Perform an HMAC MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-604">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-604">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-605">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-605">Description</span></span>

<span data-ttu-id="c23c4-606">Den här funktionen utför HMAC MD5-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-606">This function performs HMAC MD5 hash operation.</span></span> <span data-ttu-id="c23c4-607">Kontroll blocket HMAC MD5 måste ha initierats med _ *nx_crypto_method_hmac_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-607">The HMAC MD5 control block must have been initialized with _ *nx_crypto_method_hmac_md5_init()*.</span></span> <span data-ttu-id="c23c4-608">Den HMAC MD5-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-608">The HMAC MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-609">För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 16 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-609">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="c23c4-610">Den här åtgärden bevarar inte tillståndsinformation och ändrar inte nyckel materialet i HMAC MD5-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-610">This operation does not keep state information, and does not alter the key material in the HMAC MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-611">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-611">Parameters</span></span>

- <span data-ttu-id="c23c4-612">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-612">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-613">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-613">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-614">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-614">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-615">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-615">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-616">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-616">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-617">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-617">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-618">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-618">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-619">**metod** Pekar mot giltig krypterings metod för HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="c23c4-619">**method** Pointer to the valid HMAC MD5 crypto method.</span></span> <span data-ttu-id="c23c4-620">Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_hmac_md5_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-620">The crypto method used here must be the same used in the *nx_crypto_method_hmac_md5_init().*</span></span>
- <span data-ttu-id="c23c4-621">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-621">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-622">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-622">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-623">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-623">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-624">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-624">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-625">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-625">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-626">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-626">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-627">**iv_ptr** Det här fältet används inte för HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="c23c4-627">**iv_ptr** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="c23c4-628">**iv_size** Det här fältet används inte för HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="c23c4-628">**iv_size** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="c23c4-629">**output_buffer** Pekar till minnes området för den genererade HMAC MD5-hashen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-629">**output_buffer** Pointer to the memory area for the generated HMAC MD5 hash.</span></span>
- <span data-ttu-id="c23c4-630">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-630">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c23c4-631">**crypto_metadata** Pekar på det HMAC MD5-kontroll block som används i *_nx_crypto_method_hmac_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-631">**crypto_metadata** Pointer to the HMAC MD5 control block used in *_nx_crypto_method_hmac_md5_init()*.</span></span>
- <span data-ttu-id="c23c4-632">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-632">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-633">För HMAC-MD5 måste storleken på *sizeof (NX_CRYPTO_MD5_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-633">For HMAC MD5, the metadata size must *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>
- <span data-ttu-id="c23c4-634">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-634">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-635">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-635">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-636">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-636">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-637">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-637">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-638">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-638">Return Values</span></span>

- <span data-ttu-id="c23c4-639">**NX_CRYPTO_SUCCESS** (0x00) körde den HMAC MD5-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-639">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC MD5 operation.</span></span>
- <span data-ttu-id="c23c4-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-641">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-641">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-642">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC MD5-algoritm har angetts.</span><span class="sxs-lookup"><span data-stu-id="c23c4-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC MD5 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_init"></a><span data-ttu-id="c23c4-644">_nx_crypto_method_hmac_sha1_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-644">_nx_crypto_method_hmac_sha1_init</span></span>

<span data-ttu-id="c23c4-645">Initierar krypterings block för HMAC SHA1-kryptering</span><span class="sxs-lookup"><span data-stu-id="c23c4-645">Initializes the HMAC SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-646">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-646">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-647">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-647">Description</span></span>

<span data-ttu-id="c23c4-648">Den här funktionen initierar det HMAC SHA1-kontroll blocket med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-648">This function initializes the HMAC SHA1 control block with the given key string.</span></span> <span data-ttu-id="c23c4-649">När HMAC SHA1-kontroll block initieras, ska efterföljande HMAC SHA1-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-649">Once the HMAC SHA1 control block is initialized, subsequent HMAC SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-650">Programmet kan skapa flera HMAC-Control Block, som representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-650">Application may create multiple HMAC SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-651">Initiering av HMAC SHA1-kontroll block startar en ny hash-beräknings session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-651">Initializing the HMAC SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-652">Ominitieringen av HMAC SHA1 Control Block överger den aktuella sessionen och använder stjärnor som en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-652">Re-initializing the HMAC SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-653">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-653">Parameters</span></span>

- <span data-ttu-id="c23c4-654">**metod** Pekar på en giltig kontroll block för HMAC SHA1-kryptografisk metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-654">**method** Pointer to a valid HMAC SHA1 crypto method control block.</span></span> <span data-ttu-id="c23c4-655">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-655">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-656">*crypto_method_hmac_sha1*</span><span class="sxs-lookup"><span data-stu-id="c23c4-656">*crypto_method_hmac_sha1*</span></span>
- <span data-ttu-id="c23c4-657">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-657">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-658">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-658">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-659">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-659">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-660">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-660">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-661">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-661">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-662">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-662">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-663">**crypto_metadata** Pekar på ett giltigt minnes utrymme för det HMAC SHA1-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-663">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA1 control block.</span></span> <span data-ttu-id="c23c4-664">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-664">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-665">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-665">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-666">Metadata-storleken måste vara *sizeof (NX_CRYPTO_SHA1_HMAC)* för HMAC-SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-666">For HMAC SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-667">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-667">Return Values</span></span>

- <span data-ttu-id="c23c4-668">**NX_CRYPTO_SUCCESS** (0X00) slutförde initieringen av HMAC SHA1control-blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-668">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-670">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-670">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_operation"></a><span data-ttu-id="c23c4-671">_nx_crypto_method_hmac_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-671">_nx_crypto_method_hmac_sha1_operation</span></span>

<span data-ttu-id="c23c4-672">Utför HMAC SHA1-hash-åtgärd</span><span class="sxs-lookup"><span data-stu-id="c23c4-672">Perform HMAC SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-673">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-673">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-674">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-674">Description</span></span>

<span data-ttu-id="c23c4-675">Den här funktionen utför HMAC SHA1-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-675">This function performs HMAC SHA1 hash operation.</span></span> <span data-ttu-id="c23c4-676">Kontroll blocket för HMAC SHA1 måste ha initierats med _ *nx_crypto_method_hmac_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-676">The HMAC SHA1 control block must have been initialized with _ *nx_crypto_method_hmac_sha1_init()*.</span></span> <span data-ttu-id="c23c4-677">Den HMAC SHA1-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-677">The HMAC SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-678">För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 20 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-678">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-679">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-679">Parameters</span></span>

- <span data-ttu-id="c23c4-680">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-680">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-681">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-681">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-682">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-682">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-683">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-683">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-684">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-684">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-685">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-685">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-686">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-686">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-687">**metod** Pekar mot giltig krypterings metod för HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-687">**method** Pointer to the valid HMAC SHA1 crypto method.</span></span> <span data-ttu-id="c23c4-688">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha1_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-688">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha1_init().*</span></span>
- <span data-ttu-id="c23c4-689">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-689">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-690">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-690">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-691">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-691">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-692">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-692">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-693">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-693">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-694">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-694">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-695">**iv_ptr** Det här fältet används inte för HMAC-SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-695">**iv_ptr** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="c23c4-696">**iv_size** Det här fältet används inte för HMAC-SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-696">**iv_size** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="c23c4-697">**output_buffer** Pekar till minnes området för den genererade HMAC SHA1-hashen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-697">**output_buffer** Pointer to the memory area for the generated HMAC SHA1 hash.</span></span>
- <span data-ttu-id="c23c4-698">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-698">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c23c4-699">**crypto_metadata** Pekar på HMAC SHA1-kontroll block som används i *_nx_crypto_method_hmac_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-699">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>
- <span data-ttu-id="c23c4-700">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-700">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-701">Metadata-storleken för HMAC-SHA1 måste *sizeof (NX_CRYPTO_SHA1_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-701">For HMAC SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>
- <span data-ttu-id="c23c4-702">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-702">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-703">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-703">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-704">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-704">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-705">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-705">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-706">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-706">Return Values</span></span>

- <span data-ttu-id="c23c4-707">**NX_CRYPTO_SUCCESS** (0x00) körde HMAC-SHA1-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-707">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA1 operation.</span></span>
- <span data-ttu-id="c23c4-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-709">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-709">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-710">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC SHA1-algoritm har angetts.</span><span class="sxs-lookup"><span data-stu-id="c23c4-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a><span data-ttu-id="c23c4-712">_nx_crypto_method_hmac_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-712">_nx_crypto_method_hmac_sha1_cleanup</span></span>

<span data-ttu-id="c23c4-713">Rensa blockeringen av HMAC SHA1-kontroll.</span><span class="sxs-lookup"><span data-stu-id="c23c4-713">Clean up the HMAC SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-714">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-714">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-715">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-715">Description</span></span>

<span data-ttu-id="c23c4-716">Programmet anropar den här funktionen för att rensa HMAC SHA1-kontroll blocket efter det att den anger att denna HMAC SHA1-session inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-716">Application calls this function to clean up the HMAC SHA1 control block after it determines this HMAC SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-717">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-717">Parameters</span></span>

- <span data-ttu-id="c23c4-718">**crypto_metadata** Pekar på HMAC SHA1-kontroll block som används i *_nx_crypto_method_hmac_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-718">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-719">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-719">Return Values</span></span>

- <span data-ttu-id="c23c4-720">**NX_CRYPTO_SUCCESS** (0x00) rensade HMAC-SHA1-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-720">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA1 session.</span></span>
- <span data-ttu-id="c23c4-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_init"></a><span data-ttu-id="c23c4-722">_nx_crypto_method_hmac_sha256_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-722">_nx_crypto_method_hmac_sha256_init</span></span>

<span data-ttu-id="c23c4-723">Initierar SHA256 för kryptografisk kontroll av HMAC</span><span class="sxs-lookup"><span data-stu-id="c23c4-723">Initializes the HMAC SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-724">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-724">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-725">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-725">Description</span></span>

<span data-ttu-id="c23c4-726">Med den här funktionen initieras kontroll blocket för HMAC-SHA256 med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-726">This function initializes the HMAC SHA256 control block with the given key string.</span></span> <span data-ttu-id="c23c4-727">När HMAC-SHA256 kontroll block initieras, ska efterföljande HMAC SHA256-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-727">Once the HMAC SHA256 control block is initialized, subsequent HMAC SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-728">Programmet kan skapa flera SHA256 för HMAC-kontroll, som representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-728">Application may create multiple HMAC SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-729">Initierande av HMAC-SH256 kontroll block startar en ny hash-beräknings session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-729">Initializing the HMAC SH256 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-730">Ominitieringen av kontroll blocket för HMAC-SHA256 överger den aktuella sessionen och stjärnor en ny med en ny nyckel.</span><span class="sxs-lookup"><span data-stu-id="c23c4-730">Re-initializing the HMAC SHA256 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-731">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-731">Parameters</span></span>

- <span data-ttu-id="c23c4-732">**metod** Pekar på en giltig kontroll block för HMAC SHA256-kryptografisk metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-732">**method** Pointer to a valid HMAC SHA256 crypto method control block.</span></span> <span data-ttu-id="c23c4-733">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-733">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-734">*crypto_method_hmac_sha224*</span><span class="sxs-lookup"><span data-stu-id="c23c4-734">*crypto_method_hmac_sha224*</span></span>
  - <span data-ttu-id="c23c4-735">*crypto_method_hmac_sha256*</span><span class="sxs-lookup"><span data-stu-id="c23c4-735">*crypto_method_hmac_sha256*</span></span>
- <span data-ttu-id="c23c4-736">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-736">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-737">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-737">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-738">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-738">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-739">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-739">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-740">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-740">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-741">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-741">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-742">**crypto_metadata** Pekar på ett giltigt minnes utrymme för kontroll blocket för HMAC-SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-742">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA256 control block.</span></span> <span data-ttu-id="c23c4-743">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-743">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-744">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-744">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-745">För HMAC-SHA256 måste storleken på metadata vara *sizeof (NX_CRYTPO_SHA256_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-745">For HMAC SHA256, the metadata size must be *sizeof(NX_CRYTPO_SHA256_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-746">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-746">Return Values</span></span>

- <span data-ttu-id="c23c4-747">**NX_CRYPTO_SUCCESS** (0X00) lyckades initieras av HMAC-SHA256 kontroll block med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-747">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-749">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-749">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_operation"></a><span data-ttu-id="c23c4-750">_nx_crypto_method_hmac_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-750">_nx_crypto_method_hmac_sha256_operation</span></span>

<span data-ttu-id="c23c4-751">Utför hash-åtgärd för HMAC-SHA256</span><span class="sxs-lookup"><span data-stu-id="c23c4-751">Perform HMAC SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-752">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-752">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-753">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-753">Description</span></span>

<span data-ttu-id="c23c4-754">Den här funktionen utför hash-åtgärden för HMAC-SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-754">This function performs HMAC SHA256 hash operation.</span></span> <span data-ttu-id="c23c4-755">Kontroll blocket för HMAC-SHA256 måste ha initierats med _ *nx_crypto_method_hmac_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-755">The HMAC SHA256 control block must have been initialized with _ *nx_crypto_method_hmac_sha256_init()*.</span></span> <span data-ttu-id="c23c4-756">Den HMAC SHA256-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-756">The HMAC SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-757">För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 32 byte för SHA256, eller 28 byte för SHA224.</span><span class="sxs-lookup"><span data-stu-id="c23c4-757">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-758">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-758">Parameters</span></span>

- <span data-ttu-id="c23c4-759">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-759">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-760">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-760">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-761">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-761">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-762">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-762">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-763">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-763">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-764">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-764">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-765">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-765">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-766">**metod** Pekar mot den giltiga kryptografi metoden för HMAC-SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-766">**method** Pointer to the valid HMAC SHA256 crypto method.</span></span> <span data-ttu-id="c23c4-767">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha256_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-767">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha256_init().*</span></span>
- <span data-ttu-id="c23c4-768">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-768">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-769">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-769">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-770">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-770">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-771">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-771">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-772">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-772">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-773">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-773">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-774">**iv_ptr** Det här fältet används inte för HMAC-SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-774">**iv_ptr** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="c23c4-775">**iv_size** Det här fältet används inte för HMAC-SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-775">**iv_size** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="c23c4-776">**output_buffer** Pekar till minnes området för den genererade HMAC-SHA256 hash.</span><span class="sxs-lookup"><span data-stu-id="c23c4-776">**output_buffer** Pointer to the memory area for the generated HMAC SHA256 hash.</span></span>
- <span data-ttu-id="c23c4-777">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-777">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c23c4-778">**crypto_metadata** Pekar på det HMAC-SHA256 kontroll block som används i *_nx_crypto_method_hmac_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-778">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>
- <span data-ttu-id="c23c4-779">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-779">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-780">För HMAC-SHA256 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA256_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-780">For HMAC SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256_HMAC)*</span></span>
- <span data-ttu-id="c23c4-781">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-781">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-782">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-782">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-783">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-783">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-784">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-784">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-785">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-785">Return Values</span></span>

- <span data-ttu-id="c23c4-786">**NX_CRYPTO_SUCCESS** (0x00) körde åtgärden HMAC-SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-786">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA256 operation.</span></span>
- <span data-ttu-id="c23c4-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-788">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-788">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-789">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC-SHA256-algoritm har angetts.</span><span class="sxs-lookup"><span data-stu-id="c23c4-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a><span data-ttu-id="c23c4-791">_nx_crypto_method_hmac_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-791">_nx_crypto_method_hmac_sha256_cleanup</span></span>

<span data-ttu-id="c23c4-792">Rensa bort HMAC-SHA256 kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-792">Clean up the HMAC SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-793">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-793">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-794">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-794">Description</span></span>

<span data-ttu-id="c23c4-795">Programmet anropar den här funktionen för att rensa HMAC-SHA256 kontroll block efter det att den anger att denna HMAC SHA256-session inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-795">Application calls this function to clean up the HMAC SHA256 control block after it determines this HMAC SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-796">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-796">Parameters</span></span>

- <span data-ttu-id="c23c4-797">**crypto_metadata** Pekar på det HMAC-SHA256 kontroll block som används i *_nx_crypto_method_hmac_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-797">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-798">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-798">Return Values</span></span>

- <span data-ttu-id="c23c4-799">**NX_CRYPTO_SUCCESS** (0x00) rensade HMAC-SHA256-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-799">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA256 session.</span></span>
- <span data-ttu-id="c23c4-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_init"></a><span data-ttu-id="c23c4-801">_nx_crypto_method_hmac_sha512_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-801">_nx_crypto_method_hmac_sha512_init</span></span>

<span data-ttu-id="c23c4-802">Initierar SHA512 för kryptografisk kontroll av HMAC</span><span class="sxs-lookup"><span data-stu-id="c23c4-802">Initializes the HMAC SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-803">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-803">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-804">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-804">Description</span></span>

<span data-ttu-id="c23c4-805">Med den här funktionen initieras kontroll blocket för HMAC-SHA512 med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-805">This function initializes the HMAC SHA512 control block with the given key string.</span></span> <span data-ttu-id="c23c4-806">När HMAC-SHA512 kontroll block initieras, ska efterföljande HMAC SHA512-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-806">Once the HMAC SHA512 control block is initialized, subsequent HMAC SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-807">Programmet kan skapa flera SHA512 för HMAC-kontroll, som representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-807">Application may create multiple HMAC SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-808">Initierande av HMAC-SH512 kontroll block startar en ny hash-beräknings session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-808">Initializing the HMAC SH512 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-809">Ominitieringen av kontroll blocket för HMAC-SHA512 överger den aktuella sessionen och stjärnor en ny med en ny nyckel.</span><span class="sxs-lookup"><span data-stu-id="c23c4-809">Re-initializing the HMAC SHA512 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-810">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-810">Parameters</span></span>

- <span data-ttu-id="c23c4-811">**metod** Pekar på en giltig kontroll block för HMAC SHA512-kryptografisk metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-811">**method** Pointer to a valid HMAC SHA512 crypto method control block.</span></span> <span data-ttu-id="c23c4-812">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-812">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-813">*crypto_method_hmac_sha384*</span><span class="sxs-lookup"><span data-stu-id="c23c4-813">*crypto_method_hmac_sha384*</span></span>
  - <span data-ttu-id="c23c4-814">*crypto_method_hmac_sha512*</span><span class="sxs-lookup"><span data-stu-id="c23c4-814">*crypto_method_hmac_sha512*</span></span>
- <span data-ttu-id="c23c4-815">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-815">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-816">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-816">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-817">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-817">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-818">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-818">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-819">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-819">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-820">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-820">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-821">**crypto_metadata** Pekar på ett giltigt minnes utrymme för kontroll blocket för HMAC-SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-821">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA512 control block.</span></span> <span data-ttu-id="c23c4-822">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-822">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-823">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-823">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-824">För HMAC-SHA512 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA512_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-824">For HMAC SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-825">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-825">Return Values</span></span>

- <span data-ttu-id="c23c4-826">**NX_CRYPTO_SUCCESS** (0X00) lyckades initieras av HMAC-SHA512 kontroll block med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-826">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-828">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-828">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_operation"></a><span data-ttu-id="c23c4-829">_nx_crypto_method_hmac_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-829">_nx_crypto_method_hmac_sha512_operation</span></span>

<span data-ttu-id="c23c4-830">Utför hash-åtgärd för HMAC-SHA512</span><span class="sxs-lookup"><span data-stu-id="c23c4-830">Perform HMAC SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-831">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-831">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-832">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-832">Description</span></span>

<span data-ttu-id="c23c4-833">Den här funktionen utför hash-åtgärden för HMAC-SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-833">This function performs HMAC SHA512 hash operation.</span></span> <span data-ttu-id="c23c4-834">Kontroll blocket för HMAC-SHA512 måste ha initierats med _ *nx_crypto_method_hmac_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-834">The HMAC SHA512 control block must have been initialized with _ *nx_crypto_method_hmac_sha512_init()*.</span></span> <span data-ttu-id="c23c4-835">Den HMAC SHA512-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-835">The HMAC SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-836">För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 64 byte för SHA512, eller 48 byte för SHA384.</span><span class="sxs-lookup"><span data-stu-id="c23c4-836">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-837">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-837">Parameters</span></span>

- <span data-ttu-id="c23c4-838">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-838">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-839">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-839">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-840">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-840">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-841">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-841">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-842">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-842">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-843">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-843">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-844">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-844">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-845">**metod** Pekar mot den giltiga kryptografi metoden för HMAC-SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-845">**method** Pointer to the valid HMAC SHA512 crypto method.</span></span> <span data-ttu-id="c23c4-846">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha512_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-846">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha512_init().*</span></span>
- <span data-ttu-id="c23c4-847">**nyckel** Pekar på nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c23c4-847">**key** Points to the key.</span></span> <span data-ttu-id="c23c4-848">Det finns inga begränsningar för nyckel-buffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-848">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c23c4-849">**key_size_in_bits** Nyckelns storlek i bitar.</span><span class="sxs-lookup"><span data-stu-id="c23c4-849">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c23c4-850">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-850">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-851">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-851">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-852">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-852">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-853">**iv_ptr** Det här fältet används inte för HMAC-SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-853">**iv_ptr** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="c23c4-854">**iv_size** Det här fältet används inte för HMAC-SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-854">**iv_size** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="c23c4-855">**output_buffer** Pekar till minnes området för den genererade HMAC-SHA512 hash.</span><span class="sxs-lookup"><span data-stu-id="c23c4-855">**output_buffer** Pointer to the memory area for the generated HMAC SHA512 hash.</span></span>
- <span data-ttu-id="c23c4-856">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-856">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c23c4-857">**crypto_metadata** Pekar på det HMAC-SHA512 kontroll block som används i *_nx_crypto_method_hmac_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-857">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>
- <span data-ttu-id="c23c4-858">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-858">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-859">För HMAC-SHA512 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA512_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-859">For HMAC SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>
- <span data-ttu-id="c23c4-860">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-860">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-861">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-861">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-862">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-862">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-863">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-863">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-864">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-864">Return Values</span></span>

- <span data-ttu-id="c23c4-865">**NX_CRYPTO_SUCCESS** (0x00) körde åtgärden HMAC-SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-865">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA512 operation.</span></span>
- <span data-ttu-id="c23c4-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-867">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-867">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-868">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC-SHA512-algoritm har angetts.</span><span class="sxs-lookup"><span data-stu-id="c23c4-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a><span data-ttu-id="c23c4-870">_nx_crypto_method_hmac_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-870">_nx_crypto_method_hmac_sha512_cleanup</span></span>

<span data-ttu-id="c23c4-871">Rensa bort HMAC-SHA512 kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-871">Clean up the HMAC SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-872">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-872">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-873">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-873">Description</span></span>

<span data-ttu-id="c23c4-874">Programmet anropar den här funktionen för att rensa HMAC-SHA512 kontroll block efter det att den anger att denna HMAC SHA512-session inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-874">Application calls this function to clean up the HMAC SHA512 control block after it determines this HMAC SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-875">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-875">Parameters</span></span>

- <span data-ttu-id="c23c4-876">**crypto_metadata** Pekar på det HMAC-SHA512 kontroll block som används i *_nx_crypto_method_hmac_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-876">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-877">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-877">Return Values</span></span>

- <span data-ttu-id="c23c4-878">**NX_CRYPTO_SUCCESS** (0x00) rensade HMAC-SHA512-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-878">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA512 session.</span></span>
- <span data-ttu-id="c23c4-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

### <a name="example"></a><span data-ttu-id="c23c4-880">Exempel</span><span class="sxs-lookup"><span data-stu-id="c23c4-880">Example</span></span> 

## <a name="_nx_crypto_method_md5_init"></a><span data-ttu-id="c23c4-881">_nx_crypto_method_md5_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-881">_nx_crypto_method_md5_init</span></span>

<span data-ttu-id="c23c4-882">Initierar MD5-kontroll blocket</span><span class="sxs-lookup"><span data-stu-id="c23c4-882">Initializes the MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-883">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-883">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-884">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-884">Description</span></span>

<span data-ttu-id="c23c4-885">Den här funktionen initierar MD5-kontroll blocket med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-885">This function initializes the MD5 control block with the given key string.</span></span> <span data-ttu-id="c23c4-886">När MD5-kontroll blocket initieras, använder den efterföljande MD5-åtgärden samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-886">Once the MD5 control block is initialized, subsequent MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-887">Programmet kan skapa flera MD5-kontroll block, som representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-887">Application may create multiple MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-888">Initiering av MD5 Control Block startar en ny session för hash-beräkning.</span><span class="sxs-lookup"><span data-stu-id="c23c4-888">Initializing the MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-889">Ominitieringen av MD5 Control Block överger den aktuella sessionen och stjärnor med en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-889">Re-initializing the MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-890">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-890">Parameters</span></span>

- <span data-ttu-id="c23c4-891">**metod** Pekar på en giltig MD5-metod för kryptering av kryptografiska metoder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-891">**method** Pointer to a valid MD5 crypto method control block.</span></span> <span data-ttu-id="c23c4-892">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-892">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-893">*crypto_method_md5*</span><span class="sxs-lookup"><span data-stu-id="c23c4-893">*crypto_method_md5*</span></span>
- <span data-ttu-id="c23c4-894">**nyckel** Det här fältet används inte för MD5.</span><span class="sxs-lookup"><span data-stu-id="c23c4-894">**key** This field is not used for MD5.</span></span>
- <span data-ttu-id="c23c4-895">**key_size_in_bits** Det här fältet används inte för MD5</span><span class="sxs-lookup"><span data-stu-id="c23c4-895">**key_size_in_bits** This field is not used for MD5</span></span>
- <span data-ttu-id="c23c4-896">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-896">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-897">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-897">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-898">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-898">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-899">**crypto_metadata** Pekar på ett giltigt minnes utrymme för MD5-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-899">**crypto_metadata** Pointer to a valid memory space for the MD5 control block.</span></span> <span data-ttu-id="c23c4-900">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-900">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-901">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-901">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-902">För MD5 måste metadatans storlek vara *sizeof (NX_CRYPTO_MD5)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-902">For MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-903">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-903">Return Values</span></span>

- <span data-ttu-id="c23c4-904">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera MD5-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-904">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-906">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-906">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

### <a name="example"></a><span data-ttu-id="c23c4-907">Exempel</span><span class="sxs-lookup"><span data-stu-id="c23c4-907">Example</span></span>

## <a name="_nx_crypto_method_md5_operation"></a><span data-ttu-id="c23c4-908">_nx_crypto_method_md5_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-908">_nx_crypto_method_md5_operation</span></span>

<span data-ttu-id="c23c4-909">Utföra en MD5-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-909">Perform an MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-910">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-910">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-911">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-911">Description</span></span>

<span data-ttu-id="c23c4-912">Den här funktionen utför MD5-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-912">This function performs MD5 hash operation.</span></span> <span data-ttu-id="c23c4-913">MD5-kontroll blocket måste ha initierats med _ *nx_crypto_method_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-913">The MD5 control block must have been initialized with _ *nx_crypto_method_md5_init()*.</span></span> <span data-ttu-id="c23c4-914">MD5-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-914">The MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-915">För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 16 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-915">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="c23c4-916">Den här åtgärden bevarar inte tillståndsinformation och ändrar inte nyckel materialet i MD5-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-916">This operation does not keep state information and does not alter the key material in the MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-917">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-917">Parameters</span></span>

- <span data-ttu-id="c23c4-918">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-918">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-919">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-919">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-920">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-920">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-921">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-921">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-922">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-922">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-923">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-923">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-924">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-924">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-925">**metod** Pekare till den giltiga MD5-kryptografi metoden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-925">**method** Pointer to the valid MD5 crypto method.</span></span> <span data-ttu-id="c23c4-926">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_md5_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-926">The crypto method used here must be the same used in the _ *nx_crypto_method_md5_init().*</span></span>
- <span data-ttu-id="c23c4-927">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-927">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-928">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-928">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-929">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-929">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-930">**iv_ptr** Det här fältet används inte för MD5.</span><span class="sxs-lookup"><span data-stu-id="c23c4-930">**iv_ptr** This field is not used for MD5.</span></span>
- <span data-ttu-id="c23c4-931">**iv_size** Det här fältet används inte för MD5.</span><span class="sxs-lookup"><span data-stu-id="c23c4-931">**iv_size** This field is not used for MD5.</span></span>
- <span data-ttu-id="c23c4-932">**output_buffer** Pekar till minnes området för den genererade MD5-hashen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-932">**output_buffer** Pointer to the memory area for the generated MD5 hash.</span></span>
- <span data-ttu-id="c23c4-933">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-933">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c23c4-934">För MD5 måste buffertstorleken vara 16 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-934">For MD5 the buffer size must be 16 bytes.</span></span>
- <span data-ttu-id="c23c4-935">**crypto_metadata** Pekar på MD5-kontroll block som används i *_nx_crypto_method_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-935">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>
- <span data-ttu-id="c23c4-936">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-936">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-937">För MD5 måste metadatans storlek *sizeof (NX_CRYPTO_MD5)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-937">For MD5, the metadata size must *sizeof(NX_CRYPTO_MD5)*</span></span>
- <span data-ttu-id="c23c4-938">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-938">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-939">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-939">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-940">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-940">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-941">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-941">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-942">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-942">Return Values</span></span>

- <span data-ttu-id="c23c4-943">**NX_CRYPTO_SUCCESS** (0x00) körde MD5-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-943">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the MD5 operation.</span></span>
- <span data-ttu-id="c23c4-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-945">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-945">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-946">En ogiltig MD5-algoritm har angetts för **NX_CRYPTO_INVALID_ALGORITHM** (0x20004).</span><span class="sxs-lookup"><span data-stu-id="c23c4-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid MD5 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_md5_cleanup"></a><span data-ttu-id="c23c4-948">_nx_crypto_method_md5_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-948">_nx_crypto_method_md5_cleanup</span></span>

<span data-ttu-id="c23c4-949">Rensa MD5-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-949">Clean up the MD5 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-950">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-950">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-951">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-951">Description</span></span>

<span data-ttu-id="c23c4-952">Programmet anropar den här funktionen för att rensa MD5-kontroll blocket när den anger att den här MD5-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-952">Application calls this function to clean up the MD5 control block after it determines this MD5 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-953">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-953">Parameters</span></span>

- <span data-ttu-id="c23c4-954">**crypto_metadata** Pekar på MD5-kontroll block som används i *_nx_crypto_method_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-954">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-955">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-955">Return Values</span></span>

- <span data-ttu-id="c23c4-956">**NX_CRYPTO_SUCCESS** (0x00) rensade MD5-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-956">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the MD5 session.</span></span>
- <span data-ttu-id="c23c4-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha1_init"></a><span data-ttu-id="c23c4-958">_nx_crypto_method_sha1_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-958">_nx_crypto_method_sha1_init</span></span>

<span data-ttu-id="c23c4-959">Initierar kontroll block för SHA1-krypto</span><span class="sxs-lookup"><span data-stu-id="c23c4-959">Initializes the SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-960">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-960">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-961">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-961">Description</span></span>

<span data-ttu-id="c23c4-962">Den här funktionen initierar SHA1-kontrolls blocket med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-962">This function initializes the SHA1 control block with the given key string.</span></span> <span data-ttu-id="c23c4-963">När SHA1-Control-blocket initieras, ska den efterföljande SHA1-åtgärden använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-963">Once the SHA1 control block is initialized, subsequent SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-964">Programmet kan skapa flera SHA1-kontroll block, som var och en representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-964">Application may create multiple SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-965">Initiering av SHA1 Control Block startar en ny session för hash-beräkning.</span><span class="sxs-lookup"><span data-stu-id="c23c4-965">Initializing the SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-966">Om du initierar om SHA1 Control Block överges den aktuella sessionen och stjärnoren är en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-966">Re-initializing the SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-967">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-967">Parameters</span></span>

- <span data-ttu-id="c23c4-968">**metod** Pekar mot en giltig SHA1-kontroll block för krypterings metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-968">**method** Pointer to a valid SHA1 crypto method control block.</span></span> <span data-ttu-id="c23c4-969">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-969">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-970">*crypto_method_sha1*</span><span class="sxs-lookup"><span data-stu-id="c23c4-970">*crypto_method_sha1*</span></span>
- <span data-ttu-id="c23c4-971">**nyckel** Det här fältet används inte för SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-971">**key** This field is not used for SHA1.</span></span>
- <span data-ttu-id="c23c4-972">**key_size_in_bits** Det här fältet används inte för SHA1</span><span class="sxs-lookup"><span data-stu-id="c23c4-972">**key_size_in_bits** This field is not used for SHA1</span></span>
- <span data-ttu-id="c23c4-973">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-973">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-974">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-974">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-975">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-975">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-976">**crypto_metadata** Pekar på ett giltigt minnes utrymme för SHA1-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-976">**crypto_metadata** Pointer to a valid memory space for the SHA1 control block.</span></span> <span data-ttu-id="c23c4-977">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-977">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-978">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-978">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-979">För SHA1 måste metadatans storlek vara *sizeof (NX_CRYPTO_SHA1)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-979">For SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-980">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-980">Return Values</span></span>

- <span data-ttu-id="c23c4-981">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera SHA1control-blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-981">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-983">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-983">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha1_operation"></a><span data-ttu-id="c23c4-984">_nx_crypto_method_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-984">_nx_crypto_method_sha1_operation</span></span>

<span data-ttu-id="c23c4-985">Utför SHA1-hash-åtgärd</span><span class="sxs-lookup"><span data-stu-id="c23c4-985">Perform SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-986">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-986">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-987">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-987">Description</span></span>

<span data-ttu-id="c23c4-988">Den här funktionen utför SHA1-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-988">This function performs SHA1 hash operation.</span></span> <span data-ttu-id="c23c4-989">SHA1-kontroll blocket måste ha initierats med _ *nx_crypto_method_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-989">The SHA1 control block must have been initialized with _ *nx_crypto_method_sha1_init()*.</span></span> <span data-ttu-id="c23c4-990">Den SHA1-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-990">The SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-991">För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 20 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-991">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-992">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-992">Parameters</span></span>

- <span data-ttu-id="c23c4-993">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-993">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-994">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-994">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-995">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-995">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-996">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-996">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-997">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-997">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-998">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-998">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-999">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-999">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-1000">**metod** Pekare till giltig SHA1-kryptografisk metod.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1000">**method** Pointer to the valid SHA1 crypto method.</span></span> <span data-ttu-id="c23c4-1001">Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_sha1_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1001">The crypto method used here must be the same used in the *nx_crypto_method_sha1_init().*</span></span>
- <span data-ttu-id="c23c4-1002">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1002">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-1003">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1003">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-1004">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1004">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-1005">**iv_ptr** Det här fältet används inte för SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1005">**iv_ptr** This field is not used for SHA1.</span></span>
- <span data-ttu-id="c23c4-1006">**iv_size** Det här fältet används inte för SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1006">**iv_size** This field is not used for SHA1.</span></span>
- <span data-ttu-id="c23c4-1007">**output_buffer** Pekar till minnes området för den genererade SHA1-hashen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1007">**output_buffer** Pointer to the memory area for the generated SHA1 hash.</span></span>
- <span data-ttu-id="c23c4-1008">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1008">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c23c4-1009">Buffertstorleken måste vara 20 byte för SHA1.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1009">For SHA1 the buffer size must be 20 bytes.</span></span>
- <span data-ttu-id="c23c4-1010">**crypto_metadata** Pekar på SHA1-kontroll block som används i *_nx_crypto_method_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1010">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>
- <span data-ttu-id="c23c4-1011">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1011">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-1012">För SHA1 måste metadatans storlek *sizeof (NX_CRYPTO_SHA1)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1012">For SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1)*</span></span>
- <span data-ttu-id="c23c4-1013">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1013">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1014">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1014">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-1015">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1015">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1016">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1016">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1017">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1017">Return Values</span></span>

- <span data-ttu-id="c23c4-1018">**NX_CRYPTO_SUCCESS** (0x00) körde SHA1-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1018">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA1 operation.</span></span>
- <span data-ttu-id="c23c4-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-1020">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1020">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig SHA1-algoritm har angetts.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

### <a name="example"></a><span data-ttu-id="c23c4-1023">Exempel</span><span class="sxs-lookup"><span data-stu-id="c23c4-1023">Example</span></span>

## <a name="_nx_crypto_method_sha1_cleanup"></a><span data-ttu-id="c23c4-1024">_nx_crypto_method_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-1024">_nx_crypto_method_sha1_cleanup</span></span>

<span data-ttu-id="c23c4-1025">Rensa SHA1-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1025">Clean up the SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-1026">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-1026">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-1027">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-1027">Description</span></span>

<span data-ttu-id="c23c4-1028">Programmet anropar den här funktionen för att rensa SHA1-kontroll blocket när den har angett att den här SHA1-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1028">Application calls this function to clean up the SHA1 control block after it determines this SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-1029">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-1029">Parameters</span></span>

- <span data-ttu-id="c23c4-1030">**crypto_metadata** Pekar på SHA1-kontroll block som används i *_nx_crypto_method_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1030">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1031">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1031">Return Values</span></span>

- <span data-ttu-id="c23c4-1032">**NX_CRYPTO_SUCCESS** (0X00) har rensat SHA1-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1032">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA1 session.</span></span>
- <span data-ttu-id="c23c4-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha256_init"></a><span data-ttu-id="c23c4-1034">_nx_crypto_method_sha256_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-1034">_nx_crypto_method_sha256_init</span></span>

<span data-ttu-id="c23c4-1035">Initierar kontroll block för SHA256-kryptografi</span><span class="sxs-lookup"><span data-stu-id="c23c4-1035">Initializes the SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-1036">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-1036">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a><span data-ttu-id="c23c4-1037">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-1037">Description</span></span>

<span data-ttu-id="c23c4-1038">Den här funktionen initierar kontroll blocket SHA256 med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1038">This function initializes the SHA256 control block with the given key string.</span></span> <span data-ttu-id="c23c4-1039">När SHA256-kontroll blocket initieras, ska efterföljande SHA256-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1039">Once the SHA256 control block is initialized, subsequent SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-1040">Programmet kan skapa flera SHA256-kontroll block, som var och en representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1040">Application may create multiple SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-1041">Initieringen av SHA256 Control Block startar en ny session med hash-beräkning.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1041">Initializing the SHA256 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-1042">Ominitieringen av kontroll blocket SHA256 överger den aktuella sessionen och använder stjärnorna som en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1042">Re-initializing the SHA256 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-1043">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-1043">Parameters</span></span>

- <span data-ttu-id="c23c4-1044">**metod** Pekar på ett giltigt kontroll block för SHA256-kryptografiska metoder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1044">**method** Pointer to a valid SHA256 crypto method control block.</span></span> <span data-ttu-id="c23c4-1045">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-1045">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-1046">*crypto_method_sha256*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1046">*crypto_method_sha256*</span></span>
  - <span data-ttu-id="c23c4-1047">*crypto_method_sha224*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1047">*crypto_method_sha224*</span></span>
- <span data-ttu-id="c23c4-1048">**nyckel** Det här fältet används inte för SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1048">**key** This field is not used for SHA256.</span></span>
- <span data-ttu-id="c23c4-1049">**key_size_in_bits** Det här fältet används inte för SHA256</span><span class="sxs-lookup"><span data-stu-id="c23c4-1049">**key_size_in_bits** This field is not used for SHA256</span></span>
- <span data-ttu-id="c23c4-1050">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1050">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-1051">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1051">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-1052">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1052">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-1053">**crypto_metadata** Pekar på ett giltigt minnes utrymme för SHA256-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1053">**crypto_metadata** Pointer to a valid memory space for the SHA256 control block.</span></span> <span data-ttu-id="c23c4-1054">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1054">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-1055">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1055">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-1056">För SHA256 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA256)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1056">For SHA256, the metadata size must be *sizeof(NX_CRYPTO_SHA256)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1057">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1057">Return Values</span></span>

- <span data-ttu-id="c23c4-1058">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera SHA256-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1058">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-1060">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1060">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha256_operation"></a><span data-ttu-id="c23c4-1061">_nx_crypto_method_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-1061">_nx_crypto_method_sha256_operation</span></span>

<span data-ttu-id="c23c4-1062">Utför SHA256-hash-åtgärd</span><span class="sxs-lookup"><span data-stu-id="c23c4-1062">Perform SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-1063">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-1063">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c23c4-1064">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-1064">Description</span></span>

<span data-ttu-id="c23c4-1065">Den här funktionen utför SHA256-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1065">This function performs SHA256 hash operation.</span></span> <span data-ttu-id="c23c4-1066">Kontroll blocket SHA256 måste ha initierats med _ ***nx_crypto_method_sha256_init ()***.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1066">The SHA256 control block must have been initialized with _ ***nx_crypto_method_sha256_init()***.</span></span> <span data-ttu-id="c23c4-1067">SHA256-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1067">The SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-1068">För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 32 byte för SHA256, eller 28 byte för SHA224.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1068">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-1069">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-1069">Parameters</span></span>

- <span data-ttu-id="c23c4-1070">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1070">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-1071">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-1071">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-1072">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1072">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-1073">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1073">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-1074">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1074">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-1075">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1075">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1076">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1076">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-1077">**metod** Pekare till den giltiga SHA256-kryptografi metoden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1077">**method** Pointer to the valid SHA256 crypto method.</span></span> <span data-ttu-id="c23c4-1078">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_sha256_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1078">The crypto method used here must be the same used in the _ *nx_crypto_method_sha256_init().*</span></span>
- <span data-ttu-id="c23c4-1079">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1079">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-1080">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1080">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-1081">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1081">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-1082">**iv_ptr** Det här fältet används inte för SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1082">**iv_ptr** This field is not used for SHA256.</span></span>
- <span data-ttu-id="c23c4-1083">**iv_size** Det här fältet används inte för SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1083">**iv_size** This field is not used for SHA256.</span></span>
- <span data-ttu-id="c23c4-1084">**output_buffer** Pekar till minnes området för den genererade SHA256-hashen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1084">**output_buffer** Pointer to the memory area for the generated SHA256 hash.</span></span>
- <span data-ttu-id="c23c4-1085">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1085">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c23c4-1086">För SHA256 måste buffertstorleken vara 32 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1086">For SHA256 the buffer size must be 32 bytes.</span></span> <span data-ttu-id="c23c4-1087">För SHA224 måste buffertstorleken vara 28 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1087">For SHA224 the buffer size must be 28 bytes.</span></span>
- <span data-ttu-id="c23c4-1088">**crypto_metadata** Pekare till SHA2-kontroll blocket som används i *_nx_crypto_method_sha2_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1088">**crypto_metadata** Pointer to the SHA2 control block used in *_nx_crypto_method_sha2_init()*.</span></span>
- <span data-ttu-id="c23c4-1089">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1089">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-1090">För SHA256 måste metadata *-storleken sizeof (NX_CRYPTO_SHA256)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1090">For SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256)*</span></span>
- <span data-ttu-id="c23c4-1091">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1091">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1092">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1092">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-1093">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1093">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1094">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1094">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1095">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1095">Return Values</span></span>

- <span data-ttu-id="c23c4-1096">**NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1096">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA256 operation.</span></span>
- <span data-ttu-id="c23c4-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-1098">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1098">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig SHA256-algoritm anges.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha256_cleanup"></a><span data-ttu-id="c23c4-1101">_nx_crypto_method_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-1101">_nx_crypto_method_sha256_cleanup</span></span>

<span data-ttu-id="c23c4-1102">Rensa kontroll blocket SHA256.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1102">Clean up the SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-1103">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-1103">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-1104">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-1104">Description</span></span>

<span data-ttu-id="c23c4-1105">Programmet anropar den här funktionen för att rensa SHA256-kontroll blocket när den har bedömt att den här SHA256-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1105">Application calls this function to clean up the SHA256 control block after it determines this SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-1106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-1106">Parameters</span></span>

- <span data-ttu-id="c23c4-1107">**crypto_metadata** Pekare till SHA256-kontroll blocket som används i *_nx_crypto_method_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1107">**crypto_metadata** Pointer to the SHA256 control block used in *_nx_crypto_method_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1108">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1108">Return Values</span></span>

- <span data-ttu-id="c23c4-1109">**NX_CRYPTO_SUCCESS** (0X00) har rensat SHA256-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1109">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA256 session.</span></span>
- <span data-ttu-id="c23c4-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha512_init"></a><span data-ttu-id="c23c4-1111">_nx_crypto_method_sha512_init</span><span class="sxs-lookup"><span data-stu-id="c23c4-1111">_nx_crypto_method_sha512_init</span></span>

<span data-ttu-id="c23c4-1112">Initierar kontroll block för SHA512-kryptografi</span><span class="sxs-lookup"><span data-stu-id="c23c4-1112">Initializes the SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-1113">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-1113">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c23c4-1114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-1114">Description</span></span>

<span data-ttu-id="c23c4-1115">Den här funktionen initierar kontroll blocket SHA512 med den aktuella nyckel strängen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1115">This function initializes the SHA512 control block with the given key string.</span></span> <span data-ttu-id="c23c4-1116">När SHA512-kontroll blocket initieras, ska efterföljande SHA512-åtgärd använda samma kontroll block.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1116">Once the SHA512 control block is initialized, subsequent SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="c23c4-1117">Programmet kan skapa flera SHA512-kontroll block, som var och en representerar en session.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1117">Application may create multiple SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="c23c4-1118">Initieringen av SHA512 Control Block startar en ny session med hash-beräkning.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1118">Initializing the SHA512 control block starts a new hash computation session.</span></span> <span data-ttu-id="c23c4-1119">Ominitieringen av kontroll blocket SHA512 överger den aktuella sessionen och använder stjärnorna som en ny.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1119">Re-initializing the SHA512 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-1120">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-1120">Parameters</span></span>

- <span data-ttu-id="c23c4-1121">**metod** Pekar på ett giltigt kontroll block för SHA512-kryptografiska metoder.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1121">**method** Pointer to a valid SHA512 crypto method control block.</span></span> <span data-ttu-id="c23c4-1122">Följande fördefinierade krypterings metoder är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="c23c4-1122">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c23c4-1123">*crypto_method_sha512*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1123">*crypto_method_sha512*</span></span>
  - <span data-ttu-id="c23c4-1124">*crypto_method_sha384*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1124">*crypto_method_sha384*</span></span>
- <span data-ttu-id="c23c4-1125">**nyckel** Det här fältet används inte för SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1125">**key** This field is not used for SHA512.</span></span>
- <span data-ttu-id="c23c4-1126">**key_size_in_bits** Det här fältet används inte för SHA512</span><span class="sxs-lookup"><span data-stu-id="c23c4-1126">**key_size_in_bits** This field is not used for SHA512</span></span>
- <span data-ttu-id="c23c4-1127">**Hantera** Den här tjänsten returnerar en referens till anroparen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1127">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c23c4-1128">Referensen är implementerings beroende och används inte i den här implementeringen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1128">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c23c4-1129">Programmet ska skicka NULL för referensen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1129">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c23c4-1130">**crypto_metadata** Pekar på ett giltigt minnes utrymme för SHA512-kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1130">**crypto_metadata** Pointer to a valid memory space for the SHA512 control block.</span></span> <span data-ttu-id="c23c4-1131">Start adressen för minnes utrymmet måste vara 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1131">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c23c4-1132">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1132">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-1133">För SHA512 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA512)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1133">For SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1134">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1134">Return Values</span></span>

- <span data-ttu-id="c23c4-1135">**NX_CRYPTO_SUCCESS** (0X00) lyckades initiera SHA512-kontroll blocket med nyckel-och nyckel storleken.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1135">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="c23c4-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-1137">**NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1137">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha512_operation"></a><span data-ttu-id="c23c4-1138">_nx_crypto_method_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="c23c4-1138">_nx_crypto_method_sha512_operation</span></span>

<span data-ttu-id="c23c4-1139">Utför SHA512-hash-åtgärd</span><span class="sxs-lookup"><span data-stu-id="c23c4-1139">Perform SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-1140">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-1140">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="c23c4-1141">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-1141">Description</span></span>

<span data-ttu-id="c23c4-1142">Den här funktionen utför SHA512-hash-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1142">This function performs SHA512 hash operation.</span></span> <span data-ttu-id="c23c4-1143">Kontroll blocket SHA512 måste ha initierats med _ *nx_crypto_method_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1143">The SHA512 control block must have been initialized with _ *nx_crypto_method_sha512_init()*.</span></span> <span data-ttu-id="c23c4-1144">SHA512-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1144">The SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c23c4-1145">För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 64 byte för SHA512, eller 48 byte för SHA384.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1145">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-1146">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-1146">Parameters</span></span>

- <span data-ttu-id="c23c4-1147">**op** Typ av åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1147">**op** Type of operation to perform.</span></span> <span data-ttu-id="c23c4-1148">En giltig åtgärd är:</span><span class="sxs-lookup"><span data-stu-id="c23c4-1148">Valid operation is:</span></span>
  - <span data-ttu-id="c23c4-1149">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1149">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c23c4-1150">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1150">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c23c4-1151">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1151">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c23c4-1152">**Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1152">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1153">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1153">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-1154">**metod** Pekare till den giltiga SHA512-kryptografi metoden.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1154">**method** Pointer to the valid SHA512 crypto method.</span></span> <span data-ttu-id="c23c4-1155">Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_sha512_init ().*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1155">The crypto method used here must be the same used in the _ *nx_crypto_method_sha512_init().*</span></span>
- <span data-ttu-id="c23c4-1156">**input_data** Pekar på en buffert som innehåller indata för text.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1156">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c23c4-1157">Det finns inga begränsningar för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1157">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c23c4-1158">**input_data_size** Storlek på indata, i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1158">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c23c4-1159">**iv_ptr** Det här fältet används inte för SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1159">**iv_ptr** This field is not used for SHA512.</span></span>
- <span data-ttu-id="c23c4-1160">**iv_size** Det här fältet används inte för SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1160">**iv_size** This field is not used for SHA512.</span></span>
- <span data-ttu-id="c23c4-1161">**output_buffer** Pekar till minnes området för den genererade SHA512-hashen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1161">**output_buffer** Pointer to the memory area for the generated SHA512 hash.</span></span>
- <span data-ttu-id="c23c4-1162">**output_buffer_size** Storlek på utdatabufferten i byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1162">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c23c4-1163">För SHA512 måste buffertstorleken vara 64 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1163">For SHA512 the buffer size must be 64 bytes.</span></span> <span data-ttu-id="c23c4-1164">För SHA384 måste buffertstorleken vara 48 byte.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1164">For SHA384 the buffer size must be 48 bytes.</span></span>
- <span data-ttu-id="c23c4-1165">**crypto_metadata** Pekare till SHA512-kontroll blocket som används i *_nx_crypto_method_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1165">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>
- <span data-ttu-id="c23c4-1166">**crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1166">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c23c4-1167">För SHA512 måste metadata *-storleken sizeof (NX_CRYPTO_SHA512)*</span><span class="sxs-lookup"><span data-stu-id="c23c4-1167">For SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512)*</span></span>
- <span data-ttu-id="c23c4-1168">**packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1168">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1169">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1169">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c23c4-1170">**nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1170">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c23c4-1171">Alla värden som skickas i ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1171">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1172">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1172">Return Values</span></span>

- <span data-ttu-id="c23c4-1173">**NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1173">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA512 operation.</span></span>
- <span data-ttu-id="c23c4-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c23c4-1175">**NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1175">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c23c4-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig SHA512-algoritm anges.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="c23c4-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha512_cleanup"></a><span data-ttu-id="c23c4-1178">_nx_crypto_method_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="c23c4-1178">_nx_crypto_method_sha512_cleanup</span></span>

<span data-ttu-id="c23c4-1179">Rensa kontroll blocket SHA512.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1179">Clean up the SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c23c4-1180">Prototyp</span><span class="sxs-lookup"><span data-stu-id="c23c4-1180">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c23c4-1181">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c23c4-1181">Description</span></span>

<span data-ttu-id="c23c4-1182">Programmet anropar den här funktionen för att rensa SHA512-kontroll blocket när den har bedömt att den här SHA512-sessionen inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1182">Application calls this function to clean up the SHA512 control block after it determines this SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c23c4-1183">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c23c4-1183">Parameters</span></span>

- <span data-ttu-id="c23c4-1184">**crypto_metadata** Pekare till SHA512-kontroll blocket som används i *_nx_crypto_method_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1184">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c23c4-1185">Retur värden</span><span class="sxs-lookup"><span data-stu-id="c23c4-1185">Return Values</span></span>

- <span data-ttu-id="c23c4-1186">**NX_CRYPTO_SUCCESS** (0X00) har rensat SHA512-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1186">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA512 session.</span></span>
- <span data-ttu-id="c23c4-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.</span><span class="sxs-lookup"><span data-stu-id="c23c4-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>