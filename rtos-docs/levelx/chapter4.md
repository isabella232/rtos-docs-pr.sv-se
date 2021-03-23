---
title: 'Kapitel 4 – Azure återställnings tider LevelX NAND-API: er'
description: 'De Azure återställnings tider LevelX-NAND-API: er som är tillgängliga för programmet.'
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827063"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a><span data-ttu-id="09fc7-103">Kapitel 4 – Azure återställnings tider LevelX NAND-API: er</span><span class="sxs-lookup"><span data-stu-id="09fc7-103">Chapter 4 - Azure RTOS LevelX NAND APIs</span></span>

<span data-ttu-id="09fc7-104">De Azure återställnings tider LevelX-NAND-API: erna som är tillgängliga för programmet är:</span><span class="sxs-lookup"><span data-stu-id="09fc7-104">The Azure RTOS LevelX NAND APIs available to the application are:</span></span>

- <span data-ttu-id="09fc7-105">\***lx_nand_flash_close** _: _Close NAND Flash instance \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-105">***lx_nand_flash_close** _: _Close NAND flash instance*</span></span>
- <span data-ttu-id="09fc7-106">\***lx_nand_flash_defragment** _: _Defragment NAND Flash instance \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-106">***lx_nand_flash_defragment** _: _Defragment NAND flash instance*</span></span>
- <span data-ttu-id="09fc7-107">\***lx_nand_flash_extended_cache_enable** _: _Enable/Disable utökad NAND-cache \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-107">***lx_nand_flash_extended_cache_enable** _: _Enable/disable extended NAND cache*</span></span>
- <span data-ttu-id="09fc7-108">\***lx_nand_flash_initialize** _: _Initialize NAND Flash Support \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-108">***lx_nand_flash_initialize** _: _Initialize NAND flash support*</span></span>
- <span data-ttu-id="09fc7-109">\***lx_nand_flash_open** _: _Open NAND Flash instance \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-109">***lx_nand_flash_open** _: _Open NAND flash instance*</span></span>
- <span data-ttu-id="09fc7-110">\***lx_nand_flash_page_ecc_check** _: _Check sida för ECC-fel med korrigering \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-110">***lx_nand_flash_page_ecc_check** _: _Check page for ECC errors with correction*</span></span>
- <span data-ttu-id="09fc7-111">\***lx_nand_flash_page_ecc_compute** _: _Computes ECC för sida \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC for page*</span></span>
- <span data-ttu-id="09fc7-112">\***lx_nand_flash_partial_defragment** _: _Partial defragmentera NAND Flash instance \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-112">***lx_nand_flash_partial_defragment** _: _Partial defragment of NAND flash instance*</span></span>
- <span data-ttu-id="09fc7-113">\***lx_nand_flash_sector_read** _: _Read NAND Flash-sektor \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-113">***lx_nand_flash_sector_read** _: _Read NAND flash sector*</span></span>
- <span data-ttu-id="09fc7-114">\***lx_nand_flash_sector_release** _: _Release NAND Flash-sektor \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-114">***lx_nand_flash_sector_release** _: _Release NAND flash sector*</span></span>
- <span data-ttu-id="09fc7-115">\***lx_nand_flash_sector_write** _: _Write NAND Flash-sektor \*</span><span class="sxs-lookup"><span data-stu-id="09fc7-115">***lx_nand_flash_sector_write** _: _Write NAND flash sector*</span></span>

## <a name="lx_nand_flash_close"></a><span data-ttu-id="09fc7-116">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-116">lx_nand_flash_close</span></span>

<span data-ttu-id="09fc7-117">Stäng NAND Flash instance</span><span class="sxs-lookup"><span data-stu-id="09fc7-117">Close NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-118">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-118">Prototype</span></span>

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="09fc7-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-119">Description</span></span>

<span data-ttu-id="09fc7-120">Den här tjänsten stänger den tidigare öppnade NAND Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-120">This service closes the previously opened NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-121">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-121">Input Parameters</span></span>

- <span data-ttu-id="09fc7-122">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-122">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-123">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-123">Return Values</span></span>

- <span data-ttu-id="09fc7-124">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-124">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-125">**LX_ERROR**: (0x01) Det gick inte att stänga Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-125">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-126">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-126">Allowed From</span></span>

<span data-ttu-id="09fc7-127">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-127">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-128">Example</span></span>

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-129">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-129">See Also</span></span>

- <span data-ttu-id="09fc7-130">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-130">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-131">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-131">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-132">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-132">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-133">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-133">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-134">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-134">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-135">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-135">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-136">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-136">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-137">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-137">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-138">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-138">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-139">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-139">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_defragment"></a><span data-ttu-id="09fc7-140">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-140">lx_nand_flash_defragment</span></span>

<span data-ttu-id="09fc7-141">Defragmentera NAND Flash instance</span><span class="sxs-lookup"><span data-stu-id="09fc7-141">Defragment NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-142">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-142">Prototype</span></span>

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="09fc7-143">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-143">Description</span></span>

<span data-ttu-id="09fc7-144">Den här tjänsten defragmenterar den tidigare öppnade NAND-Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-144">This service defragments the previously opened NAND flash instance.</span></span> <span data-ttu-id="09fc7-145">Defragmenteringen maximerar antalet fria sidor och block.</span><span class="sxs-lookup"><span data-stu-id="09fc7-145">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-146">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-146">Input Parameters</span></span>

- <span data-ttu-id="09fc7-147">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-147">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-148">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-148">Return Values</span></span>

- <span data-ttu-id="09fc7-149">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-149">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-150">**LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-150">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-151">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-151">Allowed From</span></span>

<span data-ttu-id="09fc7-152">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-152">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-153">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-153">Example</span></span>

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-154">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-154">See Also</span></span>

- <span data-ttu-id="09fc7-155">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-155">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-156">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-156">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-157">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-157">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-158">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-158">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-159">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-159">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-160">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-160">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-161">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-161">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-162">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-162">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-163">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-163">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-164">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-164">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_extended_cache_enable"></a><span data-ttu-id="09fc7-165">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-165">lx_nand_flash_extended_cache_enable</span></span>

<span data-ttu-id="09fc7-166">Aktivera/inaktivera utökad NAND-cache</span><span class="sxs-lookup"><span data-stu-id="09fc7-166">Enable/disable extended NAND cache</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-167">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-167">Prototype</span></span>

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="09fc7-168">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-168">Description</span></span>

<span data-ttu-id="09fc7-169">Den här tjänsten implementerar ett cache-skikt i RAM-minnet med det minne som tillhandahålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="09fc7-169">This service implements a cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="09fc7-170">Den totala mängd minne som krävs för fullständig cache-åtgärd kan beräknas på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="09fc7-170">The total amount of memory required for full cache operation can be calculated as follows:</span></span>

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

<span data-ttu-id="09fc7-171">Om det tillhandahållna minnet inte är tillräckligt stort för att rymma fullständig NAND cache, så gör den här rutinen så att Flash-cachen i NAND är så stor som möjligt baserat på det angivna minnet.</span><span class="sxs-lookup"><span data-stu-id="09fc7-171">If the supplied memory is not large enough to accommodate the full NAND cache, this routine will enable as much of the NAND flash cache as possible based on the memory supplied.</span></span>

<span data-ttu-id="09fc7-172">NAND-cachen är inaktive rad om den angivna minnes adressen är NULL.</span><span class="sxs-lookup"><span data-stu-id="09fc7-172">The NAND cache is disabled if the memory address specified is NULL.</span></span> <span data-ttu-id="09fc7-173">Därför kan NAND-cachen användas på ett tillfälligt sätt.</span><span class="sxs-lookup"><span data-stu-id="09fc7-173">Hence, the NAND cache maybe be used in a temporary fashion.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-174">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-174">Input Parameters</span></span>

- <span data-ttu-id="09fc7-175">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-175">**nand_flash**: NAND flash instance pointer.</span></span>  
- <span data-ttu-id="09fc7-176">**minne**: Start adress för cache-minne som är justerat för ulong-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="09fc7-176">**memory**: Starting address for cache memory aligned for ULONG access.</span></span> <span data-ttu-id="09fc7-177">Värdet LX_NULL inaktiverar cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="09fc7-177">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="09fc7-178">**storlek**: storleken i byte för det angivna minnet.</span><span class="sxs-lookup"><span data-stu-id="09fc7-178">**size**: The size in bytes of the memory supplied.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-179">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-179">Return Values</span></span>

- <span data-ttu-id="09fc7-180">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-180">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-181">**LX_ERROR**: (0x01) det finns inte tillräckligt med minne för ett element i NAND-cachen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-181">**LX_ERROR**: (0x01) Not enough memory for one element of the NAND cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-182">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-182">Allowed From</span></span>

<span data-ttu-id="09fc7-183">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-183">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-184">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-184">Example</span></span>

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-185">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-185">See Also</span></span>

- <span data-ttu-id="09fc7-186">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-186">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-187">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-187">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-188">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-188">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-189">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-189">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-190">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-190">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-191">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-191">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-192">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-192">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-193">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-193">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-194">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-194">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-195">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-195">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_initialize"></a><span data-ttu-id="09fc7-196">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-196">lx_nand_flash_initialize</span></span>

<span data-ttu-id="09fc7-197">Initiera stöd för NAND Flash</span><span class="sxs-lookup"><span data-stu-id="09fc7-197">Initialize NAND flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-198">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-198">Prototype</span></span>

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="09fc7-199">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-199">Description</span></span>

<span data-ttu-id="09fc7-200">Den här tjänsten initierar LevelX NAND Flash-stöd.</span><span class="sxs-lookup"><span data-stu-id="09fc7-200">This service initializes LevelX NAND flash support.</span></span> <span data-ttu-id="09fc7-201">Den måste anropas före andra LevelX NAND-API: er.</span><span class="sxs-lookup"><span data-stu-id="09fc7-201">It must be called before any other LevelX NAND APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-202">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-202">Input Parameters</span></span>

- <span data-ttu-id="09fc7-203">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="09fc7-203">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-204">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-204">Return Values</span></span>

- <span data-ttu-id="09fc7-205">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-205">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-206">**LX_ERROR**: (0x01) Det gick inte att initiera stöd för NAND Flash.</span><span class="sxs-lookup"><span data-stu-id="09fc7-206">**LX_ERROR**: (0x01) Error initializing NAND flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-207">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-207">Allowed From</span></span>

<span data-ttu-id="09fc7-208">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="09fc7-208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-209">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-209">Example</span></span>

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-210">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-210">See Also</span></span>

- <span data-ttu-id="09fc7-211">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-211">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-212">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-212">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-213">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-213">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-214">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-214">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-215">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-215">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-216">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-216">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-217">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-217">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-218">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-218">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-219">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-219">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-220">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-220">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_open"></a><span data-ttu-id="09fc7-221">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-221">lx_nand_flash_open</span></span>

<span data-ttu-id="09fc7-222">Öppna NAND Flash instance</span><span class="sxs-lookup"><span data-stu-id="09fc7-222">Open NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-223">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-223">Prototype</span></span>

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a><span data-ttu-id="09fc7-224">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-224">Description</span></span>

<span data-ttu-id="09fc7-225">Den här tjänsten öppnar en NAND Flash-instans med angivet NAND för Flash-kontroll block och driv rutins initiering.</span><span class="sxs-lookup"><span data-stu-id="09fc7-225">This service opens a NAND flash instance with the specified NAND flash control block and driver initialization function.</span></span> <span data-ttu-id="09fc7-226">Observera att driv Rutinens initierings funktion ansvarar för att installera olika funktions pekare för att läsa, skriva och radera block/sidor för den NAND maskin vara som är associerad med NAND Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-226">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks/pages of the NAND hardware associated with this NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-227">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-227">Input Parameters</span></span>

- <span data-ttu-id="09fc7-228">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-228">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="09fc7-229">**namn**: namnet på NAND-Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-229">**name**: Name of NAND flash instance.</span></span>
- <span data-ttu-id="09fc7-230">**nand_driver_initialize**: funktions pekare till NAND för Flash-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-230">**nand_driver_initialize**: Function pointer to NAND flash driver initialization function.</span></span> <span data-ttu-id="09fc7-231">Se kapitel 3 i den här guiden för mer information om NAND för Flash-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-231">Please refer to Chapter 3 of this guide for more details on NAND flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-232">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-232">Return Values</span></span>

- <span data-ttu-id="09fc7-233">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-233">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-234">**LX_ERROR**: (0x01) Det gick inte att öppna NAND Flash instance.</span><span class="sxs-lookup"><span data-stu-id="09fc7-234">**LX_ERROR**: (0x01) Error opening NAND flash instance.</span></span>
- <span data-ttu-id="09fc7-235">**LX_NO_MEMORY**: (0X08) driv rutinen tillhandahöll ingen buffert för att läsa en sida i RAM-minnet.</span><span class="sxs-lookup"><span data-stu-id="09fc7-235">**LX_NO_MEMORY**: (0x08) Driver did not provide buffer for reading one page into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-236">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-236">Allowed From</span></span>

<span data-ttu-id="09fc7-237">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-238">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-238">Example</span></span>

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-239">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-239">See Also</span></span>

- <span data-ttu-id="09fc7-240">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-240">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-241">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-241">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-242">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-242">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-243">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-243">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-244">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-244">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-245">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-245">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-246">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-246">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-247">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-247">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-248">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-248">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-249">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-249">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_check"></a><span data-ttu-id="09fc7-250">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-250">lx_nand_flash_page_ecc_check</span></span>

<span data-ttu-id="09fc7-251">Kontrol lera sidan för ECC-fel med korrigering</span><span class="sxs-lookup"><span data-stu-id="09fc7-251">Check page for ECC errors with correction</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-252">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-252">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="09fc7-253">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-253">Description</span></span>

<span data-ttu-id="09fc7-254">Den här tjänsten verifierar integriteten för den tillhandahållna NAND-bufferten med angiven ECC.</span><span class="sxs-lookup"><span data-stu-id="09fc7-254">This service verifies the integrity of the supplied NAND page buffer with the supplied ECC.</span></span> <span data-ttu-id="09fc7-255">Sid storleken (definieras i NAND Flash instance Pointer) antas vara en multipel av 256-byte och den angivna ECC-koden kan korrigera ett 1-bitars fel i varje 256-byte-del av sidan.</span><span class="sxs-lookup"><span data-stu-id="09fc7-255">Page size (defined in the NAND flash instance pointer) is assumed to be a multiple of 256-bytes and the ECC code supplied is capable of correcting a 1 bit error in each 256-byte portion of the page.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-256">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-256">Input Parameters</span></span>

- <span data-ttu-id="09fc7-257">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-257">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="09fc7-258">**page_buffer**: PEKAREN till NAND Flash Page buffer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-258">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="09fc7-259">**ecc_buffer**: pekar på ECC för NAND Flash Page.</span><span class="sxs-lookup"><span data-stu-id="09fc7-259">**ecc_buffer**: Pointer to ECC for NAND flash page.</span></span> <span data-ttu-id="09fc7-260">Observera att det finns 3 ECC-byte per 256 byte-del av sidan.</span><span class="sxs-lookup"><span data-stu-id="09fc7-260">Note that there are 3 ECC bytes per 256-byte portion of the page.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-261">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-261">Return Values</span></span>

- <span data-ttu-id="09fc7-262">**LX_SUCCESS**: (0X00) NAND-sidan innehåller inga fel.</span><span class="sxs-lookup"><span data-stu-id="09fc7-262">**LX_SUCCESS**: (0x00) NAND page has no errors.</span></span>
- <span data-ttu-id="09fc7-263">**LX_NAND_ERROR_CORRECTED**: (0X06) ett eller flera 1-bitars fel korrigerades på sidan NAND – korrigeringarna finns i kommandobufferten.</span><span class="sxs-lookup"><span data-stu-id="09fc7-263">**LX_NAND_ERROR_CORRECTED**: (0x06) One or more 1-bit errors were corrected in the NAND page—correction(s) are in the page buffer.</span></span>
- <span data-ttu-id="09fc7-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0X07) för många fel som ska korrigeras på NAND-sidan.</span><span class="sxs-lookup"><span data-stu-id="09fc7-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Too many errors to correct on the NAND page.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-265">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-265">Allowed From</span></span>

<span data-ttu-id="09fc7-266">LevelX-drivrutin</span><span class="sxs-lookup"><span data-stu-id="09fc7-266">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-267">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-267">Example</span></span>

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-268">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-268">See Also</span></span>

- <span data-ttu-id="09fc7-269">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-269">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-270">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-270">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-271">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-271">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-272">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-272">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-273">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-273">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-274">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-274">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-275">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-275">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-276">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-276">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-277">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-277">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-278">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-278">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_compute"></a><span data-ttu-id="09fc7-279">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-279">lx_nand_flash_page_ecc_compute</span></span>

<span data-ttu-id="09fc7-280">Compute ECC för sida</span><span class="sxs-lookup"><span data-stu-id="09fc7-280">Compute ECC for page</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-281">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-281">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="09fc7-282">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-282">Description</span></span>

<span data-ttu-id="09fc7-283">Den här tjänsten beräknar ECC för den angivna NAND-kommandobufferten och returnerar ECC i den angivna ECC-bufferten.</span><span class="sxs-lookup"><span data-stu-id="09fc7-283">This service computes the ECC of the supplied NAND page buffer and returns the ECC in the supplied ECC buffer.</span></span> <span data-ttu-id="09fc7-284">Sid storleken antas vara en multipel av 256 byte (definieras i NAND Flash instance Pointer).</span><span class="sxs-lookup"><span data-stu-id="09fc7-284">Page size is assume to be a multiple of 256-bytes (defined in the NAND flash instance pointer).</span></span> <span data-ttu-id="09fc7-285">ECC-koden används för att verifiera sidans integritet när den läses vid ett senare tillfälle.</span><span class="sxs-lookup"><span data-stu-id="09fc7-285">The ECC code is used to verify the integrity of the page when it is read at a later time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-286">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-286">Input Parameters</span></span>

- <span data-ttu-id="09fc7-287">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-287">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="09fc7-288">**page_buffer**: PEKAREN till NAND Flash Page buffer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-288">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="09fc7-289">**ecc_buffer**: pekare till destination för ECC på Flash-sidan NAND.</span><span class="sxs-lookup"><span data-stu-id="09fc7-289">**ecc_buffer**: Pointer to destination for ECC of the NAND flash page.</span></span> <span data-ttu-id="09fc7-290">Observera att måste vara 3 byte ECC-lagring per 256 byte-del av sidan.</span><span class="sxs-lookup"><span data-stu-id="09fc7-290">Note that must be 3 bytes of ECC storage per 256-byte portion of the page.</span></span> <span data-ttu-id="09fc7-291">Till exempel kräver en 2048 byte-sida 24 byte för ECC.</span><span class="sxs-lookup"><span data-stu-id="09fc7-291">For example, a 2048 byte page would require 24 bytes for the ECC.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-292">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-292">Return Values</span></span>

- <span data-ttu-id="09fc7-293">**LX_SUCCESS**: (0X00) ECC har beräknats.</span><span class="sxs-lookup"><span data-stu-id="09fc7-293">**LX_SUCCESS**: (0x00) ECC successfully calculated.</span></span>
- <span data-ttu-id="09fc7-294">**LX_ERROR**: (0x01) Det gick inte att beräkna ECC.</span><span class="sxs-lookup"><span data-stu-id="09fc7-294">**LX_ERROR**: (0x01) Error calculating ECC.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-295">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-295">Allowed From</span></span>

<span data-ttu-id="09fc7-296">LevelX-drivrutin</span><span class="sxs-lookup"><span data-stu-id="09fc7-296">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-297">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-297">Example</span></span>

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-298">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-298">See Also</span></span>

- <span data-ttu-id="09fc7-299">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-299">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-300">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-300">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-301">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-301">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-302">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-302">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-303">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-303">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-304">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-304">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-305">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-305">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-306">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-306">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-307">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-307">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-308">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-308">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_partial_defragment"></a><span data-ttu-id="09fc7-309">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-309">lx_nand_flash_partial_defragment</span></span>

<span data-ttu-id="09fc7-310">Partiell defragmentering av NAND Flash instance</span><span class="sxs-lookup"><span data-stu-id="09fc7-310">Partial defragment of NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-311">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-311">Prototype</span></span>

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="09fc7-312">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-312">Description</span></span>

<span data-ttu-id="09fc7-313">Den här tjänsten defragmenterar den tidigare öppnade NAND Flash-instansen upp till det maximala antalet block som anges.</span><span class="sxs-lookup"><span data-stu-id="09fc7-313">This service defragments the previously opened NAND flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="09fc7-314">Defragmenteringen maximerar antalet fria sidor och block.</span><span class="sxs-lookup"><span data-stu-id="09fc7-314">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-315">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-315">Input Parameters</span></span>

- <span data-ttu-id="09fc7-316">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-316">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="09fc7-317">**max_blocks**: maximalt antal block.</span><span class="sxs-lookup"><span data-stu-id="09fc7-317">**max_blocks**: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-318">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-318">Return Values</span></span>

- <span data-ttu-id="09fc7-319">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-319">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-320">**LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-320">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-321">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-321">Allowed From</span></span>

<span data-ttu-id="09fc7-322">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-322">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-323">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-323">Example</span></span>

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-324">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-324">See Also</span></span>

- <span data-ttu-id="09fc7-325">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-325">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-326">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-326">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-327">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-327">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-328">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-328">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-329">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-329">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-330">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-330">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-331">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-331">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-332">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-332">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-333">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-333">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-334">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-334">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_read"></a><span data-ttu-id="09fc7-335">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-335">lx_nand_flash_sector_read</span></span>

<span data-ttu-id="09fc7-336">Läs NAND-Flash-sektor</span><span class="sxs-lookup"><span data-stu-id="09fc7-336">Read NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-337">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-337">Prototype</span></span>

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="09fc7-338">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-338">Description</span></span>

<span data-ttu-id="09fc7-339">Den här tjänsten läser den logiska sektorn från NAND Flash-instansen och returnerar innehållet i den angivna bufferten om det lyckas.</span><span class="sxs-lookup"><span data-stu-id="09fc7-339">This service reads the logical sector from the NAND flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="09fc7-340">Observera att NAND sektor storlek alltid är sid storleken för den underliggande NAND-maskinvaran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-340">Note that NAND sector size is always the page size of the underlying NAND hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-341">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-341">Input Parameters</span></span>

- <span data-ttu-id="09fc7-342">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-342">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="09fc7-343">**logical_sector**: logisk sektor som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="09fc7-343">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="09fc7-344">**buffert**: pekare till målet för innehållet i den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="09fc7-344">**buffer**: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="09fc7-345">Observera att bufferten antas vara storleken på storleken på NAND Flash-sidan och justeras för ULONG-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="09fc7-345">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-346">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-346">Return Values</span></span>

- <span data-ttu-id="09fc7-347">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-347">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-348">**LX_ERROR**: (0x01) Det gick inte att läsa NAND Flash-sektor.</span><span class="sxs-lookup"><span data-stu-id="09fc7-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-349">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-349">Allowed From</span></span>

<span data-ttu-id="09fc7-350">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-351">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-351">Example</span></span>

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-352">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-352">See Also</span></span>

- <span data-ttu-id="09fc7-353">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-353">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-354">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-354">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-355">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-355">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-356">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-356">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-357">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-357">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-358">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-358">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-359">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-359">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-360">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-360">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-361">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-361">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="09fc7-362">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-362">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_release"></a><span data-ttu-id="09fc7-363">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-363">lx_nand_flash_sector_release</span></span>

<span data-ttu-id="09fc7-364">Version NAND Flash sektor</span><span class="sxs-lookup"><span data-stu-id="09fc7-364">Release NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-365">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-365">Prototype</span></span>

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="09fc7-366">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-366">Description</span></span>

<span data-ttu-id="09fc7-367">Den här tjänsten släpper den logiska sektor mappningen i NAND Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-367">This service releases the logical sector mapping in the NAND flash instance.</span></span> <span data-ttu-id="09fc7-368">Att släppa en logisk sektor när den inte används gör att LevelX slitaget är mer effektivt.</span><span class="sxs-lookup"><span data-stu-id="09fc7-368">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-369">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-369">Input Parameters</span></span>

- <span data-ttu-id="09fc7-370">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-370">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="09fc7-371">**logical_sector**: logisk sektor som ska frisläppas.</span><span class="sxs-lookup"><span data-stu-id="09fc7-371">**logical_sector**: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-372">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-372">Return Values</span></span>

- <span data-ttu-id="09fc7-373">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-373">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-374">**LX_ERROR**: (0X01) fel NAND Flash sektor Write.</span><span class="sxs-lookup"><span data-stu-id="09fc7-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-375">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-375">Allowed From</span></span>

<span data-ttu-id="09fc7-376">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-376">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-377">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-377">Example</span></span>

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-378">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-378">See Also</span></span>

- <span data-ttu-id="09fc7-379">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-379">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-380">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-380">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-381">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-381">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-382">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-382">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-383">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-383">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-384">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-384">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-385">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-385">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-386">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-386">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-387">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-387">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-388">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-388">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_write"></a><span data-ttu-id="09fc7-389">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="09fc7-389">lx_nand_flash_sector_write</span></span>

<span data-ttu-id="09fc7-390">Skriv NAND Flash-sektor</span><span class="sxs-lookup"><span data-stu-id="09fc7-390">Write NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="09fc7-391">Prototyp</span><span class="sxs-lookup"><span data-stu-id="09fc7-391">Prototype</span></span>

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="09fc7-392">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="09fc7-392">Description</span></span>

<span data-ttu-id="09fc7-393">Den här tjänsten skriver den angivna logiska sektorn i NAND-Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-393">This service writes the specified logical sector in the NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="09fc7-394">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="09fc7-394">Input Parameters</span></span>

- <span data-ttu-id="09fc7-395">**nand_flash**: NAND Flash instance Pointer.</span><span class="sxs-lookup"><span data-stu-id="09fc7-395">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="09fc7-396">**logical_sector**: logisk sektor som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="09fc7-396">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="09fc7-397">**Buffer**: pekar mot innehållet i den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="09fc7-397">**buffer**: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="09fc7-398">Observera att bufferten antas vara storleken på storleken på NAND Flash-sidan och justeras för ULONG-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="09fc7-398">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="09fc7-399">Retur värden</span><span class="sxs-lookup"><span data-stu-id="09fc7-399">Return Values</span></span>

- <span data-ttu-id="09fc7-400">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="09fc7-400">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="09fc7-401">**LX_NO_SECTORS**: (protokollnumret 0x02) det finns inga fler kostnads fria sektorer att utföra skrivningen.</span><span class="sxs-lookup"><span data-stu-id="09fc7-401">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="09fc7-402">**LX_ERROR**: (0x01) Det gick inte att frigöra NAND Flash-sektor.</span><span class="sxs-lookup"><span data-stu-id="09fc7-402">**LX_ERROR**: (0x01) Error releasing NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="09fc7-403">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="09fc7-403">Allowed From</span></span>

<span data-ttu-id="09fc7-404">Konversation</span><span class="sxs-lookup"><span data-stu-id="09fc7-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="09fc7-405">Exempel</span><span class="sxs-lookup"><span data-stu-id="09fc7-405">Example</span></span>

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="09fc7-406">Se även</span><span class="sxs-lookup"><span data-stu-id="09fc7-406">See Also</span></span>

- <span data-ttu-id="09fc7-407">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="09fc7-407">lx_nand_flash_close</span></span>
- <span data-ttu-id="09fc7-408">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-408">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="09fc7-409">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="09fc7-409">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="09fc7-410">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="09fc7-410">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="09fc7-411">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="09fc7-411">lx_nand_flash_open</span></span>
- <span data-ttu-id="09fc7-412">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="09fc7-412">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="09fc7-413">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="09fc7-413">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="09fc7-414">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="09fc7-414">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="09fc7-415">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="09fc7-415">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="09fc7-416">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="09fc7-416">lx_nand_flash_sector_release</span></span>
