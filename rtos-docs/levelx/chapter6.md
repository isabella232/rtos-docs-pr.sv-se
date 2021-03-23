---
title: 'Kapitel 6 – Azure återställnings tider-LevelX eller API: er'
description: 'Azure återställnings tider-LevelX eller API: er som är tillgängliga för programmet.'
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827051"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a><span data-ttu-id="f0214-103">Kapitel 6 – Azure återställnings tider-LevelX eller API: er</span><span class="sxs-lookup"><span data-stu-id="f0214-103">Chapter 6 - Azure RTOS LevelX NOR APIs</span></span>

<span data-ttu-id="f0214-104">Azure återställnings tider-LevelX eller API-funktionerna som är tillgängliga för programmet är följande.</span><span class="sxs-lookup"><span data-stu-id="f0214-104">The Azure RTOS LevelX NOR API functions available to the application are as follows.</span></span>

- <span data-ttu-id="f0214-105">\***lx_nor_flash_close** _: _Close eller Flash-instans \*</span><span class="sxs-lookup"><span data-stu-id="f0214-105">***lx_nor_flash_close** _: _Close NOR flash instance*</span></span>
- <span data-ttu-id="f0214-106">\***lx_nor_flash_defragment** _: _Defragment eller Flash-instans \*</span><span class="sxs-lookup"><span data-stu-id="f0214-106">***lx_nor_flash_defragment** _: _Defragment NOR flash instance*</span></span>
- <span data-ttu-id="f0214-107">\***lx_nor_flash_extended_cache_enable** _: _Enable/Disable utökad eller cache \*</span><span class="sxs-lookup"><span data-stu-id="f0214-107">***lx_nor_flash_extended_cache_enable** _: _Enable/disable extended NOR cache*</span></span>
- <span data-ttu-id="f0214-108">\***lx_nor_flash_initialize** _: _INITIALIZE-eller Flash-Support \*</span><span class="sxs-lookup"><span data-stu-id="f0214-108">***lx_nor_flash_initialize** _: _Initialize NOR flash support*</span></span>
- <span data-ttu-id="f0214-109">\***lx_nor_flash_open** _: _Open eller Flash-instans \*</span><span class="sxs-lookup"><span data-stu-id="f0214-109">***lx_nor_flash_open** _: _Open NOR flash instance*</span></span>
- <span data-ttu-id="f0214-110">\***lx_nor_flash_partial_defragment** _: _Partial defragmentera eller Flash-instansen \*</span><span class="sxs-lookup"><span data-stu-id="f0214-110">***lx_nor_flash_partial_defragment** _: _Partial defragment of NOR flash instance*</span></span>
- <span data-ttu-id="f0214-111">\***lx_nor_flash_sector_read** _: _Read eller Flash-sektor \*</span><span class="sxs-lookup"><span data-stu-id="f0214-111">***lx_nor_flash_sector_read** _: _Read NOR flash sector*</span></span>
- <span data-ttu-id="f0214-112">\***lx_nor_flash_sector_release** _: _Release eller Flash-sektor \*</span><span class="sxs-lookup"><span data-stu-id="f0214-112">***lx_nor_flash_sector_release** _: _Release NOR flash sector*</span></span>
- <span data-ttu-id="f0214-113">\***lx_nor_flash_sector_write** _: _Write eller Flash-sektor \*</span><span class="sxs-lookup"><span data-stu-id="f0214-113">***lx_nor_flash_sector_write** _: _Write NOR flash sector*</span></span>

## <a name="lx_nor_flash_close"></a><span data-ttu-id="f0214-114">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-114">lx_nor_flash_close</span></span>

<span data-ttu-id="f0214-115">Stäng eller Flash-instans</span><span class="sxs-lookup"><span data-stu-id="f0214-115">Close NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-116">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-116">Prototype</span></span>

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="f0214-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-117">Description</span></span>

<span data-ttu-id="f0214-118">Den här tjänsten stänger den tidigare öppnade eller Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-118">This service closes the previously opened NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-119">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-119">Input Parameters</span></span>

- <span data-ttu-id="f0214-120">*nor_flash*: eller Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-120">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-121">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-121">Return Values</span></span>

- <span data-ttu-id="f0214-122">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-122">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-123">**LX_ERROR**: (0x01) Det gick inte att stänga Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-123">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-124">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-124">Allowed From</span></span>

<span data-ttu-id="f0214-125">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-125">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-126">Example</span></span>

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-127">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-127">See Also</span></span>

- <span data-ttu-id="f0214-128">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-128">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-129">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-129">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-130">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-130">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-131">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-131">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-132">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-132">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-133">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-133">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-134">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-134">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="f0214-135">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-135">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_defragment"></a><span data-ttu-id="f0214-136">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-136">lx_nor_flash_defragment</span></span>

<span data-ttu-id="f0214-137">Defragmentera eller Flash-instans</span><span class="sxs-lookup"><span data-stu-id="f0214-137">Defragment NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-138">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-138">Prototype</span></span>

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="f0214-139">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-139">Description</span></span>

<span data-ttu-id="f0214-140">Den här tjänsten defragmenterar den tidigare öppnade eller Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-140">This service defragments the previously opened NOR flash instance.</span></span> <span data-ttu-id="f0214-141">Defragmenteringen maximerar antalet kostnads fria sektorer och block.</span><span class="sxs-lookup"><span data-stu-id="f0214-141">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-142">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-142">Input Parameters</span></span>

- <span data-ttu-id="f0214-143">*nor_flash*: eller Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-143">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-144">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-144">Return Values</span></span>

- <span data-ttu-id="f0214-145">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-145">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-146">**LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-146">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-147">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-147">Allowed From</span></span>

<span data-ttu-id="f0214-148">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-149">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-149">Example</span></span>

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-150">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-150">See Also</span></span>

- <span data-ttu-id="f0214-151">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-151">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-152">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-152">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-153">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-153">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-154">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-154">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-155">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-155">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-156">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-156">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-157">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-157">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="f0214-158">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-158">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_extended_cache_enable"></a><span data-ttu-id="f0214-159">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-159">lx_nor_flash_extended_cache_enable</span></span>

<span data-ttu-id="f0214-160">Aktivera/inaktivera utökad eller cachelagring</span><span class="sxs-lookup"><span data-stu-id="f0214-160">Enable/disable extended NOR cache</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-161">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-161">Prototype</span></span>

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="f0214-162">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-162">Description</span></span>

<span data-ttu-id="f0214-163">Den här tjänsten implementerar ett-eller sektor cache-skikt i RAM-minnet med det minne som tillhandahålls av programmet.</span><span class="sxs-lookup"><span data-stu-id="f0214-163">This service implements a NOR sector cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="f0214-164">Varje 512 byte minne som tillhandahålls översätts till en eller sektor som kan cachelagras.</span><span class="sxs-lookup"><span data-stu-id="f0214-164">Each 512 bytes of memory supplied translates to one NOR sector that can be cached.</span></span> <span data-ttu-id="f0214-165">De cachelagrade sektorerna är de som innehåller block kontroll information, t. ex., antal rader, kostnads fri sektor karta och information om sektor mappning.</span><span class="sxs-lookup"><span data-stu-id="f0214-165">The sectors cached are those that contain the block control information, e.g., erase count, free sector map, and sector mapping information.</span></span> <span data-ttu-id="f0214-166">Data sektorer lagras inte i det här cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="f0214-166">Data sectors are not stored in this cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-167">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-167">Input Parameters</span></span>

- <span data-ttu-id="f0214-168">**nor_flash**: eller Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-168">**nor_flash**: NOR flash instance pointer.</span></span>  
- <span data-ttu-id="f0214-169">**minne**: Start adress för cache-minne, justerat för ulong-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f0214-169">**memory**: Starting address for cache memory, aligned for ULONG access.</span></span> <span data-ttu-id="f0214-170">Värdet LX_NULL inaktiverar cacheminnet.</span><span class="sxs-lookup"><span data-stu-id="f0214-170">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="f0214-171">**storlek**: storleken i byte för det angivna minnet (bör vara flera av 512 byte).</span><span class="sxs-lookup"><span data-stu-id="f0214-171">**size**: The size in bytes of the memory supplied (should be multiple of 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-172">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-172">Return Values</span></span>

- <span data-ttu-id="f0214-173">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-173">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-174">**LX_ERROR**: (0x01) det finns inte tillräckligt med minne för en eller sektor.</span><span class="sxs-lookup"><span data-stu-id="f0214-174">**LX_ERROR**: (0x01) Not enough memory for one NOR sector.</span></span>
- <span data-ttu-id="f0214-175">**LX_DISABLED**: (0X09) eller utökad cache inaktiverat av konfigurations alternativ.</span><span class="sxs-lookup"><span data-stu-id="f0214-175">**LX_DISABLED**: (0x09) NOR extended cache disabled by configuration option.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-176">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-176">Allowed From</span></span>

<span data-ttu-id="f0214-177">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-178">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-178">Example</span></span>

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-179">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-179">See Also</span></span>

- <span data-ttu-id="f0214-180">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-180">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-181">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-181">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-182">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-182">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-183">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-183">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-184">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-184">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-185">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-185">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-186">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-186">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="f0214-187">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-187">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_initialize"></a><span data-ttu-id="f0214-188">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-188">lx_nor_flash_initialize</span></span>

<span data-ttu-id="f0214-189">Initiera eller stöd för Flash</span><span class="sxs-lookup"><span data-stu-id="f0214-189">Initialize NOR flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-190">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-190">Prototype</span></span>

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="f0214-191">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-191">Description</span></span>

<span data-ttu-id="f0214-192">Den här tjänsten initierar LevelX eller Flash-stöd.</span><span class="sxs-lookup"><span data-stu-id="f0214-192">This service initializes LevelX NOR flash support.</span></span> <span data-ttu-id="f0214-193">Den måste anropas före andra LevelX eller API: er.</span><span class="sxs-lookup"><span data-stu-id="f0214-193">It must be called before any other LevelX NOR APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-194">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-194">Input Parameters</span></span>

- <span data-ttu-id="f0214-195">**Ingen**</span><span class="sxs-lookup"><span data-stu-id="f0214-195">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-196">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-196">Return Values</span></span>

- <span data-ttu-id="f0214-197">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-197">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-198">**LX_ERROR**: (0x01) Det gick inte att initiera eller Flash-stöd.</span><span class="sxs-lookup"><span data-stu-id="f0214-198">**LX_ERROR**: (0x01) Error initializing NOR flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-199">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-199">Allowed From</span></span>

<span data-ttu-id="f0214-200">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="f0214-200">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-201">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-201">Example</span></span>

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-202">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-202">See Also</span></span>

- <span data-ttu-id="f0214-203">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-203">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-204">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-204">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-205">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-205">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-206">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-206">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-207">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-207">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-208">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-208">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-209">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-209">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="f0214-210">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-210">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_open"></a><span data-ttu-id="f0214-211">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-211">lx_nor_flash_open</span></span>

<span data-ttu-id="f0214-212">Öppna eller Flash-instans</span><span class="sxs-lookup"><span data-stu-id="f0214-212">Open NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-213">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-213">Prototype</span></span>

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a><span data-ttu-id="f0214-214">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-214">Description</span></span>

<span data-ttu-id="f0214-215">Den här tjänsten öppnar en eller Flash-instans med angivet eller Flash-kontroll block och driv rutins initierings funktionen.</span><span class="sxs-lookup"><span data-stu-id="f0214-215">This service opens a NOR flash instance with the specified NOR flash control block and driver initialization function.</span></span> <span data-ttu-id="f0214-216">Observera att driv Rutinens initierings funktion ansvarar för att installera olika funktions pekare för att läsa, skriva och radera block av den eller maskin vara som är associerad med den här eller Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-216">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks of the NOR hardware associated with this NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-217">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-217">Input Parameters</span></span>

- <span data-ttu-id="f0214-218">*nor_flash*: eller Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-218">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="f0214-219">*namn*: namnet på eller Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-219">*name*: Name of NOR flash instance.</span></span>
- <span data-ttu-id="f0214-220">*nor_driver_initialize*: funktions pekare till eller Flash driver initierings funktion.</span><span class="sxs-lookup"><span data-stu-id="f0214-220">*nor_driver_initialize*: Function pointer to NOR flash driver Initialization function.</span></span> <span data-ttu-id="f0214-221">Se kapitel 5 i den här hand boken om du vill ha mer information om eller driv rutins ansvar för Flash.</span><span class="sxs-lookup"><span data-stu-id="f0214-221">Please refer to Chapter 5 of this guide for more details on NOR flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-222">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-222">Return Values</span></span>

- <span data-ttu-id="f0214-223">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-223">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-224">**LX_ERROR**: (0x01) Det gick inte att öppna eller Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-224">**LX_ERROR**: (0x01) Error opening NOR flash instance.</span></span>
- <span data-ttu-id="f0214-225">**LX_NO_MEMORY**: (0X08) driv rutinen tillhandahöll ingen buffert för att läsa någon sektor i RAM-minnet.</span><span class="sxs-lookup"><span data-stu-id="f0214-225">**LX_NO_MEMORY**:  (0x08) Driver did not provide buffer for reading none sector into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-226">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-226">Allowed From</span></span>

<span data-ttu-id="f0214-227">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-227">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-228">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-228">Example</span></span>

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-229">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-229">See Also</span></span>

- <span data-ttu-id="f0214-230">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-230">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-231">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-231">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-232">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-232">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-233">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-233">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-234">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-234">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-235">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-235">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-236">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-236">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="f0214-237">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-237">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_partial_defragment"></a><span data-ttu-id="f0214-238">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-238">lx_nor_flash_partial_defragment</span></span>

<span data-ttu-id="f0214-239">Partiell defragmentering av eller Flash-instans</span><span class="sxs-lookup"><span data-stu-id="f0214-239">Partial defragment of NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-240">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-240">Prototype</span></span>

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="f0214-241">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-241">Description</span></span>

<span data-ttu-id="f0214-242">Den här tjänsten defragmenterar den tidigare öppnade eller Flash-instansen upp till det maximala antalet block som anges.</span><span class="sxs-lookup"><span data-stu-id="f0214-242">This service defragments the previously opened NOR flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="f0214-243">Defragmenteringen maximerar antalet kostnads fria sektorer och block.</span><span class="sxs-lookup"><span data-stu-id="f0214-243">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-244">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-244">Input Parameters</span></span>

- <span data-ttu-id="f0214-245">*nor_flash*: eller Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-245">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="f0214-246">*max_blocks*: maximalt antal block.</span><span class="sxs-lookup"><span data-stu-id="f0214-246">*max_blocks*: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-247">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-247">Return Values</span></span>

- <span data-ttu-id="f0214-248">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-248">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-249">**LX_ERROR**: (0x01) Det gick inte att defragmentera Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-249">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-250">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-250">Allowed From</span></span>

<span data-ttu-id="f0214-251">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-252">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-252">Example</span></span>

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-253">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-253">See Also</span></span>

- <span data-ttu-id="f0214-254">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-254">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-255">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-255">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-256">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-256">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-257">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-257">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-258">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-258">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-259">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-259">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-260">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-260">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="f0214-261">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-261">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_read"></a><span data-ttu-id="f0214-262">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-262">lx_nor_flash_sector_read</span></span>

<span data-ttu-id="f0214-263">Läs eller Flash-sektor</span><span class="sxs-lookup"><span data-stu-id="f0214-263">Read NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-264">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-264">Prototype</span></span>

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="f0214-265">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-265">Description</span></span>

<span data-ttu-id="f0214-266">Den här tjänsten läser den logiska sektorn från eller Flash-instansen och returnerar innehållet i den angivna bufferten om det lyckas.</span><span class="sxs-lookup"><span data-stu-id="f0214-266">This service reads the logical sector from the NOR flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="f0214-267">Observera att eller sektor storlek alltid är 512 byte.</span><span class="sxs-lookup"><span data-stu-id="f0214-267">Note that NOR sector size is always 512 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-268">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-268">Input Parameters</span></span>

- <span data-ttu-id="f0214-269">*nor_flash* ELLER Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-269">*nor_flash* NOR flash instance pointer.</span></span>
- <span data-ttu-id="f0214-270">*logical_sector*: logisk sektor som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="f0214-270">*logical_sector*: Logical sector to read.</span></span>
- <span data-ttu-id="f0214-271">*buffert*: pekare till målet för innehållet i den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="f0214-271">*buffer*: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="f0214-272">Observera att bufferten antas vara 512 byte och justerad för ULONG-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f0214-272">Note that the buffer is assumed to be 512 bytes and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-273">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-273">Return Values</span></span>

- <span data-ttu-id="f0214-274">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-274">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-275">**LX_ERROR**: (0x01) Det gick inte att läsa eller Flash-sektorn.</span><span class="sxs-lookup"><span data-stu-id="f0214-275">**LX_ERROR**: (0x01) Error reading NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-276">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-276">Allowed From</span></span>

<span data-ttu-id="f0214-277">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-278">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-278">Example</span></span>

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-279">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-279">See Also</span></span>

- <span data-ttu-id="f0214-280">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-280">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-281">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-281">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-282">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-282">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-283">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-283">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-284">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-284">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-285">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-285">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-286">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-286">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="f0214-287">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-287">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_release"></a><span data-ttu-id="f0214-288">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-288">lx_nor_flash_sector_release</span></span>

<span data-ttu-id="f0214-289">Utgåva eller Flash-sektor</span><span class="sxs-lookup"><span data-stu-id="f0214-289">Release NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-290">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-290">Prototype</span></span>

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="f0214-291">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-291">Description</span></span>

<span data-ttu-id="f0214-292">Den här tjänsten släpper den logiska sektor mappningen i eller Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-292">This service releases the logical sector mapping in the NOR flash instance.</span></span> <span data-ttu-id="f0214-293">Att släppa en logisk sektor när den inte används gör att LevelX slitaget är mer effektivt.</span><span class="sxs-lookup"><span data-stu-id="f0214-293">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-294">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-294">Input Parameters</span></span>

- <span data-ttu-id="f0214-295">*nor_flash*: eller Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-295">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="f0214-296">*logical_sector*: logisk sektor som ska frisläppas.</span><span class="sxs-lookup"><span data-stu-id="f0214-296">*logical_sector*: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-297">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-297">Return Values</span></span>

- <span data-ttu-id="f0214-298">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-298">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-299">**LX_ERROR**: (0X01) fel eller Flash-sektor skrivning.</span><span class="sxs-lookup"><span data-stu-id="f0214-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-300">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-300">Allowed From</span></span>

<span data-ttu-id="f0214-301">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-302">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-302">Example</span></span>

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="f0214-303">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-303">See Also</span></span>

- <span data-ttu-id="f0214-304">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-304">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-305">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-305">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-306">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-306">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-307">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-307">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-308">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-308">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-309">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-309">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-310">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-310">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-311">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-311">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_write"></a><span data-ttu-id="f0214-312">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="f0214-312">lx_nor_flash_sector_write</span></span>

<span data-ttu-id="f0214-313">Skriv-eller Flash-sektor</span><span class="sxs-lookup"><span data-stu-id="f0214-313">Write NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="f0214-314">Prototyp</span><span class="sxs-lookup"><span data-stu-id="f0214-314">Prototype</span></span>

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="f0214-315">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0214-315">Description</span></span>

<span data-ttu-id="f0214-316">Den här tjänsten skriver den angivna logiska sektorn i eller Flash-instansen.</span><span class="sxs-lookup"><span data-stu-id="f0214-316">This service writes the specified logical sector in the NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f0214-317">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="f0214-317">Input Parameters</span></span>

- <span data-ttu-id="f0214-318">*nor_flash*: eller Flash instance-pekare.</span><span class="sxs-lookup"><span data-stu-id="f0214-318">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="f0214-319">*logical_sector*: logisk sektor som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="f0214-319">*logical_sector*: Logical sector to write.</span></span>
- <span data-ttu-id="f0214-320">*Buffer*: pekar mot innehållet i den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="f0214-320">*buffer*: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="f0214-321">Observera att bufferten antas vara 512 byte justerad för ULONG-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="f0214-321">Note that the buffer is assumed to be 512 bytes aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="f0214-322">Retur värden</span><span class="sxs-lookup"><span data-stu-id="f0214-322">Return Values</span></span>

- <span data-ttu-id="f0214-323">**LX_SUCCESS**: (0X00) lyckad begäran.</span><span class="sxs-lookup"><span data-stu-id="f0214-323">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="f0214-324">**LX_NO_SECTORS**: (protokollnumret 0x02) det finns inga fler kostnads fria sektorer att utföra skrivningen.</span><span class="sxs-lookup"><span data-stu-id="f0214-324">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="f0214-325">**LX_ERROR**: (0X01) fel vid fri släppning eller Flash-sektor.</span><span class="sxs-lookup"><span data-stu-id="f0214-325">**LX_ERROR**: (0x01) Error releasing NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f0214-326">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="f0214-326">Allowed From</span></span>

<span data-ttu-id="f0214-327">Konversation</span><span class="sxs-lookup"><span data-stu-id="f0214-327">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f0214-328">Exempel</span><span class="sxs-lookup"><span data-stu-id="f0214-328">Example</span></span>

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="f0214-329">Se även</span><span class="sxs-lookup"><span data-stu-id="f0214-329">See Also</span></span>

- <span data-ttu-id="f0214-330">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="f0214-330">lx_nor_flash_close</span></span>
- <span data-ttu-id="f0214-331">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-331">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="f0214-332">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="f0214-332">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="f0214-333">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="f0214-333">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="f0214-334">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="f0214-334">lx_nor_flash_open</span></span>
- <span data-ttu-id="f0214-335">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="f0214-335">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="f0214-336">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="f0214-336">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="f0214-337">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="f0214-337">lx_nor_flash_sector_release</span></span>
