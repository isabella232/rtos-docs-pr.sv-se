---
title: Kapitel 4 – Beskrivning av Azure RTOS FileX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS FileX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 948adff65a080649db0870e35bc75ee774775cb7
ms.sourcegitcommit: 4cbe92b337e82124bb5a86d319b787eb05b4ea76
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/27/2021
ms.locfileid: "108067020"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="fd8ab-103">Kapitel 4 – Beskrivning av Azure RTOS FileX-tjänster</span><span class="sxs-lookup"><span data-stu-id="fd8ab-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="fd8ab-104">Det här kapitlet innehåller en beskrivning av alla Azure RTOS FileX-tjänster i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="fd8ab-105">Tjänstnamn är utformade så att alla liknande tjänster grupperas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="fd8ab-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="fd8ab-107">Läser katalogattribut</span><span class="sxs-lookup"><span data-stu-id="fd8ab-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="fd8ab-109">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-109">Description</span></span>

<span data-ttu-id="fd8ab-110">Den här tjänsten läser katalogens attribut från det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-111">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-111">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-112">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-113">**directory_name:** Pekare till namnet på den begärda katalogen (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="fd8ab-114">**attribut** _ptr: Pekare till målet för katalogens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="fd8ab-115">Katalogattributen returneras i ett bit-map-format med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="fd8ab-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="fd8ab-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="fd8ab-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="fd8ab-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="fd8ab-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="fd8ab-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-122">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-122">Return Values</span></span>

- <span data-ttu-id="fd8ab-123">**FX_SUCCESS** (0x00) Lyckade katalogattribut lästa</span><span class="sxs-lookup"><span data-stu-id="fd8ab-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="fd8ab-124">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-125">**FX _NOT FOUND** (0x04) Den angivna katalogen hittades inte på mediet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="fd8ab-126">**FX_NOT_DIRECTORY post** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="fd8ab-127">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="fd8ab-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-128">**FX_FILE_CORRUPT** 0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-129">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-130">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-131">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-132">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="fd8ab-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="fd8ab-133">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="fd8ab-134">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-135">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-135">Allowed From</span></span>

<span data-ttu-id="fd8ab-136">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-138">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-138">See Also</span></span>

- <span data-ttu-id="fd8ab-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-140">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-141">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-142">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-143">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-146">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-152">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-155">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="fd8ab-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="fd8ab-160">Anger katalogattribut</span><span class="sxs-lookup"><span data-stu-id="fd8ab-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-161">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="fd8ab-162">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-162">Description</span></span>

<span data-ttu-id="fd8ab-163">Den här tjänsten anger katalogens attribut till de som anges av anroparen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-164">*Det här programmet kan bara ändra en delmängd av katalogens attribut med den här tjänsten. Om du försöker ange ytterligare attribut resulterar det i ett fel.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-165">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-165">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-166">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-167">**directory_name:** Pekare till namnet på den begärda katalogen (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="fd8ab-168">**attribut:** De nya attributen i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="fd8ab-169">Giltiga katalogattribut definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="fd8ab-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="fd8ab-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="fd8ab-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="fd8ab-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-174">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-174">Return Values</span></span>

- <span data-ttu-id="fd8ab-175">**FX_SUCCESS** (0x00) Lyckad katalogattributuppsättning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="fd8ab-176">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-177">**FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="fd8ab-178">**FX_NOT_DIRECTORY post** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="fd8ab-179">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="fd8ab-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-180">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat</span><span class="sxs-lookup"><span data-stu-id="fd8ab-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="fd8ab-181">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-182">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-183">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-184">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-185">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="fd8ab-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="fd8ab-186">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="fd8ab-187">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="fd8ab-188">**FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="fd8ab-189">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-190">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-190">Allowed From</span></span>

<span data-ttu-id="fd8ab-191">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-192">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-193">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-193">See Also</span></span>

- <span data-ttu-id="fd8ab-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-195">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-196">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-197">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-198">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-201">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-207">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-210">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="fd8ab-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-214">fx_directory_create</span></span>

<span data-ttu-id="fd8ab-215">Skapar underkatalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-216">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-217">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-217">Description</span></span>

<span data-ttu-id="fd8ab-218">Den här tjänsten skapar en underkatalog i den aktuella standardkatalogen eller i den sökväg som anges i katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="fd8ab-219">Till skillnad från rotkatalogen har underkatalogerna ingen gräns för hur många filer de kan innehålla.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="fd8ab-220">Rotkatalogen kan bara innehålla det antal poster som bestäms av startposten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-221">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-221">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-222">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-223">**directory_name:** Pekare till namnet på katalogen som ska skapas (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-224">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-224">Return Values</span></span>

- <span data-ttu-id="fd8ab-225">**FX_SUCCESS** (0x00) Lyckad katalog create.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="fd8ab-226">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-227">**FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="fd8ab-228">**FX_NOT_DIRECTORY post** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="fd8ab-229">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="fd8ab-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-230">**FX_FILE _CORRUPT** (0x08) filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-231">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-232">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-233">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-234">**FX_MEDIA_INVALID** (0x02) Ogiltig media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="fd8ab-235">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="fd8ab-236">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="fd8ab-237">**FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="fd8ab-238">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-239">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-239">Allowed From</span></span>

<span data-ttu-id="fd8ab-240">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-241">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-242">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-242">See Also</span></span>

- <span data-ttu-id="fd8ab-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-245">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-246">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-247">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-250">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-256">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-259">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="fd8ab-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-263">fx_directory_default_get</span></span>

<span data-ttu-id="fd8ab-264">Hämtar den senaste standardkatalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-265">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-266">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-266">Description</span></span>

<span data-ttu-id="fd8ab-267">Den här tjänsten returnerar pekaren till sökvägen som senast angetts ***av fx_directory_default_set***.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="fd8ab-268">Om standardkatalogen inte har angetts eller om den aktuella standardkatalogen är rotkatalogen returneras värdet FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-269">*Standardstorleken för den interna sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-270">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-270">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-271">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-272">**return_path_name:** Pekare till målet för den senaste standardkatalogsträngen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="fd8ab-273">Värdet för FX_NULL returneras om den aktuella inställningen för standardkatalogen är roten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="fd8ab-274">När mediet öppnas är roten standard.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-275">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-275">Return Values</span></span>

- <span data-ttu-id="fd8ab-276">**FX_SUCCESS** (0x00) Lyckad standardkatalog hämta</span><span class="sxs-lookup"><span data-stu-id="fd8ab-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="fd8ab-277">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-278">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="fd8ab-279">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-280">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-280">Allowed From</span></span>

<span data-ttu-id="fd8ab-281">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-282">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-283">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-283">See Also</span></span>

- <span data-ttu-id="fd8ab-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-286">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-287">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-288">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-291">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-297">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-300">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="fd8ab-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-304">fx_directory_default_set</span></span>

<span data-ttu-id="fd8ab-305">Anger standardkatalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-306">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-307">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-307">Description</span></span>

<span data-ttu-id="fd8ab-308">Den här tjänsten anger standardkatalogen för mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="fd8ab-309">Om ett värde FX_NULL anges anges standardkatalogen till mediets rotkatalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="fd8ab-310">Alla efterföljande filåtgärder som inte uttryckligen anger en sökväg kommer som standard att använda den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-311">*Standardstorleken för den interna sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-312">*För namn som anges av programmet har FileX stöd för både omsnedstreck ( ) och snedstreck (/) tecken för att avgränsa \\ kataloger, underkataloger och filnamn. FileX använder dock bara omsnedstreckstecknet i sökvägar som returneras till programmet.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-313">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-313">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-314">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-315">**new_path_name:** Pekare till nytt standardkatalognamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="fd8ab-316">Om ett värde FX_NULL anges anges standardkatalogen för mediet till mediets rotkatalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-317">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-317">Return Values</span></span>

- <span data-ttu-id="fd8ab-318">**FX_SUCCESS** (0x00) Lyckad standardkataloguppsättning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="fd8ab-319">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-320">**FX_INVALID_PATH** (0x0D) Det gick inte att hitta den nya katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="fd8ab-321">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-322">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-323">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-323">Allowed From</span></span>

<span data-ttu-id="fd8ab-324">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-325">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-326">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-326">See Also</span></span>

- <span data-ttu-id="fd8ab-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-329">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-330">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-331">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-334">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-340">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-343">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="fd8ab-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-347">fx_directory_delete</span></span>

<span data-ttu-id="fd8ab-348">Tar bort underkatalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-349">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-350">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-350">Description</span></span>

<span data-ttu-id="fd8ab-351">Den här tjänsten tar bort den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-351">This service deletes the specified directory.</span></span> <span data-ttu-id="fd8ab-352">Observera att katalogen måste vara tom för att ta bort den.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-353">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-353">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-354">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-355">**directory_name: Pekare** till namnet på katalogen som ska tas bort (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-356">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-356">Return Values</span></span>

- <span data-ttu-id="fd8ab-357">**FX_SUCCESS** (0x00) Lyckad katalog borttagning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="fd8ab-358">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-359">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="fd8ab-360">**FX_DIR_NOT_EMPTY** (0x10) Den angivna katalogen är inte tom</span><span class="sxs-lookup"><span data-stu-id="fd8ab-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="fd8ab-361">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="fd8ab-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-362">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat</span><span class="sxs-lookup"><span data-stu-id="fd8ab-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="fd8ab-363">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-364">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-365">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-366">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-367">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="fd8ab-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="fd8ab-368">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="fd8ab-369">**FX_NOT_DIRECTORY** (0x0E) Inte en katalogpost</span><span class="sxs-lookup"><span data-stu-id="fd8ab-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="fd8ab-370">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="fd8ab-371">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-372">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-372">Allowed From</span></span>

<span data-ttu-id="fd8ab-373">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-374">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-375">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-375">See Also</span></span>

- <span data-ttu-id="fd8ab-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-378">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-379">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-380">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-383">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-389">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-392">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="fd8ab-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="fd8ab-397">Hämtar den första katalogposten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-398">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-399">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-399">Description</span></span>

<span data-ttu-id="fd8ab-400">Den här tjänsten hämtar det första postnamnet i standardkatalogen och kopierar det till det angivna målet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-401">*Det angivna målet måste vara tillräckligt stort för att innehålla det maximala FileX-namnet, enligt definitionen i **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="fd8ab-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-402">*Om du använder en icke-lokal sökväg är det viktigt att förhindra andra programtrådar från att ändra den här katalogen medan en katalog-traverserning äger rum (med en ThreadX-semaphore, mutex eller prioritetsnivåändring). Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-403">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-403">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-404">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-405">**return_entry_name:** Pekare till mål för det första postnamnet i standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-406">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-406">Return Values</span></span>

- <span data-ttu-id="fd8ab-407">**FX_SUCCESS** (0x00) Lyckad första katalogpost</span><span class="sxs-lookup"><span data-stu-id="fd8ab-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="fd8ab-408">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-409">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="fd8ab-410">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="fd8ab-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-411">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-412">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-413">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-414">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="fd8ab-415">**FX_CALLER_ERROR** (0x20) Anroparen är inte en tråd</span><span class="sxs-lookup"><span data-stu-id="fd8ab-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-416">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-416">Allowed From</span></span>

<span data-ttu-id="fd8ab-417">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-418">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-419">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-419">See Also</span></span>

- <span data-ttu-id="fd8ab-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-422">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-423">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-424">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-425">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-427">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-433">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-436">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="fd8ab-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="fd8ab-441">Hämtar den första katalogposten med fullständig information</span><span class="sxs-lookup"><span data-stu-id="fd8ab-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-442">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="fd8ab-443">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-443">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-444">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-445">**directory_name:** Pekare till målet för namnet på en katalogpost.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="fd8ab-446">Måste vara minst lika stor som FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="fd8ab-447">**attribut:** Om det inte är null pekar du mot målet för postens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="fd8ab-448">Attributen returneras i bitkartformat med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="fd8ab-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="fd8ab-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="fd8ab-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="fd8ab-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="fd8ab-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="fd8ab-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="fd8ab-455">**size**: Om det inte är null pekar du till målet för postens storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="fd8ab-456">**year**: Om det inte är null pekar du till målet för postens ändringsår.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="fd8ab-457">**month**: Om det inte är null pekar du till målet för postens ändringsmånad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="fd8ab-458">**day**: Om det inte är null pekar du mot målet för postens ändringsdag.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="fd8ab-459">**hour**: Om det inte är null pekar du mot målet för postens ändringstimmar.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="fd8ab-460">**minute**: Om det inte är null pekar du mot målet för postens ändringsminut.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="fd8ab-461">**second**: Om det inte är null pekar du till målet för postens andra ändring.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-462">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-462">Return Values</span></span>

- <span data-ttu-id="fd8ab-463">**FX_SUCCESS** (0x00) Lyckad första katalogposts find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="fd8ab-464">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-465">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="fd8ab-466">**FX_IO_ERROR** (0x90) Drivrutins-I/O</span><span class="sxs-lookup"><span data-stu-id="fd8ab-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-467">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade</span><span class="sxs-lookup"><span data-stu-id="fd8ab-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="fd8ab-468">**FX_FILE _CORRUPT** (0x08) filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-469">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-470">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-471">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-472">**FX_MEDIA_INVALID** (0x02) Ogiltig media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="fd8ab-473">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="fd8ab-474">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-475">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-475">Allowed From</span></span>

<span data-ttu-id="fd8ab-476">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-477">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-477">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-478">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-478">See Also</span></span>

- <span data-ttu-id="fd8ab-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-481">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-482">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-483">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-484">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-486">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-492">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-495">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="fd8ab-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-499">fx_directory_information_get:</span></span>

<span data-ttu-id="fd8ab-500">Hämtar information om katalogpost</span><span class="sxs-lookup"><span data-stu-id="fd8ab-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-501">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="fd8ab-502">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-502">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-503">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-504">**directory_name:** Pekare till namnet på katalogposten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="fd8ab-505">**attribut:** Pekare till målet för attributen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="fd8ab-506">**storlek:** Pekare till målet för storleken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="fd8ab-507">**year**: Pekare till årets mål.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="fd8ab-508">**month**: Pekare till målet för månaden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="fd8ab-509">**day**: Pekare till dagens mål.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="fd8ab-510">**hour**: Pekare till målet för timmen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="fd8ab-511">**minute**: Pekare till målet för minuten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="fd8ab-512">**second**: Pekare till målet för den andra.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-513">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-513">Return Values</span></span>

- <span data-ttu-id="fd8ab-514">**FX_SUCCESS** (0x00) Lyckad första katalogposts find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="fd8ab-515">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-516">**FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="fd8ab-517">**FX_IO_ERROR** (0x90) Drivrutins-I/O</span><span class="sxs-lookup"><span data-stu-id="fd8ab-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-518">**FX_MEDIA_INVALID** (0x02) Ogiltig media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="fd8ab-519">**FX_FILE _CORRUPT** (0x08) filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-520">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-521">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-522">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-523">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="fd8ab-524">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-525">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-525">Allowed From</span></span>

<span data-ttu-id="fd8ab-526">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-527">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-527">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-528">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-528">See Also</span></span>

- <span data-ttu-id="fd8ab-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-531">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-532">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-533">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-534">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-542">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-545">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="fd8ab-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="fd8ab-550">Rensar den lokala standardsökvägen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-551">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="fd8ab-552">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-552">Description</span></span>

<span data-ttu-id="fd8ab-553">Den här tjänsten rensar den tidigare lokala sökvägen som har ställts in för anropstråden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-554">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-554">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-555">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-556">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-556">Return Values</span></span>

- <span data-ttu-id="fd8ab-557">**FX_SUCCESS** (0x00) Lyckad lokal sökväg rensas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="fd8ab-558">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande</span><span class="sxs-lookup"><span data-stu-id="fd8ab-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="fd8ab-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH har definierats</span><span class="sxs-lookup"><span data-stu-id="fd8ab-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="fd8ab-560">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-561">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-561">Allowed From</span></span>

<span data-ttu-id="fd8ab-562">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-563">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-564">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-564">See Also</span></span>

- <span data-ttu-id="fd8ab-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-567">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-568">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-569">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-570">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-573">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-578">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-581">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="fd8ab-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="fd8ab-586">Hämtar den aktuella lokala sökvägssträngen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-587">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-588">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-588">Description</span></span>

<span data-ttu-id="fd8ab-589">Den här tjänsten returnerar pekaren för den lokala sökvägen för det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="fd8ab-590">Om det inte finns någon lokal sökväg returneras null till anroparen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-591">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-591">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-592">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-593">**return_path_name:** Pekare till målsträngens pekare för den lokala sökvägssträng som ska lagras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-594">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-594">Return Values</span></span>

- <span data-ttu-id="fd8ab-595">**FX_SUCCESS** (0x00) Lyckad lokal sökväg hämta.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="fd8ab-596">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande</span><span class="sxs-lookup"><span data-stu-id="fd8ab-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="fd8ab-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="fd8ab-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="fd8ab-598">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="fd8ab-599">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-599">Allowed From</span></span>

<span data-ttu-id="fd8ab-600">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-601">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-602">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-602">See Also</span></span>

- <span data-ttu-id="fd8ab-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-605">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-606">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-607">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-608">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-611">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-616">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-619">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="fd8ab-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="fd8ab-624">Återställer tidigare lokal sökväg</span><span class="sxs-lookup"><span data-stu-id="fd8ab-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-625">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="fd8ab-626">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-626">Description</span></span>

<span data-ttu-id="fd8ab-627">Den här tjänsten återställer en tidigare inställd lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-627">This service restores a previously set local path.</span></span> <span data-ttu-id="fd8ab-628">Katalogsökpositionen som görs på den här lokala sökvägen återställs också, vilket gör den här rutinen användbar i rekursiva katalogtratter av programmet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-629">*Varje lokal sökväg innehåller en lokal sökvägssträng **med FX_MAXIMUM_PATH** storlek, som som standard är 256 tecken. Den här interna sökvägssträngen används inte av FileX och tillhandahålls endast för programmets användning. Om **FX_LOCAL_PATH** ska deklareras som en lokal variabel bör användarna vara försiktig med stacken som växer med storleken på den här strukturen. Användare är välkommen att minska storleken på FX_MAXIMUM_PATH **och** återskapa FileX-bibliotekskällan.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-630">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-630">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-631">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-632">**local_path_ptr:** Pekare till den tidigare inställt lokala sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="fd8ab-633">Det är mycket viktigt att se till att pekaren verkligen pekar på en tidigare använd och fortfarande intakt lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-634">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-634">Return Values</span></span>

- <span data-ttu-id="fd8ab-635">**FX_SUCCESS** (0x00) Lyckad återställning av lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="fd8ab-636">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="fd8ab-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH definieras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="fd8ab-638">**FX_PTR_ERROR** (0x18) Ogiltig media eller lokal sökvägs pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-639">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-639">Allowed From</span></span>

<span data-ttu-id="fd8ab-640">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-641">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-642">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-642">See Also</span></span>

- <span data-ttu-id="fd8ab-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-645">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-646">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-647">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-648">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-651">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-656">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-659">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="fd8ab-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="fd8ab-664">Uppsättningar en trådspecifik lokal sökväg</span><span class="sxs-lookup"><span data-stu-id="fd8ab-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-665">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-666">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-666">Description</span></span>

<span data-ttu-id="fd8ab-667">Den här tjänsten uppsättningar en trådspecifik sökväg som anges av \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="fd8ab-668">När den här rutinen har slutförts har den lokala sökvägsinformationen som lagras i _ *_local_path_ptr_*\* företräde framför den globala mediesökvägen för alla fil- och katalogåtgärder som utförs av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="fd8ab-669">Detta påverkar inte någon annan tråd i systemet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="fd8ab-670">*Standardstorleken för den lokala sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-671">*För namn som anges av programmet har FileX stöd för både omsnedstreck ( ) och snedstreck (/) tecken för att avgränsa \\ kataloger, underkataloger och filnamn. FileX använder dock bara omsnedstreckstecknet i sökvägar som returneras till programmet.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-672">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-672">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-673">**media_ptr:** Pekare till tidigare öppnade media.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="fd8ab-674">**local_path_ptr:** Mål för att lagra den trådspecifika lokala sökvägsinformationen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="fd8ab-675">Adressen för den här strukturen kan anges för den lokala funktionen för sökvägsåterställning i framtiden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="fd8ab-676">**new_path_name:** Anger den lokala sökvägen till konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-677">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-677">Return Values</span></span>

- <span data-ttu-id="fd8ab-678">**FX_SUCCESS** (0x00) Lyckad standardkataloguppsättning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="fd8ab-679">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="fd8ab-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="fd8ab-681">**FX_INVALID_PATH** (0x0D) Det gick inte att hitta den nya katalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="fd8ab-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH har definierats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="fd8ab-683">**FX_PTR_ERROR** (0x18) Ogiltig media eller lokal sökvägs pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-684">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-684">Allowed From</span></span>

<span data-ttu-id="fd8ab-685">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-686">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-686">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-687">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-687">See Also</span></span>

- <span data-ttu-id="fd8ab-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-690">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-691">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-692">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-693">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-696">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-701">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-704">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="fd8ab-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="fd8ab-709">Hämtar långt namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-710">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-711">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-711">Description</span></span>

<span data-ttu-id="fd8ab-712">Den här tjänsten hämtar det långa namnet (om det finns) som är associerat med det angivna korta (8,3-format) namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="fd8ab-713">Det korta namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-714">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-714">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-715">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-716">**short_name**: Pekare till källans korta namn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="fd8ab-717">**long_name:** Pekare till målet för det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="fd8ab-718">Om det inte finns något långt namn returneras det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="fd8ab-719">Observera att målet för det långa namnet måste vara tillräckligt stort för att innehålla FX_MAX_LONG_NAME_LEN tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-720">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-720">Return Values</span></span>

- <span data-ttu-id="fd8ab-721">**FX_SUCCESS** (0x00) Successful long name get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="fd8ab-722">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="fd8ab-723">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="fd8ab-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="fd8ab-724">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="fd8ab-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="fd8ab-725">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-726">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="fd8ab-727">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="fd8ab-728">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-729">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare</span><span class="sxs-lookup"><span data-stu-id="fd8ab-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="fd8ab-730">**FX_CALLER_ERROR** (0x20) Anroparen är inte en tråd</span><span class="sxs-lookup"><span data-stu-id="fd8ab-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-731">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-731">Allowed From</span></span>

<span data-ttu-id="fd8ab-732">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-733">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-734">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-734">See Also</span></span>

- <span data-ttu-id="fd8ab-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-737">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-738">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-739">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-740">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-743">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-748">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-751">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="fd8ab-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="fd8ab-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="fd8ab-756">Hämtar långt namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-757">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="fd8ab-758">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-758">Description</span></span>

<span data-ttu-id="fd8ab-759">Den här tjänsten hämtar det långa namnet (om det finns) som är associerat med det angivna korta (8,3-format) namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="fd8ab-760">Det korta namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-761">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-761">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-762">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-763">**short_name**: Pekare till källans korta namn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="fd8ab-764">**long_name:** Pekare till målet för det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="fd8ab-765">Om det inte finns något långt namn returneras det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="fd8ab-766">Obs! Målet för det långa namnet måste vara tillräckligt stort för att innehålla **FX_MAX_LONG_NAME_LEN** tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="fd8ab-767">**long_file_name_buffer_length:** Längden på den långa namnbufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-768">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-768">Return Values</span></span>

- <span data-ttu-id="fd8ab-769">**FX_SUCCESS** (0x00) Successful long name get.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="fd8ab-770">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="fd8ab-771">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-772">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-773">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-774">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-775">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-776">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="fd8ab-777">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="fd8ab-778">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-779">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-779">Allowed From</span></span>

<span data-ttu-id="fd8ab-780">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-781">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-782">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-782">See Also</span></span>

- <span data-ttu-id="fd8ab-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-785">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-786">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-787">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-788">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-791">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-799">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="fd8ab-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-803">fx_directory_name_test</span></span>

<span data-ttu-id="fd8ab-804">Tester för katalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-805">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-806">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-806">Description</span></span>

<span data-ttu-id="fd8ab-807">Den här tjänsten testar om det angivna namnet är en katalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="fd8ab-808">I så fall returneras FX_SUCCESS en ny.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-809">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-809">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-810">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-811">**directory_name:** Pekare till namnet på katalogposten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-812">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-812">Return Values</span></span>

- <span data-ttu-id="fd8ab-813">**FX_SUCCESS** (0x00) Det angivna namnet är en katalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="fd8ab-814">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="fd8ab-815">**FX_NOT_FOUND** (0x04) Det gick inte att hitta katalogposten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="fd8ab-816">**FX_NOT_DIRECTORY post** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="fd8ab-817">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-818">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-819">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-820">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-821">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-822">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="fd8ab-823">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="fd8ab-824">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-825">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-825">Allowed From</span></span>

<span data-ttu-id="fd8ab-826">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-827">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-828">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-828">See Also</span></span>

- <span data-ttu-id="fd8ab-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-831">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-832">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-833">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-834">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-837">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-845">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="fd8ab-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="fd8ab-849">Hämtar nästa katalogpost</span><span class="sxs-lookup"><span data-stu-id="fd8ab-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-850">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-851">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-851">Description</span></span>

<span data-ttu-id="fd8ab-852">Den här tjänsten returnerar nästa postnamn i den aktuella standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-853">*Om du använder en icke-lokal sökväg är det också viktigt att förhindra (med en ThreadX-semaphore eller trådprioritetsnivå) andra programtrådar från att ändra den här katalogen medan en katalog-traverserning sker. Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-854">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-854">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-855">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-856">**return_entry_name:** Pekare till mål för nästa postnamn i standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="fd8ab-857">Bufferten som pekar på den här pekaren måste vara tillräckligt stor för att innehålla den maximala storleken för FileX-namn, som definieras **_av FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-858">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-858">Return Values</span></span>

- <span data-ttu-id="fd8ab-859">**FX_SUCCESS** (0x00) Lyckad nästa post</span><span class="sxs-lookup"><span data-stu-id="fd8ab-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="fd8ab-860">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-861">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="fd8ab-862">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-863">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-864">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-865">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-866">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-867">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-868">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-869">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-869">Allowed From</span></span>

<span data-ttu-id="fd8ab-870">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-871">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-872">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-872">See Also</span></span>

- <span data-ttu-id="fd8ab-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-875">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-876">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-877">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-878">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-881">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-887">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-889">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="fd8ab-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="fd8ab-894">Hämtar nästa katalogpost med fullständig information</span><span class="sxs-lookup"><span data-stu-id="fd8ab-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-895">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-895">Prototype</span></span>

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="fd8ab-896">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-896">Description</span></span>

<span data-ttu-id="fd8ab-897">Den här tjänsten hämtar nästa postnamn i standardkatalogen och kopierar det till det angivna målet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="fd8ab-898">Den returnerar också fullständig information om posten som anges av de ytterligare indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-899">*Det angivna målet måste vara tillräckligt stort för att innehålla det maximala FileX-namnet, enligt definitionen i FX_MAX_LONG_NAME_LEN*...</span><span class="sxs-lookup"><span data-stu-id="fd8ab-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-900">*Om du använder en icke-lokal sökväg är det viktigt att förhindra andra programtrådar från att ändra den här katalogen medan en katalog-traverserning äger rum (med en ThreadX-semaphore, mutex eller prioritetsnivåändring). Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-901">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-901">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-902">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-903">**directory_name:** Pekare till målet för namnet på en katalogpost.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="fd8ab-904">Måste vara minst lika stor som **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="fd8ab-905">**attribut:** Om det inte är null pekar du mot målet för postens attribut som ska placeras. Attributen returneras i bitkartformat med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="fd8ab-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="fd8ab-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="fd8ab-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="fd8ab-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="fd8ab-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="fd8ab-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="fd8ab-912">**storlek:** Om det inte är null pekar du till målet för postens storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="fd8ab-913">**month**: Om det inte är null pekar du mot målet för postens ändringsmånad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="fd8ab-914">**year**: Om det inte är null pekar du mot målet för postens ändringsår.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="fd8ab-915">**day**: Om det inte är null pekar du mot målet för postens ändringsdag.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="fd8ab-916">**hour**: Om det inte är null pekar du mot målet för postens ändringstimmar.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="fd8ab-917">**minute**: Om det inte är null pekar du mot målet för postens ändringsminut.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="fd8ab-918">**second**: Om det inte är null pekar du till målet för postens andra ändring.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-919">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-919">Return Values</span></span>

- <span data-ttu-id="fd8ab-920">**FX_SUCCESS** (0x00) Nästa katalogpost söks.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="fd8ab-921">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-922">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="fd8ab-923">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-924">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-925">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-926">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-927">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="fd8ab-928">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-929">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare eller alla indataparametrar är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="fd8ab-930">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-931">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-931">Allowed From</span></span>

<span data-ttu-id="fd8ab-932">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-933">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-933">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-934">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-934">See Also</span></span>

- <span data-ttu-id="fd8ab-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-937">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-938">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-939">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-940">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-943">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-949">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-951">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="fd8ab-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-955">fx_directory_rename</span></span>

<span data-ttu-id="fd8ab-956">Byter namn på katalogen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-957">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-958">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-958">Description</span></span>

<span data-ttu-id="fd8ab-959">Den här tjänsten ändrar katalognamnet till det angivna nya katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="fd8ab-960">Namnbyte görs också i förhållande till den angivna sökvägen eller standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="fd8ab-961">Om en sökväg anges i det nya katalognamnet flyttas den omdöpta katalogen effektivt till den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="fd8ab-962">Om ingen sökväg anges placeras den omdöpta katalogen i den aktuella standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-963">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-963">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-964">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-965">**old_directory_name**: Pekare till aktuellt katalognamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="fd8ab-966">**new_directory_name**: Pekare till nytt katalognamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-967">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-967">Return Values</span></span>

- <span data-ttu-id="fd8ab-968">**FX_SUCCESS** (0x00) Lyckad katalogbyte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="fd8ab-969">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-970">**FX_NOT_FOUND** (0x04) Det gick inte att hitta katalogposten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="fd8ab-971">**FX_NOT_DIRECTORY** (0x0E) Posten är inte en katalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="fd8ab-972">**FX_INVALID_NAME** (0x0C) Nytt katalognamn är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="fd8ab-973">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-974">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-975">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-976">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-977">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-978">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="fd8ab-979">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-980">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="fd8ab-981">**FX_INVALID_PATH** (0x0D) Ogiltig sökväg med katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="fd8ab-982">**FX_ALREADY_CREATED** (0x0B) Angiven katalog har redan skapats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="fd8ab-983">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-984">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-985">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-985">Allowed From</span></span>

<span data-ttu-id="fd8ab-986">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-987">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-988">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-988">See Also</span></span>

- <span data-ttu-id="fd8ab-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-991">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-992">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-993">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-994">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-997">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="fd8ab-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="fd8ab-1010">Hämtar ett kort namn från ett långt namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1011">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-1012">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1012">Description</span></span>

<span data-ttu-id="fd8ab-1013">Den här tjänsten hämtar det korta (8.3-format) namnet som är associerat med det angivna långa namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="fd8ab-1014">Det långa namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1015">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1015">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1016">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-1017">**long_name:** Pekare till källans långa namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="fd8ab-1018">**short_name**: Pekare till målets kortnamn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="fd8ab-1019">Observera att målet för det korta namnet måste vara tillräckligt stort för att innehålla 14 tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1020">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1020">Return Values</span></span>

- <span data-ttu-id="fd8ab-1021">**FX_SUCCESS** (0x00) Ett lyckat kortnamn get.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="fd8ab-1022">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="fd8ab-1023">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1024">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1025">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1026">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1027">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1028">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1029">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-1030">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="fd8ab-1031">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1032">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1032">Allowed From</span></span>

<span data-ttu-id="fd8ab-1033">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1034">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1035">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1035">See Also</span></span>

- <span data-ttu-id="fd8ab-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1038">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1041">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1053">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="fd8ab-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="fd8ab-1057">Hämtar ett kort namn från ett långt namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1058">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="fd8ab-1059">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1059">Description</span></span>

<span data-ttu-id="fd8ab-1060">Den här tjänsten hämtar det korta (8.3-format) namnet som är associerat med det angivna långa namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="fd8ab-1061">Det långa namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1062">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1062">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1063">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-1064">**long_name:** Pekare till källans långa namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="fd8ab-1065">**short_name**: Pekare till målets kortnamn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="fd8ab-1066">Obs! Målet för det korta namnet måste vara tillräckligt stort för att innehålla 14 tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="fd8ab-1067">**short_file_name_length:** Längden på den korta namnbufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1068">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1068">Return Values</span></span>

- <span data-ttu-id="fd8ab-1069">**FX_SUCCESS** (0x00) Ett lyckat kortnamn get.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="fd8ab-1070">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="fd8ab-1071">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1072">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1073">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1074">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1075">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1076">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1077">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-1078">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="fd8ab-1079">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1080">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1080">Allowed From</span></span>

<span data-ttu-id="fd8ab-1081">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1082">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1083">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1083">See Also</span></span>

- <span data-ttu-id="fd8ab-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1086">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1089">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1101">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="fd8ab-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="fd8ab-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="fd8ab-1105">Aktiverar den feltoleranta tjänsten</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1106">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="fd8ab-1107">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1107">Description</span></span>

<span data-ttu-id="fd8ab-1108">Den här tjänsten aktiverar den feltoleranta modulen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="fd8ab-1109">Vid start identifierar den feltoleranta modulen huruvida filsystemet är under FileX-feltolerant skydd eller inte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="fd8ab-1110">Om den inte är det hittar tjänsten tillgängliga sektorer i filsystemet för att lagra loggar på filsystemtransaktioner.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="fd8ab-1111">Om filsystemet är under FileX-feltolerant skydd tillämpar det loggarna på filsystemet för att upprätthålla dess integritet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1112">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1112">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1113">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-1114">**memory_ptr:** Pekare till ett minnesblock som används av den feltoleranta modulen som ett minne som är försnåe.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="fd8ab-1115">**memory_size:** Storleken på det scratch-minnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="fd8ab-1116">För att feltoleranta ska fungera korrekt ska den scratch-minnesstorleken vara minst 3072 byte, och den måste vara flera av sektorstorleken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1117">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1117">Return Values</span></span>

- <span data-ttu-id="fd8ab-1118">**FX_SUCCESS** (0x00) Feltolerans har aktiverats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="fd8ab-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) för liten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="fd8ab-1120">**FX_BOOT_ERROR** (0x01) Startsektorfel.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="fd8ab-1121">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1122">**FX_NO_MORE_ENTRIES** (0x0F) Inget mer ledigt kluster tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="fd8ab-1123">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="fd8ab-1124">**FX_SECTOR_INVALID** (0x89) sektor är ogiltig</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="fd8ab-1125">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1126">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-1127">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1128">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1128">Allowed From</span></span>

<span data-ttu-id="fd8ab-1129">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1130">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1131">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1131">See Also</span></span>

- <span data-ttu-id="fd8ab-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1132">fx_system_initialize</span></span>
- <span data-ttu-id="fd8ab-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1133">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1135">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1136">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1140">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1141">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1142">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1144">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1145">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="fd8ab-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1149">fx_file_allocate</span></span>

<span data-ttu-id="fd8ab-1150">Allokerar utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1152">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1152">Description</span></span>

<span data-ttu-id="fd8ab-1153">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="fd8ab-1154">FileX fastställer antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="fd8ab-1155">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="fd8ab-1156">Om du vill allokera mer än 4 GB utrymme ska programmet använda *tjänsten fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1157">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1157">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1158">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-1159">**size**: Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1160">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1160">Return Values</span></span>

- <span data-ttu-id="fd8ab-1161">**FX_SUCCESS** (0x00) Lyckad filallokering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="fd8ab-1162">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-1163">**FX_FAT_READ_ERROR** (0x03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1164">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1165">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-1166">**FX_NO_MORE_ENTRIES** (0x0F) Inget mer ledigt kluster tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="fd8ab-1167">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="fd8ab-1168">**FX_SECTOR_INVALID** (0x89) sektor är ogiltig</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="fd8ab-1169">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1170">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1171">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-1172">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1173">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1173">Allowed From</span></span>

<span data-ttu-id="fd8ab-1174">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1175">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1176">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1176">See Also</span></span>

- <span data-ttu-id="fd8ab-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1180">fx_file_close– fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1182">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1189">fx_file_open– fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1191">fx_file_rename– fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1192">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1194">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="fd8ab-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="fd8ab-1201">Läser filattribut</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1202">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1203">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1203">Description</span></span>

<span data-ttu-id="fd8ab-1204">Den här tjänsten läser filens attribut från det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1205">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1205">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1206">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-1207">**file_name:** Pekare till namnet på den begärda filen (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="fd8ab-1208">**attributes_ptr:** Pekare till målet för filens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="fd8ab-1209">Filattributen returneras i ett bitkartformat med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="fd8ab-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="fd8ab-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="fd8ab-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="fd8ab-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="fd8ab-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="fd8ab-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1216">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1216">Return Values</span></span>

- <span data-ttu-id="fd8ab-1217">**FX_SUCCESS** (0x00) Lyckad attributläsning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="fd8ab-1218">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-1219">**FX_NOT_FOUND** (0x04) Den angivna filen hittades inte på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="fd8ab-1220">**FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="fd8ab-1221">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1222">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1223">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1224">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1225">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1226">**FX_PTR_ERROR** (0x18) Ogiltig media eller attribut pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="fd8ab-1227">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1228">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1228">Allowed From</span></span>

<span data-ttu-id="fd8ab-1229">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1230">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1231">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1231">See Also</span></span>

- <span data-ttu-id="fd8ab-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1232">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1235">fx_file_close– fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1237">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1244">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1245">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1247">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1248">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1249">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1251">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="fd8ab-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="fd8ab-1258">Anger filattribut</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1259">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1260">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1260">Description</span></span>

<span data-ttu-id="fd8ab-1261">Den här tjänsten anger filens attribut till de som anges av anroparen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-1262">*Programmet kan bara ändra en delmängd av filens attribut med den här tjänsten. Om du försöker ange ytterligare attribut resulterar det i ett fel.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1263">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1263">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1264">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-1265">**file_name:** Pekare till namnet på den begärda filen\*\* (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="fd8ab-1266">**attribut:** De nya attributen för filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="fd8ab-1267">De giltiga filattributen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="fd8ab-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="fd8ab-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="fd8ab-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="fd8ab-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1272">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1272">Return Values</span></span>

- <span data-ttu-id="fd8ab-1273">**FX_SUCCESS** (0x00) Lyckad attributuppsättning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="fd8ab-1274">**FX_ACCESS_ERROR** (0x06) Filen är öppen och kan inte ha sina attribut inställda.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="fd8ab-1275">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1276">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1277">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-1278">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i FAT-tabellen eller exFAT-klusterkartan.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="fd8ab-1279">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="fd8ab-1280">**FX_NOT_FOUND** (0x04) Den angivna filen hittades inte på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="fd8ab-1281">**FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="fd8ab-1282">**FX_SECTOR_INVALID** (0x89) sektor är ogiltig</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="fd8ab-1283">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1284">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1285">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-1286">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-1287">**FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="fd8ab-1288">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1289">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1289">Allowed From</span></span>

<span data-ttu-id="fd8ab-1290">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1291">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1292">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1292">See Also</span></span>

- <span data-ttu-id="fd8ab-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1293">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1296">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1297">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1299">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1306">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1307">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1309">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1310">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1311">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1313">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="fd8ab-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="fd8ab-1320">Bästa möjliga resultat för att allokera utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1321">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1322">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1322">Description</span></span>

<span data-ttu-id="fd8ab-1323">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="fd8ab-1324">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="fd8ab-1325">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="fd8ab-1326">Om det inte finns tillräckligt många kluster i följd tillgängliga på mediet länkar den här tjänsten det största tillgängliga blocket med kluster i följd till filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="fd8ab-1327">Mängden utrymme som faktiskt allokerats till filen returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="fd8ab-1328">Om du vill allokera mer än 4 GB utrymme ska programmet använda tjänsten *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1329">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1329">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1330">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-1331">**size**: Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1332">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1332">Return Values</span></span>

- <span data-ttu-id="fd8ab-1333">**FX_SUCCESS** (0x00) Lyckad filallokering med bästa resultat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="fd8ab-1334">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-1335">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-1336">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="fd8ab-1337">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1338">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1339">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1340">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1341">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1342">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1343">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare eller mål.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="fd8ab-1344">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1345">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1345">Allowed From</span></span>

<span data-ttu-id="fd8ab-1346">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1347">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1348">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1348">See Also</span></span>

- <span data-ttu-id="fd8ab-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1349">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1352">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1353">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1355">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1362">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1363">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1365">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1366">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1367">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1369">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="fd8ab-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1375">fx_file_close</span></span>

<span data-ttu-id="fd8ab-1376">Stänger filen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1377">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1378">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1378">Description</span></span>

<span data-ttu-id="fd8ab-1379">Den här tjänsten stänger den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1379">This service closes the specified file.</span></span> <span data-ttu-id="fd8ab-1380">Om filen var öppen för skrivning och om den ändrades slutför den här tjänsten filändringsprocessen genom att uppdatera dess katalogpost med den nya storleken och systemets aktuella tid och datum.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1381">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1381">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1382">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1383">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1383">Return Values</span></span>

- <span data-ttu-id="fd8ab-1384">**FX_SUCCESS** (0x00) Lyckades.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="fd8ab-1385">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="fd8ab-1386">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1387">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1388">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1389">**FX_PTR_ERROR** (0x18) Ogiltig media eller attribut pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="fd8ab-1390">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1391">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1391">Allowed From</span></span>

<span data-ttu-id="fd8ab-1392">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1393">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1394">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1394">See Also</span></span>

- <span data-ttu-id="fd8ab-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1395">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1399">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1401">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1408">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1409">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1411">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1412">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1413">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1415">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="fd8ab-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1421">fx_file_create</span></span>

<span data-ttu-id="fd8ab-1422">Skapar fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1423">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1424">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1424">Description</span></span>

<span data-ttu-id="fd8ab-1425">Den här tjänsten skapar den angivna filen i standardkatalogen eller i den katalogsökväg som medföljer filnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-1426">*Den här tjänsten skapar en fil med ingen längd, dvs. inga kluster allokerade. Allokering sker automatiskt vid efterföljande fil skrivningar eller kan göras i förväg med tjänsten fx_file_allocate eller fx_file_extended_allocate utrymme över 4 GB).*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1427">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1427">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1428">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-1429">**file_name:** Pekare till namnet på filen som ska skapas (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1430">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1430">Return Values</span></span>

- <span data-ttu-id="fd8ab-1431">**FX_SUCCESS** (0x00) Lyckades fil skapas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="fd8ab-1432">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-1433">**FX_ALREADY_CREATED** (0x0B) Den angivna filen har redan skapats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="fd8ab-1434">**FX_NO_MORE_SPACE** (0x0A) Det finns antingen inga fler poster i rotkatalogen eller så finns det inga fler kluster tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="fd8ab-1435">**FX_INVALID_PATH** (0x0D) Ogiltig sökväg medföljer filnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="fd8ab-1436">**FX_INVALID_NAME** (0x0C) är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="fd8ab-1437">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1438">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1439">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1440">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1441">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1442">**FX_MEDIA_INVALID** (0x02)Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="fd8ab-1443">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1444">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1445">**FX_PTR_ERROR** (0x18) Ogiltig media- eller filnamnspekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="fd8ab-1446">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1447">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1447">Allowed From</span></span>

<span data-ttu-id="fd8ab-1448">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1449">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1450">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1450">See Also</span></span>
- <span data-ttu-id="fd8ab-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1451">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1455">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1457">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1464">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1465">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1467">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1468">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1469">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1471">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="fd8ab-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="fd8ab-1478">Anger filens datum och tid</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1478">Sets file date and time</span></span>

<span data-ttu-id="fd8ab-1479">Ange fildatum och -tid</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1480">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1480">Prototype</span></span>

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1481">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1481">Description</span></span>

<span data-ttu-id="fd8ab-1482">Den här tjänsten anger datum och tid för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1483">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1483">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1484">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-1485">**file_name**: Pekare till namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="fd8ab-1486">**year**: Värdet för året (inklusive 1980–2107).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="fd8ab-1487">**month**: Värdet för månad (inklusive 1–12).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="fd8ab-1488">**day**: Värdet för dagen (inklusive 1–31).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="fd8ab-1489">**hour**: Timvärde (inklusive 0–23).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="fd8ab-1490">**minute**: Minutvärdet (inklusive 0–59).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="fd8ab-1491">**second**: Värdet för sekund (inklusive 0–59).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1492">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1492">Return Values</span></span>

- <span data-ttu-id="fd8ab-1493">**FX_SUCCESS** (0x00) Datum/tid har angetts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="fd8ab-1494">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-1495">**FX_NOT_FOUND** (0x04) Hittades inte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="fd8ab-1496">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1497">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1498">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1499">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1500">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="fd8ab-1501">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1502">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1503">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="fd8ab-1504">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="fd8ab-1505">**FX_INVALID_YEAR** (0x12) År är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="fd8ab-1506">**FX_INVALID_MONTH** (0x13) Månad är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="fd8ab-1507">**FX_INVALID_DAY** (0x14) Day är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="fd8ab-1508">**FX_INVALID_HOUR** (0x15) Timme är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="fd8ab-1509">**FX_INVALID_MINUTE** (0x16) Minut är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="fd8ab-1510">**FX_INVALID_SECOND** (0x17) Sekund är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1511">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1511">Allowed From</span></span>

<span data-ttu-id="fd8ab-1512">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1513">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1514">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1514">See Also</span></span>

- <span data-ttu-id="fd8ab-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1515">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1519">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1520">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1521">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1528">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1529">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1531">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1532">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1533">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1535">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="fd8ab-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="fd8ab-1542">Tar bort fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1542">Deletes file</span></span>

<span data-ttu-id="fd8ab-1543">Filborttagning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1544">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1545">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1545">Description</span></span>

<span data-ttu-id="fd8ab-1546">Den här tjänsten tar bort den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1547">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1547">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1548">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-1549">**file_name:** Pekare till namnet på filen som ska tas bort (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1550">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1550">Return Values</span></span>

- <span data-ttu-id="fd8ab-1551">**FX_SUCCESS** (0x00) Borttagningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="fd8ab-1552">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-1553">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="fd8ab-1554">**FX_NOT_A_FILE** (0x05) Det angivna filnamnet var en katalog eller volym.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="fd8ab-1555">**FX_ACCESS_ERROR** (0x06) Angiven fil är öppen för tillfället.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="fd8ab-1556">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1557">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1558">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1559">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1560">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1561">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1562">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1563">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-1564">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-1565">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1566">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1566">Allowed From</span></span>

<span data-ttu-id="fd8ab-1567">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1568">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1569">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1569">See Also</span></span>

- <span data-ttu-id="fd8ab-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1570">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1574">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1575">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1583">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1584">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1586">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1587">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1588">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1590">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="fd8ab-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="fd8ab-1597">Allokerar utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1598">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1599">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1599">Description</span></span>

<span data-ttu-id="fd8ab-1600">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="fd8ab-1601">FileX fastställer antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="fd8ab-1602">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="fd8ab-1603">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="fd8ab-1604">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan allokera utrymme i förväg över 4 GB. </span><span class="sxs-lookup"><span data-stu-id="fd8ab-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1605">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1605">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1606">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-1607">**size**: Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1608">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1608">Return Values</span></span>

- <span data-ttu-id="fd8ab-1609">**FX_SUCCESS** (0x00) Lyckad filallokering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="fd8ab-1610">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-1611">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-1612">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="fd8ab-1613">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1614">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1615">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1616">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1617">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1618">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1619">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-1620">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1621">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1621">Allowed From</span></span>

<span data-ttu-id="fd8ab-1622">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1623">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1624">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1624">See Also</span></span>

- <span data-ttu-id="fd8ab-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1625">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1629">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1630">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1632">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1638">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1639">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1641">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1642">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1643">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1645">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="fd8ab-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="fd8ab-1652">Bästa möjliga tid för att allokera utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1653">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1654">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1654">Description</span></span>

<span data-ttu-id="fd8ab-1655">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="fd8ab-1656">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="fd8ab-1657">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="fd8ab-1658">Om det inte finns tillräckligt många kluster i följd tillgängliga på mediet länkar den här tjänsten det största tillgängliga blocket med kluster i följd till filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="fd8ab-1659">Mängden utrymme som faktiskt allokeras till filen returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="fd8ab-1660">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="fd8ab-1661">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan allokera utrymme i förväg över 4 GB. </span><span class="sxs-lookup"><span data-stu-id="fd8ab-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1662">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1662">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1663">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-1664">**storlek:** Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1665">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1665">Return Values</span></span>

- <span data-ttu-id="fd8ab-1666">**FX_SUCCESS** (0x00) Lyckad filallokering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="fd8ab-1667">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-1668">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-1669">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="fd8ab-1670">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1671">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1672">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1673">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1674">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1675">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1676">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-1677">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1678">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1678">Allowed From</span></span>

<span data-ttu-id="fd8ab-1679">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1680">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1680">Example</span></span>

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1681">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1681">See Also</span></span>

- <span data-ttu-id="fd8ab-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1682">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1686">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1687">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1689">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1695">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1696">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1698">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1699">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1700">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1702">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="fd8ab-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="fd8ab-1709">Positioner till en relativ byteförskjutning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1710">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1711">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1711">Description</span></span>

<span data-ttu-id="fd8ab-1712">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna relativa byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="fd8ab-1713">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="fd8ab-1714">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="fd8ab-1715">Parametern *byte_offset* tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan flytta läs-/skrivpekaren över 4 GB.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-1716">*Om sökåtgärden försöker att söka förbi slutet av filen placeras filens läs-/skriv pekare i slutet av filen. Om sökåtgärden försöker placera sig förbi början av filen placeras däremot filens läs-/skriv pekare i början av filen.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1717">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1717">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1718">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-1719">**byte_offset:** Önskad relativ byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="fd8ab-1720">**seek_from:** Riktningen och platsen för var du ska utföra det relativa söket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="fd8ab-1721">Giltiga sökalternativ definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="fd8ab-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="fd8ab-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="fd8ab-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="fd8ab-1725">FX_SEEK_BACK (0x03) FX_SEEK_BEGIN har angetts utförs sökåtgärden från början av filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="fd8ab-1726">Om FX_SEEK_END har angetts utförs sökåtgärden bakåt från slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="fd8ab-1727">Om FX_SEEK_FORWARD har angetts utförs sökåtgärden framåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="fd8ab-1728">Om FX_SEEK_BACK har angetts utförs sökåtgärden bakåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1729">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1729">Return Values</span></span>

- <span data-ttu-id="fd8ab-1730">**FX_SUCCESS** (0x00) Lyckad relativ filsökning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="fd8ab-1731">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-1732">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1733">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1734">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1735">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1736">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-1737">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1738">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1738">Allowed From</span></span>

<span data-ttu-id="fd8ab-1739">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1740">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1741">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1741">See Also</span></span>

- <span data-ttu-id="fd8ab-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1742">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1746">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1747">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1749">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1755">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1756">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1758">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1759">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1760">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1762">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="fd8ab-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="fd8ab-1769">Positioner för byteförskjutning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1770">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1771">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1771">Description</span></span>

<span data-ttu-id="fd8ab-1772">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="fd8ab-1773">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="fd8ab-1774">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="fd8ab-1775">Parametern *byte_offset* ett 64-bitars heltalsvärde, vilket gör att anroparen kan flytta läs-/skriv pekaren över 4 GB.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1776">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1776">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1777">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-1778">**byte_offset:** Önskad byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="fd8ab-1779">Värdet noll placerar pekaren för läsning/skrivning i början av filen, medan ett värde som är större än filens storlek placerar pekaren för läsning/skrivning i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1780">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1780">Return Values</span></span>

- <span data-ttu-id="fd8ab-1781">**FX_SUCCESS** (0x00) Lyckad filsökning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="fd8ab-1782">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="fd8ab-1783">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1784">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1785">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1786">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1787">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-1788">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1789">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1789">Allowed From</span></span>

<span data-ttu-id="fd8ab-1790">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1791">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1792">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1792">See Also</span></span>

- <span data-ttu-id="fd8ab-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1793">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1797">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1798">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1800">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1806">fx_file_open– fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1808">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1809">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1810">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1812">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="fd8ab-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="fd8ab-1819">Trunkerar filen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1820">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1821">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1821">Description</span></span>

<span data-ttu-id="fd8ab-1822">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="fd8ab-1823">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="fd8ab-1824">Inget av de mediekluster som är associerade med filen släpps.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-1825">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Att trunkera en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="fd8ab-1826">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="fd8ab-1827">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta längre än 4 GB. </span><span class="sxs-lookup"><span data-stu-id="fd8ab-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1828">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1828">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1829">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-1830">**size**: Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1830">**size**: New file size.</span></span> <span data-ttu-id="fd8ab-1831">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1832">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1832">Return Values</span></span>

- <span data-ttu-id="fd8ab-1833">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="fd8ab-1834">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="fd8ab-1835">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-1836">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1837">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1838">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1839">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1840">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1841">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1842">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-1843">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1844">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1844">Allowed From</span></span>

<span data-ttu-id="fd8ab-1845">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1846">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1847">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1847">See Also</span></span>

- <span data-ttu-id="fd8ab-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1848">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1852">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1853">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1855">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1861">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1862">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1864">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1865">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1866">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1868">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="fd8ab-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="fd8ab-1875">Trunkerar fil- och versionskluster</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1876">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="fd8ab-1877">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1877">Description</span></span>

<span data-ttu-id="fd8ab-1878">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="fd8ab-1879">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="fd8ab-1880">Till skillnad ***fx_file_extended_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-1881">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="fd8ab-1882">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="fd8ab-1883">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta utanför 4 GB intervall. </span><span class="sxs-lookup"><span data-stu-id="fd8ab-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1884">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1884">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1885">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-1886">**storlek:** Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1886">**size**: New file size.</span></span> <span data-ttu-id="fd8ab-1887">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1888">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1888">Return Values</span></span>

- <span data-ttu-id="fd8ab-1889">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="fd8ab-1890">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-1891">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-1892">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1893">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-1894">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1895">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-1896">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1897">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1898">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1899">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-1900">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1901">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1901">Allowed From</span></span>

<span data-ttu-id="fd8ab-1902">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1903">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1904">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1904">See Also</span></span>

- <span data-ttu-id="fd8ab-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1905">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1909">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1910">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1912">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1918">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1919">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1921">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1922">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1923">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1925">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="fd8ab-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1931">fx_file_open</span></span>

<span data-ttu-id="fd8ab-1932">Öppnar filen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1933">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1934">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1934">Description</span></span>

<span data-ttu-id="fd8ab-1935">Den här tjänsten öppnar den angivna filen för läsning eller skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="fd8ab-1936">En fil kan öppnas för läsning flera gånger, medan en fil bara kan öppnas för skrivning en gång tills skrivaren stänger filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-1937">*Var försiktig om en fil är öppen samtidigt för läsning och skrivning. Filskrivning som utförs när en fil öppnas samtidigt för läsning kanske inte kan ses av läsaren, såvida inte läsaren stänger och öppnar filen igen för läsning. På samma sätt bör filskrivaren vara försiktig när du använder tjänster för trunkering av filer. Om en fil trunkeras av skrivaren kan läsare av samma fil returnera ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-1938">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1938">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-1939">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-1940">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-1941">**file_name:** Pekare till namnet på filen som ska öppnas (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="fd8ab-1942">**open_type:** Typ av fil som är öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="fd8ab-1943">Giltiga alternativ för öppen typ är:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="fd8ab-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="fd8ab-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="fd8ab-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="fd8ab-1947">Att öppna filer med FX_OPEN_FOR_READ och FX_OPEN_FOR_READ_FAST liknar följande:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="fd8ab-1948">FX_OPEN_FOR_READ verifiering att den länkade listan över kluster som utgör filen är intakt och FX_OPEN_FOR_READ_FAST utför inte den här verifieringen, vilket gör den snabbare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-1949">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1949">Return Values</span></span>

- <span data-ttu-id="fd8ab-1950">**FX_SUCCESS** (0x00) Filen lyckades öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="fd8ab-1951">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-1952">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="fd8ab-1953">**FX_NOT_A_FILE** (0x05) Det angivna filnamnet var en katalog eller volym.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="fd8ab-1954">**FX_FILE_CORRUPT** (0x08) Angiven fil är skadad och det gick inte att öppna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="fd8ab-1955">**FX_ACCESS_ERROR** (0x06) Angiven fil är redan öppen eller öppen typ är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="fd8ab-1956">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-1957">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="fd8ab-1958">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-1959">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-1960">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-1961">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="fd8ab-1962">**FX_PTR_ERROR** (0x18) Ogiltig media- eller fil pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="fd8ab-1963">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-1964">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1964">Allowed From</span></span>

<span data-ttu-id="fd8ab-1965">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-1966">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-1967">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1967">See Also</span></span>

- <span data-ttu-id="fd8ab-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1968">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1972">fx_file_close– fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="fd8ab-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1974">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1981">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1983">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1984">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1985">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1987">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="fd8ab-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1993">fx_file_read</span></span>

<span data-ttu-id="fd8ab-1994">Läser byte från fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-1995">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="fd8ab-1996">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1996">Description</span></span>

<span data-ttu-id="fd8ab-1997">Den här tjänsten läser byte från filen och lagrar dem i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="fd8ab-1998">När läsningen är klar justeras filens interna läs pekare så att den pekar på nästa byte i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="fd8ab-1999">Om det finns färre byte kvar i begäran lagras bara återstående byte i bufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="fd8ab-2000">I vilket fall som helst returneras det totala antalet byte som placerats i bufferten till anroparen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2001">*Programmet måste se till att den angivna bufferten kan lagra det angivna antalet begärda byte.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2002">*Snabbare prestanda uppnås om målbufferten ligger på en lång ordgräns och den begärda storleken är jämnt delbar efter sizeof(\*\*ULONG).*\*\*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2003">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2003">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2004">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-2005">**buffer_ptr:** Pekare till målbufferten för läsningen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="fd8ab-2006">**request_size:** Maximalt antal byte som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="fd8ab-2007">**actual_size:** Pekare till variabeln för det faktiska antalet byte som lästs in i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2008">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2008">Return Values</span></span>

- <span data-ttu-id="fd8ab-2009">**FX_SUCCESS** (0x00) Lyckad filläsning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="fd8ab-2010">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="fd8ab-2011">**FX_FILE_CORRUPT** (0x08) Angiven fil är skadad och läsningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="fd8ab-2012">**FX_END_OF_FILE** (0x09) Slutet av filen har nåtts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="fd8ab-2013">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2014">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-2015">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2016">**FX_PTR_ERROR** (0x18) Ogiltig fil- eller buffertpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="fd8ab-2017">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2018">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2018">Allowed From</span></span>

<span data-ttu-id="fd8ab-2019">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2020">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2020">Example</span></span>

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a><span data-ttu-id="fd8ab-2021">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2021">See Also</span></span>

- <span data-ttu-id="fd8ab-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="fd8ab-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="fd8ab-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="fd8ab-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="fd8ab-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2026">fx_file_close,</span></span>
- <span data-ttu-id="fd8ab-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2027">fx_file_create,</span></span>
- <span data-ttu-id="fd8ab-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="fd8ab-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2029">fx_file_delete,</span></span>
- <span data-ttu-id="fd8ab-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="fd8ab-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="fd8ab-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="fd8ab-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="fd8ab-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="fd8ab-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="fd8ab-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2036">fx_file_open,</span></span>
- <span data-ttu-id="fd8ab-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="fd8ab-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2038">fx_file_rename,</span></span>
- <span data-ttu-id="fd8ab-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2039">fx_file_seek,</span></span>
- <span data-ttu-id="fd8ab-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="fd8ab-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="fd8ab-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2042">fx_file_write,</span></span>
- <span data-ttu-id="fd8ab-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="fd8ab-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="fd8ab-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="fd8ab-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="fd8ab-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="fd8ab-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="fd8ab-2049">Positioner till en relativ byteförskjutning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2050">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2051">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2051">Description</span></span>

<span data-ttu-id="fd8ab-2052">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna relativa byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="fd8ab-2053">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-2054">*Om sökåtgärden försöker att söka förbi slutet av filen placeras filens läs-/skriv pekare i slutet av filen. Om sökåtgärden försöker placera sig förbi början av filen placeras däremot filens läs-/skriv pekare i början av filen.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="fd8ab-2055">Om du vill söka med ett förskjutningsvärde över 4 GB ska programmet använda tjänsten *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2056">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2056">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2057">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-2058">**byte_offset:** Önskad relativ byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="fd8ab-2059">**seek_from:** Riktningen och platsen för var du ska utföra det relativa söket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="fd8ab-2060">Giltiga sökalternativ definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="fd8ab-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="fd8ab-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="fd8ab-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="fd8ab-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="fd8ab-2065">Om FX_SEEK_BEGIN har angetts utförs sökåtgärden från början av filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="fd8ab-2066">Om FX_SEEK_END har angetts utförs sökåtgärden bakåt från slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="fd8ab-2067">Om FX_SEEK_FORWARD har angetts utförs sökåtgärden framåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="fd8ab-2068">Om FX_SEEK_BACK har angetts utförs sökåtgärden bakåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2069">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2069">Return Values</span></span>

- <span data-ttu-id="fd8ab-2070">**FX_SUCCESS** (0x00) Lyckad relativ filsökning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="fd8ab-2071">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-2072">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2073">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2074">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2075">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-2076">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-2077">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2078">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2078">Allowed From</span></span>

<span data-ttu-id="fd8ab-2079">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2080">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2081">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2081">See Also</span></span>

- <span data-ttu-id="fd8ab-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2082">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2086">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2087">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2089">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2096">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2097">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2098">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2099">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2100">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2102">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="fd8ab-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2108">fx_file_rename</span></span>

<span data-ttu-id="fd8ab-2109">Byter namn på filen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2110">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2111">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2111">Description</span></span>

<span data-ttu-id="fd8ab-2112">Den här tjänsten ändrar namnet på filen som anges av *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="fd8ab-2113">Namnbyte görs också i förhållande till den angivna sökvägen eller standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="fd8ab-2114">Om en sökväg anges i det nya filnamnet flyttas den omdöpta filen effektivt till den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="fd8ab-2115">Om ingen sökväg anges placeras den omdöpta filen i den aktuella standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2116">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2116">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2117">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="fd8ab-2118">**old_file_name:** Pekare till namnet på filen som du vill byta namn på (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="fd8ab-2119">**new_file_name**: Pekare till det nya filnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="fd8ab-2120">Katalogsökvägen tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2121">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2121">Return Values</span></span>

- <span data-ttu-id="fd8ab-2122">**FX_SUCCESS** (0x00) Namnbyte av fil.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="fd8ab-2123">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2124">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="fd8ab-2125">**FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="fd8ab-2126">**FX_ACCESS_ERROR** (0x06) Den angivna filen är redan öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="fd8ab-2127">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2128">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-2129">**FX_INVALID_NAME** (0x0C) Angivet nytt filnamn är inte ett giltigt filnamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="fd8ab-2130">**FX_INVALID_PATH** (0x0D) Sökvägen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="fd8ab-2131">**FX_ALREADY_CREATED** (0x0B) Det nya filnamnet används.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="fd8ab-2132">**FX_MEDIA_INVALID** (0x02) Media är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="fd8ab-2133">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2134">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2135">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-2136">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-2137">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="fd8ab-2138">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-2139">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2140">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2140">Allowed From</span></span>

<span data-ttu-id="fd8ab-2141">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2142">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2143">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2143">See Also</span></span>

- <span data-ttu-id="fd8ab-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2144">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2148">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2149">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2151">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2158">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2159">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2161">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2162">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2164">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="fd8ab-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2170">fx_file_seek</span></span>

<span data-ttu-id="fd8ab-2171">Positioner för byteförskjutning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2172">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2173">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2173">Description</span></span>

<span data-ttu-id="fd8ab-2174">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="fd8ab-2175">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="fd8ab-2176">Om du vill söka med ett förskjutningsvärde över 4 GB ska programmet använda *tjänsten fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2177">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2177">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2178">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-2179">**byte_offset:** Önskad byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="fd8ab-2180">Värdet noll placerar pekaren för läsning/skrivning i början av filen, medan ett värde som är större än filens storlek placerar pekaren för läsning/skrivning i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2181">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2181">Return Values</span></span>

- <span data-ttu-id="fd8ab-2182">**FX_SUCCESS** (0x00) Lyckad filsökning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="fd8ab-2183">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="fd8ab-2184">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2185">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2186">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2187">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-2188">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-2189">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2190">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2190">Allowed From</span></span>

<span data-ttu-id="fd8ab-2191">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2192">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2193">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2193">See Also</span></span>

- <span data-ttu-id="fd8ab-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2194">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2198">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2199">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2201">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2208">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2209">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2210">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2211">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2212">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2214">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="fd8ab-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2220">fx_file_truncate</span></span>

<span data-ttu-id="fd8ab-2221">Trunkerar filen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2222">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="fd8ab-2223">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2223">Description</span></span>

<span data-ttu-id="fd8ab-2224">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="fd8ab-2225">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="fd8ab-2226">Inget av de mediekluster som är associerade med filen släpps.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2227">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="fd8ab-2228">För att kunna arbeta mer än 4 GB ska programmet använda tjänsten *fx_file_extended_truncate*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2229">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2229">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2230">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-2231">**storlek:** Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2231">**size**: New file size.</span></span> <span data-ttu-id="fd8ab-2232">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2233">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2233">Return Values</span></span>

- <span data-ttu-id="fd8ab-2234">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="fd8ab-2235">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="fd8ab-2236">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-2237">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2238">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-2239">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2240">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2241">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-2242">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="fd8ab-2243">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-2244">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2245">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2245">Allowed From</span></span>

<span data-ttu-id="fd8ab-2246">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2247">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2248">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2248">See Also</span></span>

- <span data-ttu-id="fd8ab-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2249">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2253">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2254">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2256">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2263">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2264">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2266">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2267">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2269">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="fd8ab-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="fd8ab-2276">Trunkerar fil- och versionskluster</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2277">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2278">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2278">Description</span></span>

<span data-ttu-id="fd8ab-2279">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="fd8ab-2280">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="fd8ab-2281">Till skillnad ***fx_file_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2282">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="fd8ab-2283">För att kunna arbeta mer än 4 GB ska programmet använda tjänsten *fx_file_extended_truncate_release*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2284">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2284">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2285">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="fd8ab-2286">**storlek:** Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2286">**size**: New file size.</span></span> <span data-ttu-id="fd8ab-2287">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2288">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2288">Return Values</span></span>

- <span data-ttu-id="fd8ab-2289">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="fd8ab-2290">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-2291">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="fd8ab-2292">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2293">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="fd8ab-2294">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2295">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2296">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-2297">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-2298">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="fd8ab-2299">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="fd8ab-2300">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2301">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2301">Allowed From</span></span>

<span data-ttu-id="fd8ab-2302">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2303">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="fd8ab-2304">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2304">See Also</span></span>

- <span data-ttu-id="fd8ab-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2305">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2309">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2310">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2312">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2319">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2320">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2322">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2323">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2324">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2325">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="fd8ab-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2331">fx_file_write</span></span>

<span data-ttu-id="fd8ab-2332">Skriver byte till fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2334">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2334">Description</span></span>

<span data-ttu-id="fd8ab-2335">Den här tjänsten skriver byte från den angivna bufferten med början vid filens aktuella position.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="fd8ab-2336">När skriven är klar justeras filens interna läs pekare så att den pekar på nästa byte i filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2337">*Snabbare prestanda uppnås om källbufferten finns på en lång ordgräns och den begärda storleken är jämnt delbar efter sizeof(\*\*ULONG).*\*\*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2338">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2338">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2339">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-2340">**buffer_ptr:** Pekare till källbufferten för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="fd8ab-2341">**size**: Antal byte som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2342">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2342">Return Values</span></span>

- <span data-ttu-id="fd8ab-2343">**FX_SUCCESS** (0x00) Lyckad filskrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="fd8ab-2344">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="fd8ab-2345">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="fd8ab-2346">**FX_NO_MORE_SPACE** (0x0A) Det finns inte mer utrymme tillgängligt på mediet för att utföra den här skriven.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="fd8ab-2347">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2348">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-2349">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2350">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2351">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="fd8ab-2352">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="fd8ab-2353">**FX_PTR_ERROR** (0x18) Ogiltig fil eller buffertpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="fd8ab-2354">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2355">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2355">Allowed From</span></span>

<span data-ttu-id="fd8ab-2356">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2357">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2358">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2358">See Also</span></span>

- <span data-ttu-id="fd8ab-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="fd8ab-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="fd8ab-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="fd8ab-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="fd8ab-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2363">fx_file_close,</span></span>
- <span data-ttu-id="fd8ab-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2364">fx_file_create,</span></span>
- <span data-ttu-id="fd8ab-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="fd8ab-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2366">fx_file_delete,</span></span>
- <span data-ttu-id="fd8ab-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="fd8ab-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="fd8ab-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="fd8ab-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="fd8ab-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="fd8ab-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="fd8ab-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2373">fx_file_open,</span></span>
- <span data-ttu-id="fd8ab-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2374">fx_file_read,</span></span>
- <span data-ttu-id="fd8ab-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="fd8ab-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2376">fx_file_rename,</span></span>
- <span data-ttu-id="fd8ab-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2377">fx_file_seek,</span></span>
- <span data-ttu-id="fd8ab-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="fd8ab-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="fd8ab-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="fd8ab-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="fd8ab-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="fd8ab-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="fd8ab-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="fd8ab-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="fd8ab-2386">Anger funktionen för att meddela om filskrivning</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2387">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="fd8ab-2388">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2388">Description</span></span>

<span data-ttu-id="fd8ab-2389">Den här tjänsten installerar återanropsfunktionen som anropas efter en lyckad filskrivningsåtgärd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2390">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2390">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2391">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="fd8ab-2392">**file_write_notify:** Återanropsfunktionen för filskrivning som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="fd8ab-2393">Om du ställer in återanropsfunktionen på NULL inaktiveras återanropsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2394">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2394">Return Values</span></span>

- <span data-ttu-id="fd8ab-2395">**FX_SUCCESS** (0x00) Återanropsfunktionen har installerats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="fd8ab-2396">**FX_PTR_ERROR** (0x18) file_ptr är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="fd8ab-2397">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2398">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2398">Allowed From</span></span>

<span data-ttu-id="fd8ab-2399">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2400">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2401">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2401">See Also</span></span>

- <span data-ttu-id="fd8ab-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2402">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2406">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2407">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2409">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2416">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2417">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2419">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2420">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2421">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2423">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="fd8ab-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2428">fx_media_abort</span></span>

<span data-ttu-id="fd8ab-2429">Avbryter medieaktiviteter</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2430">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2431">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2431">Description</span></span>

<span data-ttu-id="fd8ab-2432">Den här tjänsten avbryter alla aktuella aktiviteter som är associerade med mediet, inklusive att stänga alla öppna filer, skicka en begäran om avbrott till den associerade drivrutinen och placera mediet i ett avbrutna tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="fd8ab-2433">Den här tjänsten anropas vanligtvis när I/O-fel identifieras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2434">*Mediet måste öppnas igen för att det ska kunna användas igen när en avbrottsåtgärd har utförts.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2435">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2435">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2436">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2437">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2437">Return Values</span></span>

- <span data-ttu-id="fd8ab-2438">**FX_SUCCESS** (0x00) Lyckad medie abort.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="fd8ab-2439">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2440">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-2441">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2442">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2442">Allowed From</span></span>

<span data-ttu-id="fd8ab-2443">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2444">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2445">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2445">See Also</span></span>

- <span data-ttu-id="fd8ab-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2448">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2449">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2453">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2454">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2455">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2457">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2458">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2461">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="fd8ab-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="fd8ab-2464">Ogiltigförklarar cache för logisk sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2465">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="fd8ab-2466">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2466">Description</span></span>

<span data-ttu-id="fd8ab-2467">Den här tjänsten rensar alla felaktiga sektorer i cacheminnet och ogiltigförklarar sedan hela cacheminnet för den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2468">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2468">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2469">**media_ptr:** Pekare till mediakontrollblock</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2470">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2470">Return Values</span></span>

- <span data-ttu-id="fd8ab-2471">**FX_SUCCESS** (0x00) Lyckad mediecache ogiltigförklaras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="fd8ab-2472">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2473">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2474">**FX_PTR_ERROR** (0x18) Ogiltig media eller scratch pointer.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="fd8ab-2475">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2476">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2476">Allowed From</span></span>

<span data-ttu-id="fd8ab-2477">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2478">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2479">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2479">See Also</span></span>

- <span data-ttu-id="fd8ab-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2481">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2482">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2483">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2487">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2488">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2489">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2491">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2492">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2495">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="fd8ab-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2497">fx_media_check</span></span>

<span data-ttu-id="fd8ab-2498">Söker efter fel i media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2499">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2500">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2500">Description</span></span>

<span data-ttu-id="fd8ab-2501">Den här tjänsten söker efter grundläggande strukturella fel på de angivna mediet, inklusive fil-/kataloglänkning, ogiltiga FAT-kedjor och förlorade kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="fd8ab-2502">Den här tjänsten ger också möjlighet att korrigera identifierade fel.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="fd8ab-2503">Tjänsten fx_media_check minne för djupanalys av kataloger och filer på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="fd8ab-2504">Mer specifikt måste det scratch-minne som tillhandahålls till mediakontrolltjänsten vara tillräckligt stort för att rymma flera katalogposter, en datastruktur för att "stapla" den aktuella katalogpostpositionen innan du anger i underkataloger och slutligen den logiska FAT-bitmappningen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="fd8ab-2505">Det scratch-minnet ska vara minst 512–1 024 byte plus minne för den logiska FAT-bitkartan, vilket kräver lika många bitar som det finns kluster på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="fd8ab-2506">Till exempel skulle en enhet med 8 000 kluster kräva 1 000 byte för att representera och därmed kräva en total scratch area på en beställning på 2 048 byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2507">*Den här tjänsten bör bara anropas omedelbart efter fx_media_open och utan någon annan filsystemaktivitet.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2508">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2508">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2509">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-2510">**scratch_memory_ptr:** Pekare till början av det scratch-minnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="fd8ab-2511">**scratch_memory_size:** Storleken på det scratch-minnet i byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="fd8ab-2512">**error_correction_option:** Bitar för felkorrigeringsalternativ när biten har angetts utförs felkorrigering.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="fd8ab-2513">Bitarna för felkorrigeringsalternativet definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="fd8ab-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="fd8ab-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="fd8ab-2516">FX_LOST_CLUSTER_ERROR (0x04) Helt enkelt ELLER ihop de alternativ för felkorrigering som krävs.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="fd8ab-2517">Om ingen felkorrigering krävs ska värdet 0 anges.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="fd8ab-2518">**errors_detected_ptr:** Mål för felidentifierings bitar enligt definitionen nedan:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="fd8ab-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="fd8ab-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="fd8ab-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2522">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2522">Return Values</span></span>

- <span data-ttu-id="fd8ab-2523">**FX_SUCCESS** (0x00) Lyckad mediekontroll visar du de fel som identifierats för mer information.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="fd8ab-2524">**FX_ACCESS_ERROR** (0x06) Det går inte att kontrollera med öppna filer.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="fd8ab-2525">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2526">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2527">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="fd8ab-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Det angivna minnet är inte tillräckligt stort.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="fd8ab-2529">**FX_ERROR_NOT_FIXED** (0x93) Fel i FAT32-rotkatalogen som inte kunde åtgärdas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="fd8ab-2530">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2531">**FX_SECTOR_INVALID** (0x89) Sektor är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="fd8ab-2532">**FX_PTR_ERROR** (0x18) Ogiltig media eller scratch pointer.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="fd8ab-2533">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2534">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2534">Allowed From</span></span>

<span data-ttu-id="fd8ab-2535">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2536">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2536">Example</span></span>

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2537">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2537">See Also</span></span>

- <span data-ttu-id="fd8ab-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2539">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2541">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2545">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2546">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2547">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2549">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2550">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2553">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="fd8ab-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2555">fx_media_close</span></span>

<span data-ttu-id="fd8ab-2556">Stänger media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2557">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2558">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2558">Description</span></span>

<span data-ttu-id="fd8ab-2559">Den här tjänsten stänger det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2559">This service closes the specified media.</span></span> <span data-ttu-id="fd8ab-2560">När mediet stängs stängs alla öppna filer och eventuella återstående buffertar rensas till det fysiska mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2561">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2561">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2562">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2563">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2563">Return Values</span></span>

- <span data-ttu-id="fd8ab-2564">**FX_SUCCESS** (0x00) Lyckad media stäng.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="fd8ab-2565">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2566">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2567">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-2568">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2569">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2569">Allowed From</span></span>

<span data-ttu-id="fd8ab-2570">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2571">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2572">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2572">See Also</span></span>

- <span data-ttu-id="fd8ab-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2574">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2576">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2580">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2581">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2582">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2584">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2585">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2588">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="fd8ab-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="fd8ab-2591">Anger funktionen media close notify</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2592">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="fd8ab-2593">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2593">Description</span></span>

<span data-ttu-id="fd8ab-2594">Den här tjänsten anger en avanropsfunktion som anropas när ett medium har stängts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2595">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2595">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2596">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-2597">**media_close_notify: Media** close notify callback function to be installed.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="fd8ab-2598">Genom att skicka NULL som återanropsfunktion inaktiveras återanropet av media close.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2599">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2599">Return Values</span></span>

- <span data-ttu-id="fd8ab-2600">**FX_SUCCESS** (0x00) Återanropsfunktionen har installerats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="fd8ab-2601">**FX_PTR_ERROR** (0x18) media_ptr är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="fd8ab-2602">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2603">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2603">Allowed From</span></span>

<span data-ttu-id="fd8ab-2604">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2605">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="fd8ab-2606">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2606">See Also</span></span>

- <span data-ttu-id="fd8ab-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2608">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2610">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2611">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2614">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2615">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2616">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2618">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2619">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2622">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="fd8ab-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="fd8ab-2625">Formaterar media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2626">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2626">Prototype</span></span>

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2627">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2627">Description</span></span>

<span data-ttu-id="fd8ab-2628">Den här tjänsten formaterar det angivna mediet på ett exFAT-kompatibelt sätt baserat på de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="fd8ab-2629">Den här tjänsten måste anropas innan mediet öppnas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2630">*Om du formaterar ett redan formaterat medium raderas effektivt alla filer och kataloger på mediet.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-2631">*ExFAT-volymstorleken ska matcha storleken på partitionen (om det finns en MBR- eller GPT-layout) eller storleken på hela enheten om det inte finns någon partitionslayout (ingen MBR eller GPT). Det finns en begränsning för Windows som exFAT Disk inte kommer att recoginzed om formateras med vissa värden för totala sektorer som är mindre än medelvärden sektorer*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2631">*The exFAT volume size should match the size of the partition (if there is an MBR or GPT layout), or the size of the whole device if there is no partition layout (no MBR or GPT). There is a limitation on Windows that exFAT Disk will not be recoginzed if formatted with some values of total sectors that are less than avialble sectors*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2632">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2632">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2633">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2633">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="fd8ab-2634">Detta används endast för att tillhandahålla viss grundläggande information som krävs för att drivrutinen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2634">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="fd8ab-2635">**driver**: Pekare till I/O-drivrutinen för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2635">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="fd8ab-2636">Detta är vanligtvis samma drivrutin som angavs för efterföljande fx_media_open anropet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2636">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="fd8ab-2637">**driver_info_ptr:** Pekare till valfri information som I/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2637">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="fd8ab-2638">**memory_ptr:** Pekare till arbetsminnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2638">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="fd8ab-2639">memory_size Anger storleken på arbetsmediaminnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2639">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="fd8ab-2640">Storleken måste vara minst lika stor som mediets sektorstorlek.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2640">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="fd8ab-2641">**volume_name:** Pekare till volymnamnssträngen, som är högst 11 tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2641">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="fd8ab-2642">**number_of_fats:** Antal vanliga frågor och svar på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2642">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="fd8ab-2643">Den aktuella implementeringen stöder en FAT på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2643">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="fd8ab-2644">**hidden_sectors:** Antalet sektorer som är dolda före det här mediets startsektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2644">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="fd8ab-2645">Detta är vanligt när det finns flera partitioner.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2645">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="fd8ab-2646">**total_sectors:** Totalt antal sektorer i mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2646">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="fd8ab-2647">**bytes_per_sector:** Antal byte per sektor, vilket vanligtvis är 512.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2647">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="fd8ab-2648">FileX kräver att detta är en multipel av 32.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2648">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="fd8ab-2649">**sectors_per_cluster:** Antalet sektorer i varje kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2649">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="fd8ab-2650">Klustret är den minsta allokeringsenheten i ett FAT-filsystem.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2650">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="fd8ab-2651">**volumne_serial_number:** Serienummer som ska användas för den här volymen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2651">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="fd8ab-2652">**boundary_unit:** Justeringsstorlek för fysiskt dataområde i antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2652">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2653">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2653">Return Values</span></span>

- <span data-ttu-id="fd8ab-2654">**FX_SUCCESS** (0x00) Medieformatet lyckades.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2654">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="fd8ab-2655">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2655">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2656">**FX_PTR_ERROR** (0x18) Ogiltig media, drivrutin eller minnespekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2656">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="fd8ab-2657">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2657">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2658">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2658">Allowed From</span></span>

<span data-ttu-id="fd8ab-2659">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2659">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2660">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2660">Example</span></span>

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2661">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2661">See Also</span></span>

- <span data-ttu-id="fd8ab-2662">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2662">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2663">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2663">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2664">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2664">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2665">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2665">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2666">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2666">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2667">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2667">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2668">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2668">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2669">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2669">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2670">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2670">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2671">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2671">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2672">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2672">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2673">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2673">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2674">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2674">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2675">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2675">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2676">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2676">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2677">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2677">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2678">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2678">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="fd8ab-2679">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2679">fx_media_extended_space_available</span></span>

<span data-ttu-id="fd8ab-2680">Returnerar tillgängligt medieutrymme</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2680">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2681">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2681">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2682">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2682">Description</span></span>

<span data-ttu-id="fd8ab-2683">Den här tjänsten returnerar antalet tillgängliga byte på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2683">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="fd8ab-2684">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2684">This service is designed for exFAT.</span></span> <span data-ttu-id="fd8ab-2685">Pekaren till *available_bytes* parametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta med medier utanför 4 GB intervall.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2685">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2686">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2686">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2687">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2687">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="fd8ab-2688">**available_bytes_ptr:** Tillgängliga byte kvar på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2688">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2689">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2689">Return Values</span></span>

- <span data-ttu-id="fd8ab-2690">**FX_SUCCESS** (0x00) Tillgängligt utrymme på mediet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2690">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="fd8ab-2691">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2691">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2692">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare eller tillgänglig byte-pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2692">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="fd8ab-2693">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2693">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2694">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2694">Allowed From</span></span>

<span data-ttu-id="fd8ab-2695">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2695">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2696">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2696">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2697">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2697">See Also</span></span>

- <span data-ttu-id="fd8ab-2698">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2698">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2699">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2699">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2700">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2700">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2701">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2701">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2702">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2702">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2703">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2703">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2704">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2704">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2705">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2705">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2706">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2706">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2707">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2707">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2708">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2708">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2709">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2709">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2710">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2710">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2711">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2711">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2712">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2712">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2713">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2713">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2714">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2714">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="fd8ab-2715">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2715">fx_media_flush</span></span>

<span data-ttu-id="fd8ab-2716">Rensar data till fysiska media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2716">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2717">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2717">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2718">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2718">Description</span></span>

<span data-ttu-id="fd8ab-2719">Den här tjänsten rensar alla cachelagrade sektorer och katalogposter för ändrade filer till det fysiska mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2719">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2720">*Den här rutinen kan anropas regelbundet av programmet för att minska risken för skadade filer och/eller dataförlust i händelse av plötslig strömförlust på målet.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2720">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2721">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2721">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2722">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2722">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2723">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2723">Return Values</span></span>

- <span data-ttu-id="fd8ab-2724">**FX_SUCCESS** (0x00) Lyckad medieström.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2724">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="fd8ab-2725">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2725">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2726">**FX_FILE_CORRUPT**    (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2726">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="fd8ab-2727">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2727">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2728">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2728">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2729">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2729">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-2730">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2730">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-2731">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2731">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2732">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2732">Allowed From</span></span>

<span data-ttu-id="fd8ab-2733">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2734">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2734">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2735">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2735">See Also</span></span>

- <span data-ttu-id="fd8ab-2736">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2736">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2737">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2737">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2738">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2738">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2739">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2739">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2740">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2740">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2741">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2741">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2742">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2742">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2743">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2743">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2744">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2744">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2745">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2745">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2746">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2746">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2747">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2747">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2748">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2748">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2749">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2749">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2750">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2750">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2751">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2751">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2752">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2752">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="fd8ab-2753">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2753">fx_media_format</span></span>

<span data-ttu-id="fd8ab-2754">Formaterar media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2754">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2755">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2755">Prototype</span></span>

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2756">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2756">Description</span></span>

<span data-ttu-id="fd8ab-2757">Den här tjänsten formaterar det angivna mediet på ett FAT 12/16/32-kompatibelt sätt baserat på de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2757">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="fd8ab-2758">Den här tjänsten måste anropas innan mediet öppnas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2758">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2759">*Om du formaterar ett redan formaterat medium raderas effektivt alla filer och kataloger på mediet.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2759">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2760">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2760">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2761">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2761">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="fd8ab-2762">Detta används endast för att tillhandahålla viss grundläggande information som krävs för att drivrutinen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2762">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="fd8ab-2763">**driver**: Pekare till I/O-drivrutinen för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2763">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="fd8ab-2764">Detta är vanligtvis samma drivrutin som tillhandahålls till efterföljande fx_media_open anrop.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2764">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="fd8ab-2765">**driver_info_ptr:** Pekare till valfri information som I/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2765">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="fd8ab-2766">**memory_ptr:** Pekare till arbetsminnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2766">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="fd8ab-2767">**memory_size:** Anger storleken på arbetsmediaminnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2767">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="fd8ab-2768">Storleken måste vara minst lika stor som mediets sektorstorlek.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2768">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="fd8ab-2769">**volume_name:** Pekare till volymnamnssträngen, som är högst 11 tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2769">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="fd8ab-2770">**number_of_fats:** Antal vanliga frågor och svar i mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2770">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="fd8ab-2771">Det minimala värdet är 1 för primärt FAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2771">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="fd8ab-2772">Värden som är större än 1 resulterar i att ytterligare FAT-kopior underhålls vid körning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2772">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="fd8ab-2773">**directory_entries:** Antal katalogposter i rotkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2773">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="fd8ab-2774">**hidden_sectors:** Antalet sektorer som är dolda före det här mediets startsektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2774">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="fd8ab-2775">Detta är vanligt när det finns flera partitioner.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2775">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="fd8ab-2776">**total_sectors:** Totalt antal sektorer i mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2776">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="fd8ab-2777">**bytes_per_sector:** Antal byte per sektor, vilket vanligtvis är 512.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2777">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="fd8ab-2778">FileX kräver att detta är en multipel av 32.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2778">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="fd8ab-2779">**sectors_per_cluster:** Antalet sektorer i varje kluster.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2779">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="fd8ab-2780">Klustret är den minsta allokeringsenheten i ett FAT-filsystem.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2780">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="fd8ab-2781">**krona:** Antal fysiska huvuden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2781">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="fd8ab-2782">**sectors_per_track:** Antal sektorer per spår.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2782">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2783">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2783">Return Values</span></span>

- <span data-ttu-id="fd8ab-2784">**FX_SUCCESS** (0x00) Medieformatet lyckades.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2784">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="fd8ab-2785">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2785">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2786">**FX_PTR_ERROR** (0x18) Ogiltig media-, drivrutins- eller minnespekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2786">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="fd8ab-2787">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2787">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2788">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2788">Allowed From</span></span>

<span data-ttu-id="fd8ab-2789">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2790">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2790">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2791">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2791">See Also</span></span>

- <span data-ttu-id="fd8ab-2792">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2792">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2793">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2793">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2794">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2794">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2795">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2795">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2796">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2796">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2797">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2797">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2798">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2798">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2799">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2799">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2800">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2800">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2801">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2801">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2802">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2802">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2803">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2803">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2804">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2804">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2805">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2805">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2806">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2806">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2807">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2807">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2808">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2808">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="fd8ab-2809">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2809">fx_media_open</span></span>

<span data-ttu-id="fd8ab-2810">Öppnar media för filåtkomst</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2810">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2811">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2811">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2812">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2812">Description</span></span>

<span data-ttu-id="fd8ab-2813">Den här tjänsten öppnar ett medium för filåtkomst med hjälp av den angivna I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2813">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-2814">*Det minne som tillhandahålls till den här tjänsten används för att implementera en intern logisk sektorcache, och ju mer minne som tillhandahålls desto mer fysisk I/O minskas. FileX kräver en cache med minst en logisk sektor (byte per sektor av mediet).*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2814">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2815">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2815">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2816">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2816">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-2817">**media_name:** Pekare till mediets namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2817">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="fd8ab-2818">**media_driver:** Pekare till I/O-drivrutin för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2818">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="fd8ab-2819">I/O-drivrutinen måste uppfylla kraven för FileX-drivrutinen som definieras i kapitel 5.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2819">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="fd8ab-2820">**driver_info_ptr:** Pekare till valfri information som den angivna I/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2820">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="fd8ab-2821">**memory_ptr:** Pekare till arbetsminnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2821">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="fd8ab-2822">**memory_size:** Anger storleken på arbetsmediaminnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2822">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="fd8ab-2823">Storleken måste vara lika stor som mediets sektorstorlek (vanligtvis 512 byte).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2823">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2824">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2824">Return Values</span></span>

- <span data-ttu-id="fd8ab-2825">**FX_SUCCESS** (0x00) Lyckad media är öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2825">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="fd8ab-2826">**FX_BOOT_ERROR** (0x01) Fel vid läsning av mediets startsektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2826">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="fd8ab-2827">**FX_MEDIA_INVALID** (0x02) Det angivna mediets startsektor är skadad eller ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2827">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="fd8ab-2828">Dessutom används den här returkoden för att ange att antingen cachestorleken för den logiska sektorn eller FAT-poststorleken inte är 2.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2828">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="fd8ab-2829">**FX_FAT_READ_ERROR** (0x03) Fel vid läsning av mediet FAT.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2829">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="fd8ab-2830">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2830">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2831">**FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2831">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="fd8ab-2832">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2832">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2833">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2833">Allowed From</span></span>

<span data-ttu-id="fd8ab-2834">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2834">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2835">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2835">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2836">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2836">See Also</span></span>

- <span data-ttu-id="fd8ab-2837">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2837">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2838">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2838">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2839">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2839">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2840">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2840">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2841">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2841">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2842">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2842">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2843">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2843">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2844">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2844">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2845">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2845">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2846">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2846">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2847">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2847">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2848">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2848">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2849">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2849">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2850">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2850">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2851">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2851">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2852">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2852">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2853">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2853">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="fd8ab-2854">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2854">fx_media_open_notify_set</span></span>

<span data-ttu-id="fd8ab-2855">Anger media open notify-funktionen</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2855">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2856">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2856">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="fd8ab-2857">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2857">Description</span></span>

<span data-ttu-id="fd8ab-2858">Den här tjänsten anger en avanropsfunktion som anropas när ett medium har öppnats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2858">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2859">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2859">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2860">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2860">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-2861">**media_open_notify:** Funktionen Media open notify callback som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2861">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="fd8ab-2862">Om null-värdet används som återanropsfunktion inaktiveras återanropet från mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2862">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2863">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2863">Return Values</span></span>


- <span data-ttu-id="fd8ab-2864">**FX_SUCCESS** (0x00) Successfuly installerade återanropsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2864">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="fd8ab-2865">**FX_PTR_ERROR** (0x18) media_ptr är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2865">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="fd8ab-2866">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2866">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2867">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2867">Allowed From</span></span>

<span data-ttu-id="fd8ab-2868">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2868">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2869">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2869">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2870">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2870">See Also</span></span>

- <span data-ttu-id="fd8ab-2871">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2871">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2872">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2872">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2873">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2873">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2874">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2874">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2875">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2875">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2876">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2876">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2877">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2877">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2878">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2878">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2879">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2879">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2880">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2880">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2881">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2881">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2882">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2882">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2883">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2883">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2884">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2884">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2885">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2885">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2886">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2886">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2887">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2887">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="fd8ab-2888">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2888">fx_media_read</span></span>

<span data-ttu-id="fd8ab-2889">Läser logisk sektor från media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2889">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2890">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2890">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2891">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2891">Description</span></span>

<span data-ttu-id="fd8ab-2892">Den här tjänsten läser en logisk sektor från mediet och placerar den i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2892">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2893">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2893">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2894">**media_ptr:** Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2894">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="fd8ab-2895">**logical_sector:** Logisk sektor att läsa.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2895">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="fd8ab-2896">**buffer_ptr:** Pekare till målet för den logiska sektorn läsa.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2896">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2897">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2897">Return Values</span></span>

- <span data-ttu-id="fd8ab-2898">**FX_SUCCESS** (0x00) Lyckad medieläsning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2898">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="fd8ab-2899">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2899">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2900">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2900">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2901">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2901">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-2902">**FX_PTR_ERROR** (0x18) Ogiltig media eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2902">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="fd8ab-2903">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2903">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2904">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2904">Allowed From</span></span>

<span data-ttu-id="fd8ab-2905">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2906">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2906">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2907">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2907">See Also</span></span>

- <span data-ttu-id="fd8ab-2908">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2908">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2909">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2909">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2910">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2910">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2911">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2911">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2912">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2912">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2913">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2913">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2914">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2914">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2915">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2915">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2916">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2916">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2917">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2917">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2918">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2918">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2919">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2919">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2920">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2920">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2921">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2921">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2922">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2922">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2923">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2923">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2924">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2924">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="fd8ab-2925">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2925">fx_media_space_available</span></span>

<span data-ttu-id="fd8ab-2926">Returnerar tillgängligt medieutrymme</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2926">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2927">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2927">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="fd8ab-2928">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2928">Description</span></span>

<span data-ttu-id="fd8ab-2929">Den här tjänsten returnerar antalet tillgängliga byte på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2929">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="fd8ab-2930">Om du vill arbeta med media som är större än 4 GB ska programmet använda tjänsten *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2930">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2931">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2931">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2932">**media_ptr:** Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2932">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="fd8ab-2933">**available_bytes_ptr:** Tillgängliga byte kvar på mediet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2933">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2934">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2934">Return Values</span></span>

- <span data-ttu-id="fd8ab-2935">**FX_SUCCESS** (0x00) Tillgängligt utrymme på mediet har returnerats.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2935">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="fd8ab-2936">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2936">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2937">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare eller tillgänglig byte-pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2937">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="fd8ab-2938">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2938">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2939">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2939">Allowed From</span></span>

<span data-ttu-id="fd8ab-2940">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2940">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2941">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2941">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2942">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2942">See Also</span></span>

- <span data-ttu-id="fd8ab-2943">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2943">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2944">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2944">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2945">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2945">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2946">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2946">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2947">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2947">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2948">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2948">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2949">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2949">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2950">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2950">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2951">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2951">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2952">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2952">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2953">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2953">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2954">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2954">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2955">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2955">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2956">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2956">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-2957">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2957">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2958">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2958">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-2959">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2959">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="fd8ab-2960">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2960">fx_media_volume_get</span></span>

<span data-ttu-id="fd8ab-2961">Hämtar medievolymens namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2961">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-2962">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2962">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="fd8ab-2963">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2963">Description</span></span>

<span data-ttu-id="fd8ab-2964">Den här tjänsten hämtar volymnamnet för det media som öppnades tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2964">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-2965">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2965">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-2966">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2966">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-2967">**volume_name:** Pekare till mål för volymnamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2967">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="fd8ab-2968">Observera att målet måste vara minst tillräckligt stort för att innehålla 12 tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2968">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="fd8ab-2969">**volume_source:** Anger var namnet ska hämtas, antingen från startsektorn eller rotkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2969">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="fd8ab-2970">Giltiga värden för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2970">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="fd8ab-2971">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2971">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="fd8ab-2972">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2972">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-2973">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2973">Return Values</span></span>

- <span data-ttu-id="fd8ab-2974">**FX_SUCCESS** (0x00) Lyckad medievolym get.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2974">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="fd8ab-2975">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2975">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-2976">**FX_NOT_FOUND** (0x04)-volymen hittades inte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2976">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="fd8ab-2977">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2977">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-2978">**FX_PTR_ERROR** (0x18) Ogiltig media- eller volymmål pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2978">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="fd8ab-2979">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2979">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-2980">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2980">Allowed From</span></span>

<span data-ttu-id="fd8ab-2981">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2981">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-2982">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2982">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="fd8ab-2983">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2983">See Also</span></span>

- <span data-ttu-id="fd8ab-2984">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2984">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-2985">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2985">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-2986">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2986">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-2987">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2987">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-2988">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2988">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-2989">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2989">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-2990">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2990">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-2991">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2991">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-2992">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2992">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-2993">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2993">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-2994">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2994">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-2995">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2995">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-2996">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2996">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-2997">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2997">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-2998">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2998">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-2999">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-2999">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-3000">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3000">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="fd8ab-3001">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3001">fx_media_volume_get_extended</span></span>

<span data-ttu-id="fd8ab-3002">Hämtar medievolymens namn på tidigare öppnade media</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3002">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3003">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3003">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3004">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3004">Description</span></span>

<span data-ttu-id="fd8ab-3005">Den här tjänsten hämtar volymnamnet för det media som öppnades tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3005">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3006">Den här tjänsten är identisk med \***fx_media_volume_get()** _ förutom att anroparen skickar storleken på *bufferten* _ volume_name \* .</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3006">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3007">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3007">Input Parameters</span></span>


- <span data-ttu-id="fd8ab-3008">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3008">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3009">**volume_name:** Pekare till mål för volymnamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3009">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="fd8ab-3010">Observera att målet måste vara minst tillräckligt stort för att innehålla 12 tecken.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3010">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="fd8ab-3011">**volume_name_buffer_length:** Storleken på volume_name bufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3011">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="fd8ab-3012">**volume_source:** Anger var namnet ska hämtas, antingen från startsektorn eller rotkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3012">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="fd8ab-3013">Giltiga värden för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3013">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="fd8ab-3014">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3014">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="fd8ab-3015">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3015">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3016">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3016">Return Values</span></span>

- <span data-ttu-id="fd8ab-3017">**FX_SUCCESS** (0x00) Lyckad medievolym get.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3017">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="fd8ab-3018">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3018">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3019">**FX_NOT_FOUND** (0x04)-volymen hittades inte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3019">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="fd8ab-3020">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3020">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3021">**FX_PTR_ERROR** (0x18) Ogiltig media- eller volymmål pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3021">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="fd8ab-3022">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3022">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3023">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3023">Allowed From</span></span>

<span data-ttu-id="fd8ab-3024">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3024">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3025">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3025">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3026">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3026">See Also</span></span>

- <span data-ttu-id="fd8ab-3027">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3027">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-3028">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3028">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-3029">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3029">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-3030">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3030">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-3031">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3031">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-3032">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3032">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-3033">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3033">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-3034">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3034">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-3035">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3035">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-3036">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3036">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-3037">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3037">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-3038">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3038">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-3039">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3039">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-3040">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3040">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-3041">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3041">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-3042">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3042">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-3043">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3043">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="fd8ab-3044">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3044">fx_media_volume_set</span></span>

<span data-ttu-id="fd8ab-3045">Anger medievolymnamn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3045">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3046">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3046">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3047">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3047">Description</span></span>

<span data-ttu-id="fd8ab-3048">Den här tjänsten anger volymnamnet för det media som öppnades tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3048">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3049">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3049">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3050">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3050">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3051">**volume_name:** Pekare till volymnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3051">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3052">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3052">Return Values</span></span>

- <span data-ttu-id="fd8ab-3053">**FX_SUCCESS** (0x00) Lyckad medievolymuppsättning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3053">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="fd8ab-3054">**FX_INVALID_NAME** (0x0C) Volume_name är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3054">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="fd8ab-3055">**FX_MEDIA_INVALID** (0x02) Det går inte att ange volymnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3055">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="fd8ab-3056">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3056">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3057">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3057">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3058">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3058">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-3059">**FX_PTR_ERROR** (0x18) Ogiltig media- eller volymnamnspekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3059">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="fd8ab-3060">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3060">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3061">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3061">Allowed From</span></span>

<span data-ttu-id="fd8ab-3062">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3062">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3063">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3063">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3064">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3064">See Also</span></span>

- <span data-ttu-id="fd8ab-3065">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3065">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-3066">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3066">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-3067">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3067">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-3068">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3068">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-3069">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3069">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-3070">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3070">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-3071">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3071">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-3072">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3072">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-3073">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3073">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-3074">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3074">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-3075">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3075">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-3076">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3076">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-3077">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3077">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-3078">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3078">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-3079">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3079">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-3080">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3080">fx_media_write</span></span>
- <span data-ttu-id="fd8ab-3081">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3081">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="fd8ab-3082">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3082">fx_media_write</span></span>

<span data-ttu-id="fd8ab-3083">Skriver logisk sektor</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3083">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3084">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3084">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3085">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3085">Description</span></span>

<span data-ttu-id="fd8ab-3086">Den här tjänsten skriver den angivna bufferten till den angivna logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3086">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3087">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3087">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3088">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3088">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="fd8ab-3089">**logical_sector:** Logisk sektor att skriva.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3089">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="fd8ab-3090">**buffer_ptr:** Pekare till källan för den logiska sektorskrivningen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3090">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3091">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3091">Return Values</span></span>

- <span data-ttu-id="fd8ab-3092">**FX_SUCCESS** (0x00) Lyckad medieskrivning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3092">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="fd8ab-3093">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3093">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3094">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3094">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-3095">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3095">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3096">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3096">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-3097">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3097">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="fd8ab-3098">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3098">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3099">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3099">Allowed From</span></span>

<span data-ttu-id="fd8ab-3100">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3100">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3101">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3101">Example</span></span>

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3102">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3102">See Also</span></span>

- <span data-ttu-id="fd8ab-3103">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3103">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="fd8ab-3104">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3104">fx_media_abort</span></span>
- <span data-ttu-id="fd8ab-3105">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3105">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="fd8ab-3106">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3106">fx_media_check</span></span>
- <span data-ttu-id="fd8ab-3107">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3107">fx_media_close</span></span>
- <span data-ttu-id="fd8ab-3108">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3108">fx_media_close_notify_set</span></span>
- <span data-ttu-id="fd8ab-3109">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3109">fx_media_exFAT_format</span></span>
- <span data-ttu-id="fd8ab-3110">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3110">fx_media_extended_space_available</span></span>
- <span data-ttu-id="fd8ab-3111">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3111">fx_media_flush</span></span>
- <span data-ttu-id="fd8ab-3112">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3112">fx_media_format</span></span>
- <span data-ttu-id="fd8ab-3113">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3113">fx_media_open</span></span>
- <span data-ttu-id="fd8ab-3114">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3114">fx_media_open_notify_set</span></span>
- <span data-ttu-id="fd8ab-3115">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3115">fx_media_read</span></span>
- <span data-ttu-id="fd8ab-3116">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3116">fx_media_space_available</span></span>
- <span data-ttu-id="fd8ab-3117">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3117">fx_media_volume_get</span></span>
- <span data-ttu-id="fd8ab-3118">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3118">fx_media_volume_set</span></span>
- <span data-ttu-id="fd8ab-3119">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3119">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="fd8ab-3120">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3120">fx_system_date_get</span></span>

<span data-ttu-id="fd8ab-3121">Hämtar filsystemdatum</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3121">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3122">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3122">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3123">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3123">Description</span></span>

<span data-ttu-id="fd8ab-3124">Den här tjänsten returnerar det aktuella systemdatumet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3124">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3125">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3125">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3126">**year**: Pekare till mål för år.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3126">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="fd8ab-3127">**month**: Pekare till mål för månad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3127">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="fd8ab-3128">**day**: Pekare till mål för dagen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3128">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3129">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3129">Return Values</span></span>

- <span data-ttu-id="fd8ab-3130">**FX_SUCCESS** (0x00) Lyckad datumhämtning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3130">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="fd8ab-3131">**FX_PTR_ERROR** (0x18) En eller flera av indataparametrarna är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3131">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3132">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3132">Allowed From</span></span>

<span data-ttu-id="fd8ab-3133">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3134">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3134">Example</span></span>

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3135">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3135">See Also</span></span>

- <span data-ttu-id="fd8ab-3136">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3136">fx_system_date_set</span></span>
- <span data-ttu-id="fd8ab-3137">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3137">fx_system_initialize</span></span>
- <span data-ttu-id="fd8ab-3138">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3138">fx_system_time_get</span></span>
- <span data-ttu-id="fd8ab-3139">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3139">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="fd8ab-3140">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3140">fx_system_date_set</span></span>

<span data-ttu-id="fd8ab-3141">Anger systemdatum</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3141">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3142">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3142">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3143">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3143">Description</span></span>

<span data-ttu-id="fd8ab-3144">Den här tjänsten anger systemdatumet som angivet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3144">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-3145">*Den här tjänsten ska anropas strax efter **fx_system_initialize för** att ange det första systemdatumet. Som standard är systemdatumet den senaste allmänna FileX-versionen.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3145">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3146">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3146">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3147">**year**: Nytt år.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3147">**year**: New year.</span></span> <span data-ttu-id="fd8ab-3148">Det giltiga intervallet är från 1980 till och med år 2107.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3148">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="fd8ab-3149">**month**: Ny månad.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3149">**month**: New month.</span></span> <span data-ttu-id="fd8ab-3150">Det giltiga intervallet är mellan 1 och 12.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3150">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="fd8ab-3151">**day**: Ny dag.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3151">**day**: New day.</span></span> <span data-ttu-id="fd8ab-3152">Det giltiga intervallet är mellan 1 och 31, beroende på månad och skottår.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3152">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3153">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3153">Return Values</span></span>

- <span data-ttu-id="fd8ab-3154">**FX_SUCCESS** (0x00) Inställningen Lyckades.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3154">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="fd8ab-3155">**FX_INVALID_YEAR** (0x12) Ogiltigt år angivet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3155">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="fd8ab-3156">**FX_INVALID_MONTH** (0x13) Ogiltig månad har angetts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3156">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="fd8ab-3157">**FX_INVALID_DAY** (0x14) Ogiltig dag har angetts.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3157">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3158">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3158">Allowed From</span></span>

<span data-ttu-id="fd8ab-3159">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3159">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3160">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3160">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3161">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3161">See Also</span></span>

- <span data-ttu-id="fd8ab-3162">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3162">fx_system_date_get</span></span>
- <span data-ttu-id="fd8ab-3163">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3163">fx_system_initialize</span></span>
- <span data-ttu-id="fd8ab-3164">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3164">fx_system_time_get</span></span>
- <span data-ttu-id="fd8ab-3165">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3165">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="fd8ab-3166">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3166">fx_system_initialize</span></span>

<span data-ttu-id="fd8ab-3167">Initierar hela systemet</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3167">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3168">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3168">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3169">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3169">Description</span></span>

<span data-ttu-id="fd8ab-3170">Den här tjänsten initierar alla större FileX-datastrukturer.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3170">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="fd8ab-3171">Det bör anropas antingen ***i tx_application_define*** eller möjligen från en initieringstråd och måste anropas innan du använder någon annan FileX-tjänst.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3171">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-3172">\*När det här anropet initieras bör programmet anropa fx_system_date_set _ och _ fx_system_time_set \* för att börja med ett *korrekt systemdatum och en korrekt tid.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3172">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3173">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3173">Input Parameters</span></span>

<span data-ttu-id="fd8ab-3174">Inget</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3174">None</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3175">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3175">Return Values</span></span>

<span data-ttu-id="fd8ab-3176">Inga.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3176">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3177">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3177">Allowed From</span></span>

<span data-ttu-id="fd8ab-3178">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3178">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3179">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3179">Example</span></span>

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3180">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3180">See Also</span></span>

- <span data-ttu-id="fd8ab-3181">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3181">fx_system_date_get</span></span>
- <span data-ttu-id="fd8ab-3182">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3182">fx_system_date_set</span></span>
- <span data-ttu-id="fd8ab-3183">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3183">fx_system_time_get</span></span>
- <span data-ttu-id="fd8ab-3184">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3184">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="fd8ab-3185">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3185">fx_system_time_get</span></span>

<span data-ttu-id="fd8ab-3186">Hämtar aktuell systemtid</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3186">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3187">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3187">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3188">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3188">Description</span></span>

<span data-ttu-id="fd8ab-3189">Den här tjänsten hämtar den aktuella systemtiden.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3189">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3190">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3190">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3191">**hour**: Pekare till mål för timme.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3191">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="fd8ab-3192">**minute**: Pekare till mål för minut.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3192">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="fd8ab-3193">**second**: Pekare till mål för andra.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3193">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3194">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3194">Return Values</span></span>

- <span data-ttu-id="fd8ab-3195">**FX_SUCCESS** (0x00) Lyckad systemtidshämtning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3195">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="fd8ab-3196">**FX_PTR_ERROR** (0x18) En eller flera av indataparametrarna</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3196">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3197">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3197">Allowed From</span></span>

<span data-ttu-id="fd8ab-3198">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3199">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3199">Example</span></span>

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3200">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3200">See Also</span></span>

- <span data-ttu-id="fd8ab-3201">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3201">fx_system_date_get</span></span>
- <span data-ttu-id="fd8ab-3202">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3202">fx_system_date_set</span></span>
- <span data-ttu-id="fd8ab-3203">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3203">fx_system_initialize</span></span>
- <span data-ttu-id="fd8ab-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3204">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="fd8ab-3205">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3205">fx_system_time_set</span></span>

<span data-ttu-id="fd8ab-3206">Anger aktuell systemtid</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3206">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3207">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3207">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3208">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3208">Description</span></span>

<span data-ttu-id="fd8ab-3209">Den här tjänsten anger den aktuella systemtiden till den som anges av indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3209">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-3210">*Den här tjänsten ska anropas strax efter **fx_system_initialize för** att ange den första systemtiden. Som standard är systemtiden 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3210">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3211">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3211">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3212">**hour**: Ny timme (0–23).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3212">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="fd8ab-3213">**minute**: Ny minut (0–59).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3213">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="fd8ab-3214">**second**: Ny sekund (0–59).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3214">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3215">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3215">Return Values</span></span>

- <span data-ttu-id="fd8ab-3216">**FX_SUCCESS** (0x00) Lyckad systemtidshämtning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3216">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="fd8ab-3217">**FX_INVALID_HOUR**    (0x15) Ny timme är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3217">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="fd8ab-3218">**FX_INVALID_MINUTE** (0x16) Ny minut är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3218">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="fd8ab-3219">**FX_INVALID_SECOND** (0x17) Ny sekund är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3219">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3220">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3220">Allowed From</span></span>

<span data-ttu-id="fd8ab-3221">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3221">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3222">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3222">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3223">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3223">See Also</span></span>

- <span data-ttu-id="fd8ab-3224">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3224">fx_system_date_get</span></span>
- <span data-ttu-id="fd8ab-3225">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3225">fx_system_date_set</span></span>
- <span data-ttu-id="fd8ab-3226">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3226">fx_system_initialize</span></span>
- <span data-ttu-id="fd8ab-3227">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3227">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="fd8ab-3228">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3228">fx_unicode_directory_create</span></span>

<span data-ttu-id="fd8ab-3229">Skapar en Unicode-katalog</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3229">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3230">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3230">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3231">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3231">Description</span></span>

<span data-ttu-id="fd8ab-3232">Den här tjänsten skapar en Unicode-namngiven underkatalog i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i parametern Unicode-källnamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3232">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="fd8ab-3233">Om det lyckas returneras det korta namnet (8.3-format) för den nyligen skapade Unicode-underkatalogen av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3233">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-3234">*Alla åtgärder i Unicode-underkatalogen (vilket gör den till standardsökväg, borttagning osv.) ska göras genom att ange det returnerade korta namnet (8.3-format) till standardfilX-katalogtjänsterna.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3234">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3235">*Den här tjänsten stöds inte på exFAT-media.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3235">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3236">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3236">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3237">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3237">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3238">**source_unicode_name:** Pekare till Unicode-namnet för den nya underkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3238">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="fd8ab-3239">**source_unicode_length:** Längden på Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3239">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3240">**short_name:** Pekare till mål för kortnamn (8.3-format) för den nya Unicode-underkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3240">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3241">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3241">Return Values</span></span>

- <span data-ttu-id="fd8ab-3242">**FX_SUCCESS** (0x00) Lyckad Unicode-katalog skapas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3242">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="fd8ab-3243">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3243">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3244">**FX_ALREADY_CREATED** (0x0B) Angiven katalog finns redan.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3244">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="fd8ab-3245">**FX_NO_MORE_SPACE** (0x0A) Inga fler kluster tillgängliga på mediet för den nya katalogposten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3245">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="fd8ab-3246">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3246">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="fd8ab-3247">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3247">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-3248">**FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3248">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="fd8ab-3249">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3249">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="fd8ab-3250">**FX_IO_ERROR (0x90)** Drivrutins-I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3250">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3251">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3251">Allowed From</span></span>

<span data-ttu-id="fd8ab-3252">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3252">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3253">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3253">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3254">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3254">See Also</span></span>

- <span data-ttu-id="fd8ab-3255">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3255">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3256">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3256">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3257">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3257">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-3258">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3258">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-3259">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3259">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-3260">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3260">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-3261">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3261">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-3262">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3262">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-3263">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3263">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-3264">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3264">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-3265">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3265">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-3266">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3266">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-3267">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3267">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-3268">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3268">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-3269">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3269">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-3270">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3270">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-3271">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3271">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-3272">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3272">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-3273">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3273">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3274">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="fd8ab-3275">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3275">fx_unicode_directory_rename</span></span>

<span data-ttu-id="fd8ab-3276">Byter namn på katalogen med Unicode-sträng</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3276">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3277">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3277">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3278">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3278">Description</span></span>

<span data-ttu-id="fd8ab-3279">Den här tjänsten ändrar en Unicode-namngiven underkatalog till angivet nytt Unicode-namn i den aktuella arbetskatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3279">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="fd8ab-3280">Unicode-namnparametrarna får inte innehålla sökvägsinformation.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3280">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3281">*Den här tjänsten stöds inte på exFAT-media.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3281">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3282">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3282">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3283">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3283">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3284">**old_unicode_name:** Pekare till Unicode-namnet för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3284">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="fd8ab-3285">**old_unicode_name_length:** Längden på det aktuella Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3285">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3286">**new_unicode_name**: Pekare till det nya Unicode-filnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3286">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="fd8ab-3287">**old_unicode_name_length:** Längden på det nya Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3287">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3288">**new_short_name:** Pekare till mål för kortnamn (8.3-format) för den omdöpta Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3288">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="fd8ab-3289">Byt namn på katalog med Unicode</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3289">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3290">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3290">Return Values</span></span>

- <span data-ttu-id="fd8ab-3291">**FX_SUCCESS** (0x00) Lyckad media är öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3291">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="fd8ab-3292">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3292">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3293">**FX_ALREADY_CREATED** (0x0B) Angivet katalognamn finns redan.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3293">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="fd8ab-3294">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3294">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3295">**FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3295">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="fd8ab-3296">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3296">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="fd8ab-3297">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3297">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3298">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3298">Allowed From</span></span>

<span data-ttu-id="fd8ab-3299">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3299">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3300">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3300">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3301">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3301">See Also</span></span>

- <span data-ttu-id="fd8ab-3302">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3302">fx_directory_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3303">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3303">fx_directory_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3304">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3304">fx_directory_create</span></span>
- <span data-ttu-id="fd8ab-3305">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3305">fx_directory_default_get</span></span>
- <span data-ttu-id="fd8ab-3306">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3306">fx_directory_default_set</span></span>
- <span data-ttu-id="fd8ab-3307">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3307">fx_directory_delete</span></span>
- <span data-ttu-id="fd8ab-3308">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3308">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="fd8ab-3309">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3309">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-3310">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3310">fx_directory_information_get</span></span>
- <span data-ttu-id="fd8ab-3311">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3311">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="fd8ab-3312">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3312">fx_directory_local_path_get</span></span>
- <span data-ttu-id="fd8ab-3313">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3313">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="fd8ab-3314">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3314">fx_directory_local_path_set</span></span>
- <span data-ttu-id="fd8ab-3315">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3315">fx_directory_long_name_get</span></span>
- <span data-ttu-id="fd8ab-3316">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3316">fx_directory_name_test</span></span>
- <span data-ttu-id="fd8ab-3317">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3317">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="fd8ab-3318">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3318">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="fd8ab-3319">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3319">fx_directory_rename</span></span>
- <span data-ttu-id="fd8ab-3320">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3320">fx_directory_short_name_get</span></span>
- <span data-ttu-id="fd8ab-3321">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3321">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="fd8ab-3322">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3322">fx_unicode_file_create</span></span>

<span data-ttu-id="fd8ab-3323">Skapar en Unicode-fil</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3323">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3324">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3324">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3325">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3325">Description</span></span>

<span data-ttu-id="fd8ab-3326">Den här tjänsten skapar en Unicode-namngiven fil i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i parametern Unicode-källnamn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3326">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="fd8ab-3327">Om det lyckas returneras det korta namnet (8.3-format) för den nyligen skapade Unicode-filen av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3327">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="fd8ab-3328">*Alla åtgärder på Unicode-filen (öppna, skriva, läsa, stänga osv.) ska göras genom att ange det returnerade korta namnet (formatet 8.3) till standardfiltjänsterna för FileX.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3328">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3329">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3329">Input Parameters</span></span>


- <span data-ttu-id="fd8ab-3330">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3330">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3331">**source_unicode_name:** Pekare till Unicode-namnet för den nya filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3331">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="fd8ab-3332">**source_unicode_length:** Längden på Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3332">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3333">**short_name**: Pekare till mål för kortnamn (8.3-format) för den nya Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3333">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3334">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3334">Return Values</span></span>

- <span data-ttu-id="fd8ab-3335">**FX_SUCCESS** (0x00) Lyckades fil skapas.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3335">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="fd8ab-3336">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3336">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3337">**FX_ALREADY_CREATED** (0x0B) Angiven fil finns redan.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3337">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="fd8ab-3338">**FX_NO_MORE_SPACE** (0x0A) Inga fler kluster tillgängliga på mediet för den nya filposten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3338">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="fd8ab-3339">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3339">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="fd8ab-3340">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3340">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3341">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3341">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="fd8ab-3342">**FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3342">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="fd8ab-3343">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3343">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3344">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3344">Allowed From</span></span>

<span data-ttu-id="fd8ab-3345">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3345">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3346">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3346">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3347">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3347">See Also</span></span>

- <span data-ttu-id="fd8ab-3348">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3348">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3349">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3349">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3350">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3350">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3351">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3351">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3352">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3353">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3354">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3355">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3359">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3362">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3363">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3364">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3365">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3366">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3367">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3368">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3369">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3371">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3371">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-3372">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3372">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-3373">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3373">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="fd8ab-3374">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3374">fx_unicode_file_rename</span></span>

<span data-ttu-id="fd8ab-3375">Byter namn på en fil med Unicode-sträng</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3375">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3376">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3376">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3377">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3377">Description</span></span>

<span data-ttu-id="fd8ab-3378">Den här tjänsten ändrar ett Unicode-namn till angivet nytt Unicode-namn i den aktuella standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3378">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="fd8ab-3379">Unicode-namnparametrarna får inte ha sökvägsinformation.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3379">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3380">*Den här tjänsten stöds inte på exFAT-media.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3380">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3381">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3381">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3382">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3382">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3383">**old_unicode_name:** Pekare till Unicode-namnet för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3383">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="fd8ab-3384">**old_unicode_name_length:** Längden på det aktuella Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3384">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3385">**new_unicode_name**: Pekare till det nya Unicode-filnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3385">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="fd8ab-3386">**new_unicode_name_length:** Längden på det nya Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3386">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3387">**new_short_name:** Pekare till mål för kortnamn (8.3-format) för den omdöpta Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3387">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3388">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3388">Return Values</span></span>


- <span data-ttu-id="fd8ab-3389">**FX_SUCCESS** (0x00) Lyckad media är öppen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3389">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="fd8ab-3390">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3390">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3391">**FX_ALREADY_CREATED** (0x0B) Det angivna filnamnet finns redan.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3391">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="fd8ab-3392">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3392">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3393">**FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3393">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="fd8ab-3394">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3394">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="fd8ab-3395">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3395">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3396">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3396">Allowed From</span></span>

<span data-ttu-id="fd8ab-3397">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3398">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3398">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3399">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3399">See Also</span></span>

- <span data-ttu-id="fd8ab-3400">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3400">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3401">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3401">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3402">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3402">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3403">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3403">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3404">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3404">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3405">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3405">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3406">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3406">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3407">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3407">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3408">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3408">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3409">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3409">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3410">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3410">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3411">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3411">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3412">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3412">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3413">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3413">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3414">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3414">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3415">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3415">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3416">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3416">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3417">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3417">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3418">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3418">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3419">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3419">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3420">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3420">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3421">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3421">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3422">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3422">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3423">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3423">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-3424">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3424">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-3425">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3425">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="fd8ab-3426">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3426">fx_unicode_length_get</span></span>

<span data-ttu-id="fd8ab-3427">Hämtar längden på Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3427">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3428">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3428">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3429">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3429">Description</span></span>

<span data-ttu-id="fd8ab-3430">Den här tjänsten avgör längden på det angivna Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3430">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="fd8ab-3431">Ett Unicode-tecken representeras av två byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3431">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="fd8ab-3432">Ett Unicode-namn är en serie med Unicode-tecken med två byte som avslutas med två NULL-byte (två byte med 0 värde).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3432">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3433">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3433">Input Parameters</span></span>

<span data-ttu-id="fd8ab-3434">**unicode_name**: Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3434">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3435">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3435">Return Values</span></span>

<span data-ttu-id="fd8ab-3436">**length**: Längden på Unicode-namnet (antalet Unicode-tecken i namnet).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3436">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3437">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3437">Allowed From</span></span>

<span data-ttu-id="fd8ab-3438">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3438">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3439">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3439">Example</span></span>

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3440">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3440">See Also</span></span>

- <span data-ttu-id="fd8ab-3441">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3441">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3442">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3442">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3443">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3443">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3444">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3444">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3445">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3445">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3446">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3446">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3447">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3447">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3448">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3448">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3449">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3449">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3450">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3450">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3451">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3451">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3452">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3452">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3453">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3453">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3454">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3454">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3455">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3455">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3456">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3456">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3457">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3457">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3458">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3458">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3459">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3459">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3460">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3460">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3461">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3461">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3462">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3462">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3463">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3463">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3464">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3464">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-3465">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3465">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-3466">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3466">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-3467">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3467">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="fd8ab-3468">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3468">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="fd8ab-3469">Hämtar längden på Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3469">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3470">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3470">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3471">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3471">Description</span></span>

<span data-ttu-id="fd8ab-3472">Den här tjänsten hämtar längden på det angivna Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3472">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="fd8ab-3473">Ett Unicode-tecken representeras av två byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3473">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="fd8ab-3474">Ett Unicode-namn är en serie med Unicode-tecken på tvåbyte som avslutas med två NULL-byte (två byte med ett värde på 0).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3474">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3475">*Den här tjänsten är **identisk med fx_unicode_length_get()** förutom att anroparen skickar storleken på unicode_name bufferten, inklusive de två NULL-tecknen.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3475">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3476">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3476">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3477">**unicode_name**: Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3477">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3478">**buffer_length:** Storlek på Unicode-namnbuffert.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3478">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3479">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3479">Return Values</span></span>

<span data-ttu-id="fd8ab-3480">**length**: Längden på Unicode-namnet (antalet Unicode-tecken i namnet).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3480">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3481">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3481">Allowed From</span></span>

<span data-ttu-id="fd8ab-3482">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3482">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3483">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3483">Example</span></span>

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3484">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3484">See Also</span></span>

- <span data-ttu-id="fd8ab-3485">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3485">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3486">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3486">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3487">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3487">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3488">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3488">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3489">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3489">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3490">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3490">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3491">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3491">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3492">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3492">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3493">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3493">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3494">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3494">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3495">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3495">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3496">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3496">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3497">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3497">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3498">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3498">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3499">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3499">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3500">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3500">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3501">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3501">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3502">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3502">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3503">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3503">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3504">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3504">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3505">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3505">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3506">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3506">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3507">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3507">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3508">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3508">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-3509">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3509">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-3510">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3510">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-3511">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3511">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="fd8ab-3512">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3512">fx_unicode_name_get</span></span>

<span data-ttu-id="fd8ab-3513">Hämtar Unicode-namn från kortnamn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3513">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3514">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3514">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3515">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3515">Description</span></span>

<span data-ttu-id="fd8ab-3516">Den här tjänsten hämtar Unicode-namnet som är associerat med det angivna kortnamnet (formatet 8.3) i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i den korta namnparametern.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3516">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="fd8ab-3517">Om det lyckas returneras Unicode-namnet som är associerat med det korta namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3517">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3518">*Den här tjänsten kan användas för att hämta Unicode-namn för både filer och underkataloger.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3518">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3519">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3519">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3520">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3520">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3521">**short_name** Pekare till kortnamn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3521">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="fd8ab-3522">**destination_unicode_name:** Pekare till målet för Unicode-namnet som är associerat med det angivna korta namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3522">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="fd8ab-3523">destination_unicode_length : **Pekare** till returnerad Unicode-namnlängd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3523">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3524">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3524">Return Values</span></span>

- <span data-ttu-id="fd8ab-3525">**FX_SUCCESS** (0x00) Lyckad hämtning av Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3525">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="fd8ab-3526">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3526">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="fd8ab-3527">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3527">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-3528">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3528">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3529">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3529">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3530">**FX_NOT_FOUND** (0x04) Kortnamnet hittades inte eller så är Unicode-målstorleken för liten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3530">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="fd8ab-3531">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3531">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-3532">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3532">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="fd8ab-3533">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3534">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3534">Allowed From</span></span>

<span data-ttu-id="fd8ab-3535">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3536">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3536">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3537">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3537">See Also</span></span>

- <span data-ttu-id="fd8ab-3538">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3538">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3539">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3539">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3540">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3540">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3541">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3541">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3542">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3542">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3543">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3543">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3544">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3544">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3545">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3545">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3546">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3546">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3547">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3547">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3548">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3548">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3549">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3549">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3550">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3550">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3551">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3551">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3552">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3552">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3553">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3553">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3554">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3554">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3555">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3555">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3556">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3556">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3557">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3557">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3558">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3558">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3559">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3559">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3560">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3560">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3561">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3561">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-3562">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3562">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-3563">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3563">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="fd8ab-3564">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3564">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="fd8ab-3565">Hämtar Unicode-namn från kortnamn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3565">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3566">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3566">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="fd8ab-3567">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3567">Description</span></span>

<span data-ttu-id="fd8ab-3568">Den här tjänsten hämtar Unicode-namnet som är associerat med det angivna kortnamnet (formatet 8.3) i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i den korta namnparametern.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3568">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="fd8ab-3569">Om det lyckas returneras Unicode-namnet som är associerat med det korta namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3569">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3570">\*Den här tjänsten är identisk med \***fx_unicode_name_get**, förutom att anroparen tillhandahåller storleken på _Unicode-målbufferten som ett indataargument. På så sätt kan tjänsten garantera att den inte skriver över Unicode-målbufferten_</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3570">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3571">*Den här tjänsten kan användas för att hämta Unicode-namn för både filer och underkataloger.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3571">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3572">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3572">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3573">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3573">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3574">**short_name**: Pekare till kortnamn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3574">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="fd8ab-3575">**destination_unicode_name: Pekare** till målet för Unicode-namnet som är associerat med det angivna kortnamnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3575">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="fd8ab-3576">**destination_unicode_length: Pekare** till returnerad Unicode-namnlängd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3576">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="fd8ab-3577">**unicode_name_buffer_length:** Storlek på Unicode-namnbufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3577">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="fd8ab-3578">Obs! En NULL-avslutning krävs, vilket gör en extra byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3578">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3579">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3579">Return Values</span></span>

- <span data-ttu-id="fd8ab-3580">**FX_SUCCESS** (0x00) Lyckad hämtning av Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3580">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="fd8ab-3581">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3581">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="fd8ab-3582">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3582">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-3583">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3583">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3584">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3584">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3585">**FX_NOT_FOUND** (0x04) Kortnamnet hittades inte eller så är Unicode-målstorleken för liten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3585">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="fd8ab-3586">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3586">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-3587">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3587">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="fd8ab-3588">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3588">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3589">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3589">Allowed From</span></span>

<span data-ttu-id="fd8ab-3590">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3590">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3591">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3591">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3592">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3592">See Also</span></span>

- <span data-ttu-id="fd8ab-3593">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3593">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3594">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3594">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3595">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3595">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3596">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3596">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3597">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3597">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3598">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3598">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3599">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3599">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3600">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3600">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3601">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3601">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3602">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3602">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3603">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3603">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3604">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3604">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3605">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3605">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3606">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3606">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3607">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3607">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3608">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3608">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3609">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3609">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3610">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3610">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3611">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3611">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3612">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3612">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3613">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3613">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3614">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3614">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3615">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3615">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3616">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3616">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-3617">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3617">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3618">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="fd8ab-3619">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3619">fx_unicode_short_name_get</span></span>

<span data-ttu-id="fd8ab-3620">Hämtar kort namn från Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3620">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3621">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3621">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="fd8ab-3622">Den här tjänsten hämtar det korta namnet (8.3-format) som är associerat med Unicode-namnet i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i Unicode-namnparametern.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3622">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="fd8ab-3623">Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3623">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3624">*Den här tjänsten kan användas för att hämta korta namn för både filer och underkataloger.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3624">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3625">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3625">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3626">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3626">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3627">**source_unicode_name**: Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3627">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3628">**source_unicode_length:** Längden på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3628">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3629">**destination_short_name:** Pekare till mål för kortnamnet (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3629">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="fd8ab-3630">Detta måste vara minst 13 byte stort.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3630">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3631">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3631">Return Values</span></span>

- <span data-ttu-id="fd8ab-3632">**FX_SUCCESS** (0x00) Kortnamnhämtningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3632">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="fd8ab-3633">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3633">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="fd8ab-3634">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3634">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="fd8ab-3635">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3635">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3636">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3637">**FX_NOT_FOUND** (0x04) Unicode-namn hittades inte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3637">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="fd8ab-3638">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3638">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="fd8ab-3639">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3639">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-3640">**FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3640">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="fd8ab-3641">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3641">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3642">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3642">Allowed From</span></span>

<span data-ttu-id="fd8ab-3643">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3643">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3644">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3644">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3645">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3645">See Also</span></span>

- <span data-ttu-id="fd8ab-3646">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3646">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3647">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3647">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3648">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3648">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3649">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3649">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3650">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3650">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3651">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3651">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3652">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3652">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3653">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3653">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3654">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3654">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3655">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3655">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3656">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3656">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3657">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3657">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3658">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3658">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3659">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3659">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3660">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3660">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3661">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3661">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3662">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3662">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3663">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3663">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3664">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3664">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3665">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3665">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3666">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3666">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3667">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3667">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3668">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3668">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3669">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3669">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-3670">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3670">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-3671">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3671">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="fd8ab-3672">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3672">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="fd8ab-3673">Hämtar kort namn från Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3673">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="fd8ab-3674">Prototyp</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3674">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="fd8ab-3675">Description</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3675">Description</span></span>

<span data-ttu-id="fd8ab-3676">Den här tjänsten hämtar det korta namnet (8.3-format) som är associerat med Unicode-namnet i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i Unicode-namnparametern.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3676">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="fd8ab-3677">Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3677">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8ab-3678">*Den här tjänsten är identisk **med fx_unicode_short_name_get()**, förutom att anroparen tillhandahåller storleken på målbufferten som ett indataargument. Detta gör att tjänsten kan garantera att det korta namnet inte överskrider målbufferten.*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3678">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="fd8ab-3679">*Den här tjänsten kan användas för att hämta korta namn för både filer och underkataloger*</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3679">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fd8ab-3680">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3680">Input Parameters</span></span>

- <span data-ttu-id="fd8ab-3681">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3681">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="fd8ab-3682">**source_unicode_name**: Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3682">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3683">**source_unicode_length:** Längden på Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3683">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="fd8ab-3684">**destination_short_name:** Pekare till mål för kortnamnet (formatet 8.3).</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3684">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="fd8ab-3685">Det måste vara minst 13 byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3685">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="fd8ab-3686">**short_name_buffer_length:** Storleken på målbufferten.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3686">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="fd8ab-3687">Buffertstorleken måste vara minst 14 byte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3687">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="fd8ab-3688">Returvärden</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3688">Return Values</span></span>

- <span data-ttu-id="fd8ab-3689">**FX_SUCCESS** (0x00) Lyckad kort namnhämtning.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3689">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="fd8ab-3690">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3690">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="fd8ab-3691">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3691">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="fd8ab-3692">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3692">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="fd8ab-3693">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3693">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="fd8ab-3694">**FX_NOT_FOUND** (0x04) Unicode-namn hittades inte.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3694">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="fd8ab-3695">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3695">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="fd8ab-3696">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3696">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="fd8ab-3697">**FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3697">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="fd8ab-3698">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3698">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fd8ab-3699">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3699">Allowed From</span></span>

<span data-ttu-id="fd8ab-3700">Trådar</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3700">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fd8ab-3701">Exempel</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3701">Example</span></span>

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="fd8ab-3702">Se även</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3702">See Also</span></span>

- <span data-ttu-id="fd8ab-3703">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3703">fx_file_allocate</span></span>
- <span data-ttu-id="fd8ab-3704">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3704">fx_file_attributes_read</span></span>
- <span data-ttu-id="fd8ab-3705">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3705">fx_file_attributes_set</span></span>
- <span data-ttu-id="fd8ab-3706">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3706">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3707">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3707">fx_file_close</span></span>
- <span data-ttu-id="fd8ab-3708">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3708">fx_file_create</span></span>
- <span data-ttu-id="fd8ab-3709">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3709">fx_file_date_time_set</span></span>
- <span data-ttu-id="fd8ab-3710">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3710">fx_file_delete</span></span>
- <span data-ttu-id="fd8ab-3711">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3711">fx_file_extended_allocate</span></span>
- <span data-ttu-id="fd8ab-3712">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3712">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="fd8ab-3713">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3713">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3714">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3714">fx_file_extended_seek</span></span>
- <span data-ttu-id="fd8ab-3715">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3715">fx_file_extended_truncate</span></span>
- <span data-ttu-id="fd8ab-3716">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3716">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3717">fx_file_open</span></span>
- <span data-ttu-id="fd8ab-3718">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3718">fx_file_read</span></span>
- <span data-ttu-id="fd8ab-3719">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3719">fx_file_relative_seek</span></span>
- <span data-ttu-id="fd8ab-3720">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3720">fx_file_rename</span></span>
- <span data-ttu-id="fd8ab-3721">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3721">fx_file_seek</span></span>
- <span data-ttu-id="fd8ab-3722">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3722">fx_file_truncate</span></span>
- <span data-ttu-id="fd8ab-3723">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3723">fx_file_truncate_release</span></span>
- <span data-ttu-id="fd8ab-3724">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3724">fx_file_write</span></span>
- <span data-ttu-id="fd8ab-3725">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3725">fx_file_write_notify_set</span></span>
- <span data-ttu-id="fd8ab-3726">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3726">fx_unicode_file_create</span></span>
- <span data-ttu-id="fd8ab-3727">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3727">fx_unicode_file_rename</span></span>
- <span data-ttu-id="fd8ab-3728">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3728">fx_unicode_name_get</span></span>
- <span data-ttu-id="fd8ab-3729">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="fd8ab-3729">fx_unicode_short_name_get</span></span>
