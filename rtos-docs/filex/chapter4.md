---
title: Kapitel 4 – Beskrivning Azure RTOS FileX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS FileX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c24259fb9b6b212dda99422e3ee1ad0e2fd970ce
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754887"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="457c7-103">Kapitel 4 – Beskrivning Azure RTOS FileX-tjänster</span><span class="sxs-lookup"><span data-stu-id="457c7-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="457c7-104">Det här kapitlet innehåller en beskrivning av alla Azure RTOS FileX-tjänster i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="457c7-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="457c7-105">Tjänstnamn är utformade så att alla liknande tjänster grupperas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="457c7-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="457c7-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="457c7-107">Läser katalogattribut</span><span class="sxs-lookup"><span data-stu-id="457c7-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="457c7-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-109">Description</span></span>

<span data-ttu-id="457c7-110">Den här tjänsten läser katalogens attribut från det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-111">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-111">Input Parameters</span></span>

- <span data-ttu-id="457c7-112">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-113">**directory_name:** Pekare till namnet på den begärda katalogen (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="457c7-114">**attribut** _ptr: Pekare till målet för katalogens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="457c7-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="457c7-115">Katalogattributen returneras i bitkartformat med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="457c7-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="457c7-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="457c7-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="457c7-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="457c7-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="457c7-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="457c7-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="457c7-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="457c7-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="457c7-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="457c7-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-122">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-122">Return Values</span></span>

- <span data-ttu-id="457c7-123">**FX_SUCCESS** (0x00) Lyckade katalogattribut lästa</span><span class="sxs-lookup"><span data-stu-id="457c7-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="457c7-124">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-125">**FX _NOT FOUND** (0x04) Den angivna katalogen hittades inte på mediet</span><span class="sxs-lookup"><span data-stu-id="457c7-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="457c7-126">**FX_NOT_DIRECTORY posten** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="457c7-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="457c7-127">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="457c7-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-128">**FX_FILE_CORRUPT** 0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-129">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-130">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-131">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-132">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="457c7-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="457c7-133">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare</span><span class="sxs-lookup"><span data-stu-id="457c7-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="457c7-134">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-135">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-135">Allowed From</span></span>

<span data-ttu-id="457c7-136">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="457c7-138">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-138">See Also</span></span>

- <span data-ttu-id="457c7-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-140">fx_directory_create</span></span>
- <span data-ttu-id="457c7-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-141">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-142">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-143">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-146">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-152">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-155">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="457c7-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="457c7-160">Anger katalogattribut</span><span class="sxs-lookup"><span data-stu-id="457c7-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-161">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="457c7-162">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-162">Description</span></span>

<span data-ttu-id="457c7-163">Den här tjänsten anger katalogens attribut till de som anges av anroparen.</span><span class="sxs-lookup"><span data-stu-id="457c7-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-164">*Det här programmet kan bara ändra en delmängd av katalogens attribut med den här tjänsten. Alla försök att ange ytterligare attribut resulterar i ett fel.*</span><span class="sxs-lookup"><span data-stu-id="457c7-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-165">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-165">Input Parameters</span></span>

- <span data-ttu-id="457c7-166">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-167">**directory_name:** Pekare till namnet på den begärda katalogen (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="457c7-168">**attribut:** De nya attributen för den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="457c7-169">Giltiga katalogattribut definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="457c7-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="457c7-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="457c7-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="457c7-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="457c7-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="457c7-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="457c7-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-174">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-174">Return Values</span></span>

- <span data-ttu-id="457c7-175">**FX_SUCCESS** (0x00) Lyckad katalogattributuppsättning</span><span class="sxs-lookup"><span data-stu-id="457c7-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="457c7-176">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-177">**FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet</span><span class="sxs-lookup"><span data-stu-id="457c7-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="457c7-178">**FX_NOT_DIRECTORY posten** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="457c7-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="457c7-179">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="457c7-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-180">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat</span><span class="sxs-lookup"><span data-stu-id="457c7-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="457c7-181">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-182">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-183">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-184">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-185">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="457c7-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="457c7-186">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="457c7-187">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare</span><span class="sxs-lookup"><span data-stu-id="457c7-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="457c7-188">**FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.</span><span class="sxs-lookup"><span data-stu-id="457c7-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="457c7-189">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-190">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-190">Allowed From</span></span>

<span data-ttu-id="457c7-191">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-192">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-193">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-193">See Also</span></span>

- <span data-ttu-id="457c7-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-195">fx_directory_create</span></span>
- <span data-ttu-id="457c7-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-196">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-197">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-198">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-201">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-207">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-210">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="457c7-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-214">fx_directory_create</span></span>

<span data-ttu-id="457c7-215">Skapar underkatalog</span><span class="sxs-lookup"><span data-stu-id="457c7-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-216">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="457c7-217">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-217">Description</span></span>

<span data-ttu-id="457c7-218">Den här tjänsten skapar en underkatalog i den aktuella standardkatalogen eller i den sökväg som anges i katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="457c7-219">Till skillnad från rotkatalogen har underkatalogerna ingen gräns för antalet filer som de kan innehålla.</span><span class="sxs-lookup"><span data-stu-id="457c7-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="457c7-220">Rotkatalogen kan bara innehålla det antal poster som bestäms av startposten.</span><span class="sxs-lookup"><span data-stu-id="457c7-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-221">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-221">Input Parameters</span></span>

- <span data-ttu-id="457c7-222">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-223">**directory_name:** Pekare till namnet på katalogen som ska skapas (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-224">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-224">Return Values</span></span>

- <span data-ttu-id="457c7-225">**FX_SUCCESS** (0x00) Lyckad katalog create.</span><span class="sxs-lookup"><span data-stu-id="457c7-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="457c7-226">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-227">**FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet</span><span class="sxs-lookup"><span data-stu-id="457c7-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="457c7-228">**FX_NOT_DIRECTORY posten** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="457c7-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="457c7-229">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="457c7-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-230">**FX_FILE _CORRUPT** (0x08) filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-231">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-232">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-233">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-234">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="457c7-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="457c7-235">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="457c7-236">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare</span><span class="sxs-lookup"><span data-stu-id="457c7-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="457c7-237">**FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.</span><span class="sxs-lookup"><span data-stu-id="457c7-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="457c7-238">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-239">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-239">Allowed From</span></span>

<span data-ttu-id="457c7-240">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-241">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-242">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-242">See Also</span></span>

- <span data-ttu-id="457c7-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-245">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-246">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-247">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-250">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-256">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-259">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="457c7-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-263">fx_directory_default_get</span></span>

<span data-ttu-id="457c7-264">Hämtar den senaste standardkatalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-265">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="457c7-266">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-266">Description</span></span>

<span data-ttu-id="457c7-267">Den här tjänsten returnerar pekaren till den sökväg som senast angetts ***av fx_directory_default_set***.</span><span class="sxs-lookup"><span data-stu-id="457c7-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="457c7-268">Om standardkatalogen inte har angetts eller om den aktuella standardkatalogen är rotkatalogen returneras värdet FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-269">*Standardstorleken för den interna sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="457c7-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-270">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-270">Input Parameters</span></span>

- <span data-ttu-id="457c7-271">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-272">**return_path_name:** Pekare till målet för den senaste standardkatalogsträngen.</span><span class="sxs-lookup"><span data-stu-id="457c7-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="457c7-273">Värdet för FX_NULL returneras om den aktuella inställningen för standardkatalogen är roten.</span><span class="sxs-lookup"><span data-stu-id="457c7-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="457c7-274">När mediet öppnas är roten standard.</span><span class="sxs-lookup"><span data-stu-id="457c7-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-275">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-275">Return Values</span></span>

- <span data-ttu-id="457c7-276">**FX_SUCCESS** (0x00) Lyckad standardkatalog hämta</span><span class="sxs-lookup"><span data-stu-id="457c7-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="457c7-277">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-278">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="457c7-279">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-280">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-280">Allowed From</span></span>

<span data-ttu-id="457c7-281">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-282">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="457c7-283">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-283">See Also</span></span>

- <span data-ttu-id="457c7-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-286">fx_directory_create</span></span>
- <span data-ttu-id="457c7-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-287">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-288">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-291">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-297">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-300">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="457c7-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-304">fx_directory_default_set</span></span>

<span data-ttu-id="457c7-305">Anger standardkatalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-306">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="457c7-307">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-307">Description</span></span>

<span data-ttu-id="457c7-308">Den här tjänsten anger standardkatalogen för mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="457c7-309">Om värdet FX_NULL anges anges standardkatalogen till mediets rotkatalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="457c7-310">Alla efterföljande filåtgärder som inte uttryckligen anger en sökväg kommer som standard att använda den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-311">*Standardstorleken för den interna sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="457c7-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-312">*För namn som tillhandahålls av programmet stöder FileX både omsnedstreck ( ) och snedstreck (/) tecken till separata \\ kataloger, underkataloger och filnamn. FileX använder dock bara omsnedstreckstecknet i sökvägar som returneras till programmet.*</span><span class="sxs-lookup"><span data-stu-id="457c7-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-313">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-313">Input Parameters</span></span>

- <span data-ttu-id="457c7-314">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-315">**new_path_name:** Pekare till nytt standardkatalognamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="457c7-316">Om ett värde FX_NULL anges anges standardkatalogen för mediet till mediets rotkatalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-317">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-317">Return Values</span></span>

- <span data-ttu-id="457c7-318">**FX_SUCCESS** (0x00) Lyckad standardkataloguppsättning</span><span class="sxs-lookup"><span data-stu-id="457c7-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="457c7-319">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-320">**FX_INVALID_PATH** (0x0D) Det gick inte att hitta den nya katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="457c7-321">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-322">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-323">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-323">Allowed From</span></span>

<span data-ttu-id="457c7-324">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-325">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-326">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-326">See Also</span></span>

- <span data-ttu-id="457c7-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-329">fx_directory_create</span></span>
- <span data-ttu-id="457c7-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-330">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-331">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-334">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-340">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-343">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="457c7-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-347">fx_directory_delete</span></span>

<span data-ttu-id="457c7-348">Tar bort underkatalog</span><span class="sxs-lookup"><span data-stu-id="457c7-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-349">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="457c7-350">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-350">Description</span></span>

<span data-ttu-id="457c7-351">Den här tjänsten tar bort den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-351">This service deletes the specified directory.</span></span> <span data-ttu-id="457c7-352">Observera att katalogen måste vara tom för att ta bort den.</span><span class="sxs-lookup"><span data-stu-id="457c7-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-353">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-353">Input Parameters</span></span>

- <span data-ttu-id="457c7-354">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-355">**directory_name: Pekare** till namnet på katalogen som ska tas bort (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-356">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-356">Return Values</span></span>

- <span data-ttu-id="457c7-357">**FX_SUCCESS** (0x00) Lyckad katalog borttagning</span><span class="sxs-lookup"><span data-stu-id="457c7-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="457c7-358">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-359">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="457c7-360">**FX_DIR_NOT_EMPTY** (0x10) Den angivna katalogen är inte tom</span><span class="sxs-lookup"><span data-stu-id="457c7-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="457c7-361">**FX_IO_ERROR** (0x90) Drivrutins-I/O</span><span class="sxs-lookup"><span data-stu-id="457c7-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-362">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade</span><span class="sxs-lookup"><span data-stu-id="457c7-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="457c7-363">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-364">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-365">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-366">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-367">**FX_MEDIA_INVALID** (0x02) Ogiltig media</span><span class="sxs-lookup"><span data-stu-id="457c7-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="457c7-368">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="457c7-369">**FX_NOT_DIRECTORY** (0x0E) Inte en katalogpost</span><span class="sxs-lookup"><span data-stu-id="457c7-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="457c7-370">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="457c7-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="457c7-371">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-372">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-372">Allowed From</span></span>

<span data-ttu-id="457c7-373">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-374">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-375">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-375">See Also</span></span>

- <span data-ttu-id="457c7-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-378">fx_directory_create</span></span>
- <span data-ttu-id="457c7-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-379">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-380">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-383">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-389">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-392">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="457c7-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="457c7-397">Hämtar den första katalogposten</span><span class="sxs-lookup"><span data-stu-id="457c7-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-398">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="457c7-399">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-399">Description</span></span>

<span data-ttu-id="457c7-400">Den här tjänsten hämtar det första postnamnet i standardkatalogen och kopierar det till det angivna målet.</span><span class="sxs-lookup"><span data-stu-id="457c7-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-401">*Det angivna målet måste vara tillräckligt stort för att innehålla det maximala FileX-namnet, enligt definitionen i **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="457c7-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-402">*Om du använder en icke-lokal sökväg är det viktigt att förhindra (med en ThreadX-semaphore, mutex eller prioritetsnivåändring) att andra programtrådar ändrar den här katalogen medan en katalogförseningar sker. Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="457c7-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-403">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-403">Input Parameters</span></span>

- <span data-ttu-id="457c7-404">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-405">**return_entry_name:** Pekare till mål för det första postnamnet i standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-406">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-406">Return Values</span></span>

- <span data-ttu-id="457c7-407">**FX_SUCCESS** (0x00) Lyckad första katalogposts find</span><span class="sxs-lookup"><span data-stu-id="457c7-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="457c7-408">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-409">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="457c7-410">**FX_IO_ERROR** (0x90) Drivrutins-I/O</span><span class="sxs-lookup"><span data-stu-id="457c7-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-411">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-412">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-413">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-414">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare</span><span class="sxs-lookup"><span data-stu-id="457c7-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="457c7-415">**FX_CALLER_ERROR** (0x20) Anroparen är inte en tråd</span><span class="sxs-lookup"><span data-stu-id="457c7-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-416">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-416">Allowed From</span></span>

<span data-ttu-id="457c7-417">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-418">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-419">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-419">See Also</span></span>

- <span data-ttu-id="457c7-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-422">fx_directory_create</span></span>
- <span data-ttu-id="457c7-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-423">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-424">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-425">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-427">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-433">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-436">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="457c7-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="457c7-441">Hämtar den första katalogposten med fullständig information</span><span class="sxs-lookup"><span data-stu-id="457c7-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-442">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="457c7-443">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-443">Input Parameters</span></span>

- <span data-ttu-id="457c7-444">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-445">**directory_name:** Pekare till målet för namnet på en katalogpost.</span><span class="sxs-lookup"><span data-stu-id="457c7-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="457c7-446">Måste vara minst lika stor som FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="457c7-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="457c7-447">**attribut:** Om det inte är null pekar du på målet för postens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="457c7-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="457c7-448">Attributen returneras i ett bit-map-format med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="457c7-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="457c7-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="457c7-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="457c7-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="457c7-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="457c7-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="457c7-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="457c7-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="457c7-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="457c7-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="457c7-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="457c7-455">**storlek:** Om det inte är null pekar du till målet för postens storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="457c7-456">**year**: Om det inte är null pekar du mot målet för postens ändringsår.</span><span class="sxs-lookup"><span data-stu-id="457c7-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="457c7-457">**month**: Om det inte är null pekar du på målet för postens ändringsmånad.</span><span class="sxs-lookup"><span data-stu-id="457c7-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="457c7-458">**day**: Om det inte är null pekar du mot målet för postens ändringsdag.</span><span class="sxs-lookup"><span data-stu-id="457c7-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="457c7-459">**hour**: Om det inte är null pekar du mot målet för postens ändringstimmar.</span><span class="sxs-lookup"><span data-stu-id="457c7-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="457c7-460">**minute**: Om det inte är null pekar du mot målet för postens ändringsminut.</span><span class="sxs-lookup"><span data-stu-id="457c7-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="457c7-461">**second**: Om det inte är null pekar du till målet för postens andra ändring.</span><span class="sxs-lookup"><span data-stu-id="457c7-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-462">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-462">Return Values</span></span>

- <span data-ttu-id="457c7-463">**FX_SUCCESS** (0x00) Lyckad första katalogposts find</span><span class="sxs-lookup"><span data-stu-id="457c7-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="457c7-464">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-465">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="457c7-466">**FX_IO_ERROR** (0x90) Drivrutins-I/O</span><span class="sxs-lookup"><span data-stu-id="457c7-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-467">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade</span><span class="sxs-lookup"><span data-stu-id="457c7-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="457c7-468">**FX_FILE _CORRUPT** (0x08) filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-469">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-470">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-471">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-472">**FX_MEDIA_INVALID** (0x02) Ogiltig media</span><span class="sxs-lookup"><span data-stu-id="457c7-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="457c7-473">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="457c7-474">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-475">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-475">Allowed From</span></span>

<span data-ttu-id="457c7-476">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-477">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-477">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-478">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-478">See Also</span></span>

- <span data-ttu-id="457c7-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-481">fx_directory_create</span></span>
- <span data-ttu-id="457c7-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-482">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-483">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-484">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-486">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-492">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-495">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="457c7-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="457c7-499">fx_directory_information_get:</span></span>

<span data-ttu-id="457c7-500">Hämtar information om katalogpost</span><span class="sxs-lookup"><span data-stu-id="457c7-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-501">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="457c7-502">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-502">Input Parameters</span></span>

- <span data-ttu-id="457c7-503">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-504">**directory_name:** Pekare till namnet på katalogposten.</span><span class="sxs-lookup"><span data-stu-id="457c7-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="457c7-505">**attribut:** Pekare till målet för attributen.</span><span class="sxs-lookup"><span data-stu-id="457c7-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="457c7-506">**storlek:** Pekare till målet för storleken.</span><span class="sxs-lookup"><span data-stu-id="457c7-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="457c7-507">**year**: Pekare till årets mål.</span><span class="sxs-lookup"><span data-stu-id="457c7-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="457c7-508">**month**: Pekare till målet för månaden.</span><span class="sxs-lookup"><span data-stu-id="457c7-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="457c7-509">**day**: Pekare till dagens mål.</span><span class="sxs-lookup"><span data-stu-id="457c7-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="457c7-510">**hour**: Pekare till målet för timmen.</span><span class="sxs-lookup"><span data-stu-id="457c7-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="457c7-511">**minute**: Pekare till målet för minuten.</span><span class="sxs-lookup"><span data-stu-id="457c7-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="457c7-512">**second**: Pekare till målet för den andra.</span><span class="sxs-lookup"><span data-stu-id="457c7-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-513">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-513">Return Values</span></span>

- <span data-ttu-id="457c7-514">**FX_SUCCESS** (0x00) Lyckad första katalogposts find</span><span class="sxs-lookup"><span data-stu-id="457c7-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="457c7-515">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-516">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna katalogen på mediet</span><span class="sxs-lookup"><span data-stu-id="457c7-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="457c7-517">**FX_IO_ERROR** (0x90) Drivrutins-I/O</span><span class="sxs-lookup"><span data-stu-id="457c7-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-518">**FX_MEDIA_INVALID** (0x02) Ogiltig media</span><span class="sxs-lookup"><span data-stu-id="457c7-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="457c7-519">**FX_FILE _CORRUPT** (0x08) filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-520">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-521">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-522">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-523">**FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="457c7-524">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-525">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-525">Allowed From</span></span>

<span data-ttu-id="457c7-526">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-527">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-527">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-528">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-528">See Also</span></span>

- <span data-ttu-id="457c7-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-531">fx_directory_create</span></span>
- <span data-ttu-id="457c7-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-532">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-533">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-534">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-542">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-545">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="457c7-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="457c7-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="457c7-550">Rensar den lokala standardsökvägen</span><span class="sxs-lookup"><span data-stu-id="457c7-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-551">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="457c7-552">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-552">Description</span></span>

<span data-ttu-id="457c7-553">Den här tjänsten rensar den tidigare lokala sökvägen som har ställts in för anropstråden.</span><span class="sxs-lookup"><span data-stu-id="457c7-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-554">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-554">Input Parameters</span></span>

- <span data-ttu-id="457c7-555">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-556">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-556">Return Values</span></span>

- <span data-ttu-id="457c7-557">**FX_SUCCESS** (0x00) Lyckad lokal sökväg rensas.</span><span class="sxs-lookup"><span data-stu-id="457c7-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="457c7-558">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande</span><span class="sxs-lookup"><span data-stu-id="457c7-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="457c7-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH har definierats</span><span class="sxs-lookup"><span data-stu-id="457c7-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="457c7-560">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="457c7-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-561">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-561">Allowed From</span></span>

<span data-ttu-id="457c7-562">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-563">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-564">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-564">See Also</span></span>

- <span data-ttu-id="457c7-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-567">fx_directory_create</span></span>
- <span data-ttu-id="457c7-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-568">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-569">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-570">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-573">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-578">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-581">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="457c7-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="457c7-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="457c7-586">Hämtar den aktuella lokala sökvägssträngen</span><span class="sxs-lookup"><span data-stu-id="457c7-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-587">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="457c7-588">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-588">Description</span></span>

<span data-ttu-id="457c7-589">Den här tjänsten returnerar pekaren för den lokala sökvägen för det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="457c7-590">Om det inte finns någon lokal sökväg returneras null-värdet till anroparen.</span><span class="sxs-lookup"><span data-stu-id="457c7-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-591">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-591">Input Parameters</span></span>

- <span data-ttu-id="457c7-592">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-593">**return_path_name:** Pekare till målsträngens pekare för den lokala sökvägssträng som ska lagras.</span><span class="sxs-lookup"><span data-stu-id="457c7-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-594">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-594">Return Values</span></span>

- <span data-ttu-id="457c7-595">**FX_SUCCESS** (0x00) Lyckad lokal sökväg hämta.</span><span class="sxs-lookup"><span data-stu-id="457c7-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="457c7-596">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande</span><span class="sxs-lookup"><span data-stu-id="457c7-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="457c7-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="457c7-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="457c7-598">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="457c7-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="457c7-599">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-599">Allowed From</span></span>

<span data-ttu-id="457c7-600">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-601">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-602">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-602">See Also</span></span>

- <span data-ttu-id="457c7-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-605">fx_directory_create</span></span>
- <span data-ttu-id="457c7-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-606">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-607">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-608">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-611">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-616">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-619">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="457c7-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="457c7-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="457c7-624">Återställer tidigare lokal sökväg</span><span class="sxs-lookup"><span data-stu-id="457c7-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-625">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="457c7-626">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-626">Description</span></span>

<span data-ttu-id="457c7-627">Den här tjänsten återställer en tidigare inställd lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="457c7-627">This service restores a previously set local path.</span></span> <span data-ttu-id="457c7-628">Katalogsökpositionen som görs på den här lokala sökvägen återställs också, vilket gör den här rutinen användbar i rekursiva katalog-traverserar av programmet.</span><span class="sxs-lookup"><span data-stu-id="457c7-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-629">*Varje lokal sökväg innehåller en lokal sökvägssträng **FX_MAXIMUM_PATH** i storlek, som som standard är 256 tecken. Den här interna sökvägssträngen används inte av FileX och tillhandahålls endast för programmets användning. Om **FX_LOCAL_PATH** ska deklareras som en lokal variabel bör användarna se upp för stacken som växer med den här strukturens storlek. Användarna är välkommen att minska storleken på FX_MAXIMUM_PATH **och återskapa** FileX-bibliotekskällan.*</span><span class="sxs-lookup"><span data-stu-id="457c7-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-630">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-630">Input Parameters</span></span>

- <span data-ttu-id="457c7-631">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-632">**local_path_ptr:** Pekare till den tidigare inställt lokala sökvägen.</span><span class="sxs-lookup"><span data-stu-id="457c7-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="457c7-633">Det är mycket viktigt att se till att pekaren verkligen pekar på en tidigare använd och fortfarande intakt lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="457c7-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-634">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-634">Return Values</span></span>

- <span data-ttu-id="457c7-635">**FX_SUCCESS** (0x00) Lyckad återställning av lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="457c7-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="457c7-636">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="457c7-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH definieras.</span><span class="sxs-lookup"><span data-stu-id="457c7-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="457c7-638">**FX_PTR_ERROR** (0x18) Ogiltig media eller lokal sökvägs pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-639">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-639">Allowed From</span></span>

<span data-ttu-id="457c7-640">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-641">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-642">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-642">See Also</span></span>

- <span data-ttu-id="457c7-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-645">fx_directory_create</span></span>
- <span data-ttu-id="457c7-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-646">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-647">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-648">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-651">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-656">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-659">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="457c7-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="457c7-664">Uppsättningar en trådspecifik lokal sökväg</span><span class="sxs-lookup"><span data-stu-id="457c7-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-665">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="457c7-666">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-666">Description</span></span>

<span data-ttu-id="457c7-667">Den här tjänsten uppsättningar en trådspecifik sökväg som anges av \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="457c7-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="457c7-668">När den här rutinen har slutförts har den lokala sökvägsinformationen som lagras i _ *_local_path_ptr_*\* företräde framför den globala mediesökvägen för alla fil- och katalogåtgärder som görs av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="457c7-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="457c7-669">Detta påverkar inte någon annan tråd i systemet</span><span class="sxs-lookup"><span data-stu-id="457c7-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="457c7-670">*Standardstorleken för den lokala sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="457c7-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-671">*För namn som tillhandahålls av programmet stöder FileX både omsnedstreck ( ) och snedstreck (/) tecken till separata \\ kataloger, underkataloger och filnamn. FileX använder dock bara omsnedstreckstecknet i sökvägar som returneras till programmet.*</span><span class="sxs-lookup"><span data-stu-id="457c7-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-672">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-672">Input Parameters</span></span>

- <span data-ttu-id="457c7-673">**media_ptr:** Pekare till det tidigare öppnade mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="457c7-674">**local_path_ptr:** Mål för att lagra den trådspecifika lokala sökvägsinformationen.</span><span class="sxs-lookup"><span data-stu-id="457c7-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="457c7-675">Adressen för den här strukturen kan anges för den lokala funktionen för sökvägsåterställning i framtiden.</span><span class="sxs-lookup"><span data-stu-id="457c7-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="457c7-676">**new_path_name:** Anger den lokala sökvägen till konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="457c7-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-677">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-677">Return Values</span></span>

- <span data-ttu-id="457c7-678">**FX_SUCCESS** (0x00) Lyckad standardkataloguppsättning.</span><span class="sxs-lookup"><span data-stu-id="457c7-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="457c7-679">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="457c7-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="457c7-681">**FX_INVALID_PATH** (0x0D) Det gick inte att hitta någon ny katalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="457c7-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH har definierats.</span><span class="sxs-lookup"><span data-stu-id="457c7-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="457c7-683">**FX_PTR_ERROR** (0x18) Ogiltig media eller lokal sökvägs pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-684">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-684">Allowed From</span></span>

<span data-ttu-id="457c7-685">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-686">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-686">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-687">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-687">See Also</span></span>

- <span data-ttu-id="457c7-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-690">fx_directory_create</span></span>
- <span data-ttu-id="457c7-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-691">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-692">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-693">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-696">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-701">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-704">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="457c7-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="457c7-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="457c7-709">Hämtar långt namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="457c7-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-710">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="457c7-711">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-711">Description</span></span>

<span data-ttu-id="457c7-712">Den här tjänsten hämtar det långa namnet (om det finns) som är associerat med det angivna korta (8,3-format) namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="457c7-713">Det korta namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-714">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-714">Input Parameters</span></span>

- <span data-ttu-id="457c7-715">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-716">**short_name**: Pekare till källans korta namn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="457c7-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="457c7-717">**long_name:** Pekare till mål för det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="457c7-718">Om det inte finns något långt namn returneras det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="457c7-719">Observera att målet för det långa namnet måste vara tillräckligt stort för att innehålla FX_MAX_LONG_NAME_LEN tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-720">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-720">Return Values</span></span>

- <span data-ttu-id="457c7-721">**FX_SUCCESS** (0x00) Successful long name get</span><span class="sxs-lookup"><span data-stu-id="457c7-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="457c7-722">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet</span><span class="sxs-lookup"><span data-stu-id="457c7-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="457c7-723">**FX_IO_ERROR** (0x90) I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="457c7-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="457c7-724">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="457c7-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="457c7-725">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-726">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="457c7-727">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten</span><span class="sxs-lookup"><span data-stu-id="457c7-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="457c7-728">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-729">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare</span><span class="sxs-lookup"><span data-stu-id="457c7-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="457c7-730">**FX_CALLER_ERROR** (0x20) Anroparen är inte en tråd</span><span class="sxs-lookup"><span data-stu-id="457c7-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-731">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-731">Allowed From</span></span>

<span data-ttu-id="457c7-732">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-733">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-734">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-734">See Also</span></span>

- <span data-ttu-id="457c7-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-737">fx_directory_create</span></span>
- <span data-ttu-id="457c7-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-738">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-739">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-740">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-743">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-748">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-751">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="457c7-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="457c7-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="457c7-756">Hämtar långt namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="457c7-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-757">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="457c7-758">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-758">Description</span></span>

<span data-ttu-id="457c7-759">Den här tjänsten hämtar det långa namnet (om det finns) som är associerat med det angivna korta (8,3-format) namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="457c7-760">Det korta namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-761">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-761">Input Parameters</span></span>

- <span data-ttu-id="457c7-762">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-763">**short_name**: Pekare till källans korta namn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="457c7-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="457c7-764">**long_name:** Pekare till mål för det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="457c7-765">Om det inte finns något långt namn returneras det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="457c7-766">Obs! Målet för det långa namnet måste vara tillräckligt stort för att innehålla **FX_MAX_LONG_NAME_LEN** tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="457c7-767">**long_file_name_buffer_length:** Längden på den långa namnbufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-768">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-768">Return Values</span></span>

- <span data-ttu-id="457c7-769">**FX_SUCCESS** (0x00) Successful long name get.</span><span class="sxs-lookup"><span data-stu-id="457c7-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="457c7-770">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="457c7-771">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-772">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-773">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-774">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-775">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-776">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="457c7-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="457c7-777">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="457c7-778">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-779">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-779">Allowed From</span></span>

<span data-ttu-id="457c7-780">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-781">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name, sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-782">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-782">See Also</span></span>

- <span data-ttu-id="457c7-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-785">fx_directory_create</span></span>
- <span data-ttu-id="457c7-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-786">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-787">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-788">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-791">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-799">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="457c7-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-803">fx_directory_name_test</span></span>

<span data-ttu-id="457c7-804">Tester för katalog</span><span class="sxs-lookup"><span data-stu-id="457c7-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-805">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="457c7-806">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-806">Description</span></span>

<span data-ttu-id="457c7-807">Den här tjänsten testar om det angivna namnet är en katalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="457c7-808">I så fall returneras FX_SUCCESS en ny.</span><span class="sxs-lookup"><span data-stu-id="457c7-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-809">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-809">Input Parameters</span></span>

- <span data-ttu-id="457c7-810">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-811">**directory_name:** Pekare till namnet på katalogposten.</span><span class="sxs-lookup"><span data-stu-id="457c7-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-812">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-812">Return Values</span></span>

- <span data-ttu-id="457c7-813">**FX_SUCCESS** (0x00) Det angivna namnet är en katalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="457c7-814">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="457c7-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="457c7-815">**FX_NOT_FOUND** (0x04) Det gick inte att hitta katalogposten.</span><span class="sxs-lookup"><span data-stu-id="457c7-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="457c7-816">**FX_NOT_DIRECTORY posten** (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="457c7-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="457c7-817">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-818">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-819">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-820">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-821">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-822">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="457c7-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="457c7-823">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="457c7-824">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-825">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-825">Allowed From</span></span>

<span data-ttu-id="457c7-826">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-827">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-828">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-828">See Also</span></span>

- <span data-ttu-id="457c7-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-831">fx_directory_create</span></span>
- <span data-ttu-id="457c7-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-832">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-833">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-834">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-837">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-845">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="457c7-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="457c7-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="457c7-849">Hämtar nästa katalogpost</span><span class="sxs-lookup"><span data-stu-id="457c7-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-850">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="457c7-851">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-851">Description</span></span>

<span data-ttu-id="457c7-852">Den här tjänsten returnerar nästa postnamn i den aktuella standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-853">*Om du använder en icke-lokal sökväg är det också viktigt att förhindra (med en ThreadX-semaphore eller trådprioritetsnivå) andra programtrådar från att ändra den här katalogen medan en katalog-traverserning sker. Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="457c7-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-854">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-854">Input Parameters</span></span>

- <span data-ttu-id="457c7-855">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-856">**return_entry_name:** Pekare till mål för nästa postnamn i standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="457c7-857">Bufferten som pekar på måste vara tillräckligt stor för att innehålla den maximala storleken för FileX-namn, definierad **_av FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="457c7-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-858">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-858">Return Values</span></span>

- <span data-ttu-id="457c7-859">**FX_SUCCESS** (0x00) Lyckades nästa post</span><span class="sxs-lookup"><span data-stu-id="457c7-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="457c7-860">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-861">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="457c7-862">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-863">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-864">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-865">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-866">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-867">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-868">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-869">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-869">Allowed From</span></span>

<span data-ttu-id="457c7-870">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-871">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="457c7-872">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-872">See Also</span></span>

- <span data-ttu-id="457c7-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-875">fx_directory_create</span></span>
- <span data-ttu-id="457c7-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-876">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-877">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-878">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-881">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-887">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-889">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="457c7-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="457c7-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="457c7-894">Hämtar nästa katalogpost med fullständig information</span><span class="sxs-lookup"><span data-stu-id="457c7-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-895">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-895">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="457c7-896">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-896">Description</span></span>

<span data-ttu-id="457c7-897">Den här tjänsten hämtar nästa postnamn i standardkatalogen och kopierar det till det angivna målet.</span><span class="sxs-lookup"><span data-stu-id="457c7-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="457c7-898">Den returnerar också fullständig information om posten som anges av de ytterligare indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="457c7-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-899">*Det angivna målet måste vara tillräckligt stort för att innehålla det maximala FileX-namnet, enligt definitionen i FX_MAX_LONG_NAME_LEN*...</span><span class="sxs-lookup"><span data-stu-id="457c7-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-900">*Om du använder en icke-lokal sökväg är det viktigt att förhindra (med en ThreadX-semaphore, mutex eller prioritetsnivåändring) andra programtrådar från att ändra den här katalogen medan en katalogtratning sker. Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="457c7-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-901">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-901">Input Parameters</span></span>

- <span data-ttu-id="457c7-902">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-903">**directory_name:** Pekare till målet för namnet på en katalogpost.</span><span class="sxs-lookup"><span data-stu-id="457c7-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="457c7-904">Måste vara minst lika stor som **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="457c7-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="457c7-905">**attribut:** Om det inte är null pekar du mot målet för postens attribut som ska placeras. Attributen returneras i bitkartformat med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="457c7-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="457c7-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="457c7-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="457c7-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="457c7-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="457c7-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="457c7-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="457c7-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="457c7-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="457c7-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="457c7-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="457c7-912">**size**: Om det inte är null pekar du till målet för postens storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="457c7-913">**month**: Om det inte är null pekar du till målet för postens ändringsmånad.</span><span class="sxs-lookup"><span data-stu-id="457c7-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="457c7-914">**year**: Om det inte är null pekar du till målet för postens ändringsår.</span><span class="sxs-lookup"><span data-stu-id="457c7-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="457c7-915">**day**: Om det inte är null pekar du till målet för postens ändringsdag.</span><span class="sxs-lookup"><span data-stu-id="457c7-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="457c7-916">**hour**: Om det inte är null pekar du mot målet för postens ändringstimmar.</span><span class="sxs-lookup"><span data-stu-id="457c7-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="457c7-917">**minute**: Om det inte är null pekar du mot målet för postens ändringsminut.</span><span class="sxs-lookup"><span data-stu-id="457c7-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="457c7-918">**second**: Om det inte är null pekar du till målet för postens andra ändring.</span><span class="sxs-lookup"><span data-stu-id="457c7-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-919">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-919">Return Values</span></span>

- <span data-ttu-id="457c7-920">**FX_SUCCESS** (0x00) Lyckad katalog nästa post sök.</span><span class="sxs-lookup"><span data-stu-id="457c7-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="457c7-921">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-922">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="457c7-923">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-924">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-925">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-926">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-927">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="457c7-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="457c7-928">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-929">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare eller alla indataparametrar är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="457c7-930">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-931">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-931">Allowed From</span></span>

<span data-ttu-id="457c7-932">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-933">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-933">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-934">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-934">See Also</span></span>

- <span data-ttu-id="457c7-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-937">fx_directory_create</span></span>
- <span data-ttu-id="457c7-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-938">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-939">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-940">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-943">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-949">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-951">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="457c7-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-955">fx_directory_rename</span></span>

<span data-ttu-id="457c7-956">Byter namn på katalogen</span><span class="sxs-lookup"><span data-stu-id="457c7-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-957">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="457c7-958">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-958">Description</span></span>

<span data-ttu-id="457c7-959">Den här tjänsten ändrar katalognamnet till det angivna nya katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="457c7-960">Namnbyte görs också i förhållande till den angivna sökvägen eller standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="457c7-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="457c7-961">Om en sökväg anges i det nya katalognamnet flyttas den omdöpta katalogen effektivt till den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="457c7-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="457c7-962">Om ingen sökväg anges placeras den omdöpta katalogen i den aktuella standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="457c7-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-963">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-963">Input Parameters</span></span>

- <span data-ttu-id="457c7-964">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-965">**old_directory_name:** Pekare till aktuellt katalognamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="457c7-966">**new_directory_name:** Pekare till nytt katalognamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-967">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-967">Return Values</span></span>

- <span data-ttu-id="457c7-968">**FX_SUCCESS** (0x00) Katalogen har bytt namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="457c7-969">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-970">**FX_NOT_FOUND** (0x04) Det gick inte att hitta katalogposten.</span><span class="sxs-lookup"><span data-stu-id="457c7-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="457c7-971">**FX_NOT_DIRECTORY post** (0x0E) är inte en katalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="457c7-972">**FX_INVALID_NAME** (0x0C) Nytt katalognamn är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="457c7-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="457c7-973">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-974">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-975">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-976">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-977">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-978">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="457c7-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="457c7-979">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-980">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="457c7-981">**FX_INVALID_PATH** (0x0D) Ogiltig sökväg med katalognamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="457c7-982">**FX_ALREADY_CREATED** (0x0B) Den angivna katalogen har redan skapats.</span><span class="sxs-lookup"><span data-stu-id="457c7-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="457c7-983">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-984">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-985">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-985">Allowed From</span></span>

<span data-ttu-id="457c7-986">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-987">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="457c7-988">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-988">See Also</span></span>

- <span data-ttu-id="457c7-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-991">fx_directory_create</span></span>
- <span data-ttu-id="457c7-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-992">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-993">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-994">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-997">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="457c7-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="457c7-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="457c7-1010">Hämtar ett kort namn från ett långt namn</span><span class="sxs-lookup"><span data-stu-id="457c7-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1011">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="457c7-1012">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1012">Description</span></span>

<span data-ttu-id="457c7-1013">Den här tjänsten hämtar det korta (8.3-format) namnet som är associerat med det angivna långa namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="457c7-1014">Det långa namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1015">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1015">Input Parameters</span></span>

- <span data-ttu-id="457c7-1016">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-1017">**long_name:** Pekare till källans långa namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="457c7-1018">**short_name**: Pekare till målets kortnamn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="457c7-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="457c7-1019">Observera att målet för det korta namnet måste vara tillräckligt stort för att innehålla 14 tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1020">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1020">Return Values</span></span>

- <span data-ttu-id="457c7-1021">**FX_SUCCESS** (0x00) Lyckades kortnamn get.</span><span class="sxs-lookup"><span data-stu-id="457c7-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="457c7-1022">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="457c7-1023">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1024">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1025">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1026">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1027">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1028">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1029">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-1030">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="457c7-1031">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1032">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1032">Allowed From</span></span>

<span data-ttu-id="457c7-1033">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1034">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1035">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1035">See Also</span></span>

- <span data-ttu-id="457c7-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1038">fx_directory_create</span></span>
- <span data-ttu-id="457c7-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1041">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1053">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="457c7-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="457c7-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="457c7-1057">Hämtar ett kort namn från ett långt namn</span><span class="sxs-lookup"><span data-stu-id="457c7-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1058">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="457c7-1059">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1059">Description</span></span>

<span data-ttu-id="457c7-1060">Den här tjänsten hämtar det korta (8.3-format) namnet som är associerat med det angivna långa namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="457c7-1061">Det långa namnet kan vara antingen ett filnamn eller ett katalognamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1062">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1062">Input Parameters</span></span>

- <span data-ttu-id="457c7-1063">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-1064">**long_name:** Pekare till källans långa namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="457c7-1065">**short_name**: Pekare till målets kortnamn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="457c7-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="457c7-1066">Obs! Målet för det korta namnet måste vara tillräckligt stort för att innehålla 14 tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="457c7-1067">**short_file_name_length:** Längden på kort namnbufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1068">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1068">Return Values</span></span>

- <span data-ttu-id="457c7-1069">**FX_SUCCESS** (0x00) Lyckades kortnamn get.</span><span class="sxs-lookup"><span data-stu-id="457c7-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="457c7-1070">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det långa namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="457c7-1071">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1072">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1073">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1074">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1075">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1076">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1077">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-1078">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="457c7-1079">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1080">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1080">Allowed From</span></span>

<span data-ttu-id="457c7-1081">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1082">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1083">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1083">See Also</span></span>

- <span data-ttu-id="457c7-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1086">fx_directory_create</span></span>
- <span data-ttu-id="457c7-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1089">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1101">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="457c7-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="457c7-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="457c7-1105">Aktiverar den feltoleranta tjänsten</span><span class="sxs-lookup"><span data-stu-id="457c7-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1106">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="457c7-1107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1107">Description</span></span>

<span data-ttu-id="457c7-1108">Den här tjänsten aktiverar den feltoleranta modulen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="457c7-1109">När du startar identifierar den feltoleranta modulen huruvida filsystemet är under feltoleransskydd i FileX.</span><span class="sxs-lookup"><span data-stu-id="457c7-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="457c7-1110">Om den inte är det hittar tjänsten tillgängliga sektorer i filsystemet för att lagra loggar på filsystemtransaktioner.</span><span class="sxs-lookup"><span data-stu-id="457c7-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="457c7-1111">Om filsystemet är under Ett feltolerant FileX-skydd tillämpar det loggarna på filsystemet för att upprätthålla dess integritet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1112">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1112">Input Parameters</span></span>

- <span data-ttu-id="457c7-1113">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-1114">**memory_ptr:** Pekare till ett minnesblock som används av den feltoleranta modulen som ett minne som är försnåe.</span><span class="sxs-lookup"><span data-stu-id="457c7-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="457c7-1115">**memory_size:** Storleken på det scratch-minnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="457c7-1116">För att feltoleranta ska fungera korrekt ska den scratch-minnesstorleken vara minst 3072 byte och måste vara flera av sektorstorleken.</span><span class="sxs-lookup"><span data-stu-id="457c7-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1117">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1117">Return Values</span></span>

- <span data-ttu-id="457c7-1118">**FX_SUCCESS** (0x00) Feltolerans har aktiverats.</span><span class="sxs-lookup"><span data-stu-id="457c7-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="457c7-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) för liten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="457c7-1120">**FX_BOOT_ERROR** (0x01) Startsektorfel.</span><span class="sxs-lookup"><span data-stu-id="457c7-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="457c7-1121">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1122">**FX_NO_MORE_ENTRIES** (0x0F) Inget mer ledigt kluster tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="457c7-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="457c7-1123">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="457c7-1124">**FX_SECTOR_INVALID** (0x89) Sektor är ogiltig</span><span class="sxs-lookup"><span data-stu-id="457c7-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="457c7-1125">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1126">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-1127">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1128">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1128">Allowed From</span></span>

<span data-ttu-id="457c7-1129">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1130">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="457c7-1131">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1131">See Also</span></span>

- <span data-ttu-id="457c7-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-1132">fx_system_initialize</span></span>
- <span data-ttu-id="457c7-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-1133">fx_media_abort</span></span>
- <span data-ttu-id="457c7-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-1135">fx_media_check</span></span>
- <span data-ttu-id="457c7-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1136">fx_media_close</span></span>
- <span data-ttu-id="457c7-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-1140">fx_media_flush</span></span>
- <span data-ttu-id="457c7-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-1141">fx_media_format</span></span>
- <span data-ttu-id="457c7-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1142">fx_media_open</span></span>
- <span data-ttu-id="457c7-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1144">fx_media_read</span></span>
- <span data-ttu-id="457c7-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-1145">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="457c7-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1149">fx_file_allocate</span></span>

<span data-ttu-id="457c7-1150">Allokerar utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="457c7-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="457c7-1152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1152">Description</span></span>

<span data-ttu-id="457c7-1153">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="457c7-1154">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="457c7-1155">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="457c7-1156">Om du vill allokera mer än 4 GB utrymme ska programmet använda tjänsten *fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="457c7-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1157">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1157">Input Parameters</span></span>

- <span data-ttu-id="457c7-1158">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-1159">**size**: Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1160">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1160">Return Values</span></span>

- <span data-ttu-id="457c7-1161">**FX_SUCCESS** (0x00) Lyckad filallokering.</span><span class="sxs-lookup"><span data-stu-id="457c7-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="457c7-1162">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-1163">**FX_FAT_READ_ERROR** (0x03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1164">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1165">**FX_NOT_OPEN** (0x07) Den angivna filen är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-1166">**FX_NO_MORE_ENTRIES** (0x0F) Inget mer ledigt kluster tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="457c7-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="457c7-1167">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="457c7-1168">**FX_SECTOR_INVALID** (0x89) Sektor är ogiltig</span><span class="sxs-lookup"><span data-stu-id="457c7-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="457c7-1169">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1170">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1171">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-1172">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1173">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1173">Allowed From</span></span>

<span data-ttu-id="457c7-1174">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1175">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1176">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1176">See Also</span></span>

- <span data-ttu-id="457c7-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1180">fx_file_close – fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="457c7-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1182">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1189">fx_file_open– fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="457c7-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1191">fx_file_rename – fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="457c7-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1192">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1194">fx_file_write</span></span>
- <span data-ttu-id="457c7-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="457c7-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="457c7-1201">Läser filattribut</span><span class="sxs-lookup"><span data-stu-id="457c7-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1202">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-1203">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1203">Description</span></span>

<span data-ttu-id="457c7-1204">Den här tjänsten läser filens attribut från det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1205">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1205">Input Parameters</span></span>

- <span data-ttu-id="457c7-1206">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-1207">**file_name:** Pekare till namnet på den begärda filen (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="457c7-1208">**attributes_ptr:** Pekare till målet för filens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="457c7-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="457c7-1209">Filattributen returneras i ett bit-map-format med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="457c7-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="457c7-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="457c7-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="457c7-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="457c7-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="457c7-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="457c7-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="457c7-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="457c7-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="457c7-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="457c7-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1216">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1216">Return Values</span></span>

- <span data-ttu-id="457c7-1217">**FX_SUCCESS** (0x00) Lyckad attributläsning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="457c7-1218">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-1219">**FX_NOT_FOUND** (0x04) Den angivna filen hittades inte på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="457c7-1220">**FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="457c7-1221">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1222">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1223">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1224">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1225">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1226">**FX_PTR_ERROR** (0x18) Ogiltig media eller attribut pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="457c7-1227">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1228">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1228">Allowed From</span></span>

<span data-ttu-id="457c7-1229">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1230">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="457c7-1231">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1231">See Also</span></span>

- <span data-ttu-id="457c7-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1232">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1235">fx_file_close– fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="457c7-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1237">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1244">fx_file_open</span></span>
- <span data-ttu-id="457c7-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1245">fx_file_read</span></span>
- <span data-ttu-id="457c7-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1247">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1248">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1249">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1251">fx_file_write</span></span>
- <span data-ttu-id="457c7-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="457c7-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="457c7-1258">Anger filattribut</span><span class="sxs-lookup"><span data-stu-id="457c7-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1259">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="457c7-1260">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1260">Description</span></span>

<span data-ttu-id="457c7-1261">Den här tjänsten anger filens attribut till de som anges av anroparen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-1262">*Programmet kan bara ändra en delmängd av filens attribut med den här tjänsten. Om du försöker ange ytterligare attribut resulterar det i ett fel.*</span><span class="sxs-lookup"><span data-stu-id="457c7-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1263">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1263">Input Parameters</span></span>

- <span data-ttu-id="457c7-1264">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-1265">**file_name:** Pekare till namnet på den begärda filen\*\* (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="457c7-1266">**attribut:** De nya attributen för filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="457c7-1267">De giltiga filattributen definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="457c7-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="457c7-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="457c7-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="457c7-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="457c7-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="457c7-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="457c7-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1272">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1272">Return Values</span></span>

- <span data-ttu-id="457c7-1273">**FX_SUCCESS** (0x00) Lyckad attributuppsättning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="457c7-1274">**FX_ACCESS_ERROR** (0x06) Filen är öppen och kan inte ha sina attribut inställda.</span><span class="sxs-lookup"><span data-stu-id="457c7-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="457c7-1275">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1276">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1277">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-1278">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i FAT-tabellen eller exFAT-klusterkartan.</span><span class="sxs-lookup"><span data-stu-id="457c7-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="457c7-1279">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="457c7-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="457c7-1280">**FX_NOT_FOUND** (0x04) Den angivna filen hittades inte på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="457c7-1281">**FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="457c7-1282">**FX_SECTOR_INVALID** (0x89)-sektor är ogiltig</span><span class="sxs-lookup"><span data-stu-id="457c7-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="457c7-1283">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1284">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1285">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-1286">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-1287">**FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.</span><span class="sxs-lookup"><span data-stu-id="457c7-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="457c7-1288">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1289">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1289">Allowed From</span></span>

<span data-ttu-id="457c7-1290">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1291">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="457c7-1292">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1292">See Also</span></span>

- <span data-ttu-id="457c7-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1293">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1296">fx_file_close</span></span>
- <span data-ttu-id="457c7-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1297">fx_file_create</span></span>
- <span data-ttu-id="457c7-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1299">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1306">fx_file_open</span></span>
- <span data-ttu-id="457c7-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1307">fx_file_read</span></span>
- <span data-ttu-id="457c7-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1309">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1310">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1311">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1313">fx_file_write</span></span>
- <span data-ttu-id="457c7-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="457c7-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="457c7-1320">Bästa möjliga tid för att allokera utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="457c7-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1321">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="457c7-1322">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1322">Description</span></span>

<span data-ttu-id="457c7-1323">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="457c7-1324">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="457c7-1325">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="457c7-1326">Om det inte finns tillräckligt många kluster i följd tillgängliga på mediet länkar den här tjänsten det största tillgängliga blocket med kluster i följd till filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="457c7-1327">Mängden utrymme som faktiskt allokerats till filen returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="457c7-1328">Om du vill allokera mer än 4 GB utrymme ska programmet använda tjänsten *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="457c7-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1329">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1329">Input Parameters</span></span>

- <span data-ttu-id="457c7-1330">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-1331">**size**: Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1332">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1332">Return Values</span></span>

- <span data-ttu-id="457c7-1333">**FX_SUCCESS** (0x00) Lyckad filallokering med bästa resultat.</span><span class="sxs-lookup"><span data-stu-id="457c7-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="457c7-1334">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-1335">**FX_NOT_OPEN** (0x07) Den angivna filen är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-1336">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="457c7-1337">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1338">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1339">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1340">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1341">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1342">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1343">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare eller mål.</span><span class="sxs-lookup"><span data-stu-id="457c7-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="457c7-1344">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1345">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1345">Allowed From</span></span>

<span data-ttu-id="457c7-1346">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1347">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="457c7-1348">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1348">See Also</span></span>

- <span data-ttu-id="457c7-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1349">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1352">fx_file_close</span></span>
- <span data-ttu-id="457c7-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1353">fx_file_create</span></span>
- <span data-ttu-id="457c7-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1355">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1362">fx_file_open</span></span>
- <span data-ttu-id="457c7-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1363">fx_file_read</span></span>
- <span data-ttu-id="457c7-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1365">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1366">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1367">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1369">fx_file_write</span></span>
- <span data-ttu-id="457c7-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="457c7-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1375">fx_file_close</span></span>

<span data-ttu-id="457c7-1376">Stänger filen</span><span class="sxs-lookup"><span data-stu-id="457c7-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1377">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-1378">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1378">Description</span></span>

<span data-ttu-id="457c7-1379">Den här tjänsten stänger den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1379">This service closes the specified file.</span></span> <span data-ttu-id="457c7-1380">Om filen var öppen för skrivning och om den ändrades slutför den här tjänsten filändringsprocessen genom att uppdatera dess katalogpost med den nya storleken och systemets aktuella tid och datum.</span><span class="sxs-lookup"><span data-stu-id="457c7-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1381">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1381">Input Parameters</span></span>

- <span data-ttu-id="457c7-1382">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1383">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1383">Return Values</span></span>

- <span data-ttu-id="457c7-1384">**FX_SUCCESS** (0x00) Lyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="457c7-1385">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="457c7-1386">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1387">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1388">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1389">**FX_PTR_ERROR** (0x18) Pekaren Ogiltig media eller attribut.</span><span class="sxs-lookup"><span data-stu-id="457c7-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="457c7-1390">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1391">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1391">Allowed From</span></span>

<span data-ttu-id="457c7-1392">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1393">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1394">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1394">See Also</span></span>

- <span data-ttu-id="457c7-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1395">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1399">fx_file_create</span></span>
- <span data-ttu-id="457c7-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1401">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1408">fx_file_open</span></span>
- <span data-ttu-id="457c7-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1409">fx_file_read</span></span>
- <span data-ttu-id="457c7-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1411">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1412">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1413">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1415">fx_file_write</span></span>
- <span data-ttu-id="457c7-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="457c7-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1421">fx_file_create</span></span>

<span data-ttu-id="457c7-1422">Skapar fil</span><span class="sxs-lookup"><span data-stu-id="457c7-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1423">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="457c7-1424">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1424">Description</span></span>

<span data-ttu-id="457c7-1425">Den här tjänsten skapar den angivna filen i standardkatalogen eller i den katalogsökväg som medföljer filnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-1426">*Den här tjänsten skapar en fil med längden noll, det vill säga inga kluster allokerade. Allokering sker automatiskt vid efterföljande fil skrivningar eller kan göras i förväg med fx_file_allocate-tjänsten eller fx_file_extended_allocate utrymme över 4 GB).*</span><span class="sxs-lookup"><span data-stu-id="457c7-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1427">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1427">Input Parameters</span></span>

- <span data-ttu-id="457c7-1428">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-1429">**file_name:** Pekare till namnet på filen som ska skapas (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1430">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1430">Return Values</span></span>

- <span data-ttu-id="457c7-1431">**FX_SUCCESS** (0x00) Lyckades fil skapas.</span><span class="sxs-lookup"><span data-stu-id="457c7-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="457c7-1432">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-1433">**FX_ALREADY_CREATED** (0x0B) Den angivna filen har redan skapats.</span><span class="sxs-lookup"><span data-stu-id="457c7-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="457c7-1434">**FX_NO_MORE_SPACE** (0x0A) Det finns antingen inga fler poster i rotkatalogen eller så finns det inga fler kluster tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="457c7-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="457c7-1435">**FX_INVALID_PATH** (0x0D) Ogiltig sökväg medföljer filnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="457c7-1436">**FX_INVALID_NAME** (0x0C) är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="457c7-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="457c7-1437">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1438">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1439">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1440">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1441">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1442">**FX_MEDIA_INVALID** (0x02)Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="457c7-1443">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1444">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="457c7-1445">**FX_PTR_ERROR** (0x18) Felaktig media- eller filnamnspekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="457c7-1446">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1447">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1447">Allowed From</span></span>

<span data-ttu-id="457c7-1448">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1449">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1450">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1450">See Also</span></span>
- <span data-ttu-id="457c7-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1451">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1455">fx_file_close</span></span>
- <span data-ttu-id="457c7-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1457">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1464">fx_file_open</span></span>
- <span data-ttu-id="457c7-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1465">fx_file_read</span></span>
- <span data-ttu-id="457c7-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1467">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1468">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1469">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1471">fx_file_write</span></span>
- <span data-ttu-id="457c7-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="457c7-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="457c7-1478">Anger fildatum och -tid</span><span class="sxs-lookup"><span data-stu-id="457c7-1478">Sets file date and time</span></span>

<span data-ttu-id="457c7-1479">Ange fildatum och -tid</span><span class="sxs-lookup"><span data-stu-id="457c7-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1480">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1480">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="457c7-1481">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1481">Description</span></span>

<span data-ttu-id="457c7-1482">Den här tjänsten anger datum och tid för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="457c7-1483">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1483">Input Parameters</span></span>

- <span data-ttu-id="457c7-1484">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-1485">**file_name**: Pekare till namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="457c7-1486">**year**: Värde för år (inklusive 1980–2107).</span><span class="sxs-lookup"><span data-stu-id="457c7-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="457c7-1487">**month**: Värdet för month (1–12 inklusivt).</span><span class="sxs-lookup"><span data-stu-id="457c7-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="457c7-1488">**day**: Värdet för day (1–31 inklusivt).</span><span class="sxs-lookup"><span data-stu-id="457c7-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="457c7-1489">**hour**: Värdet för hour (0–23 inklusivt).</span><span class="sxs-lookup"><span data-stu-id="457c7-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="457c7-1490">**minute**: Minutvärdet (inklusive 0–59).</span><span class="sxs-lookup"><span data-stu-id="457c7-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="457c7-1491">**second**: Värdet för sekund (inklusive 0–59).</span><span class="sxs-lookup"><span data-stu-id="457c7-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1492">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1492">Return Values</span></span>

- <span data-ttu-id="457c7-1493">**FX_SUCCESS** (0x00) Datum/tid har angetts.</span><span class="sxs-lookup"><span data-stu-id="457c7-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="457c7-1494">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-1495">**FX_NOT_FOUND** (0x04) Hittades inte.</span><span class="sxs-lookup"><span data-stu-id="457c7-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="457c7-1496">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="457c7-1497">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1498">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1499">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1500">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="457c7-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="457c7-1501">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1502">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1503">**FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="457c7-1504">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="457c7-1505">**FX_INVALID_YEAR** (0x12) År är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="457c7-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="457c7-1506">**FX_INVALID_MONTH** (0x13) Månad är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="457c7-1507">**FX_INVALID_DAY** (0x14) Day är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="457c7-1508">**FX_INVALID_HOUR** (0x15) Timme är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="457c7-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="457c7-1509">**FX_INVALID_MINUTE** (0x16) Minut är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="457c7-1510">**FX_INVALID_SECOND** (0x17) Sekund är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="457c7-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1511">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1511">Allowed From</span></span>

<span data-ttu-id="457c7-1512">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1513">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="457c7-1514">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1514">See Also</span></span>

- <span data-ttu-id="457c7-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1515">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1519">fx_file_close</span></span>
- <span data-ttu-id="457c7-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1520">fx_file_create</span></span>
- <span data-ttu-id="457c7-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1521">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1528">fx_file_open</span></span>
- <span data-ttu-id="457c7-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1529">fx_file_read</span></span>
- <span data-ttu-id="457c7-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1531">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1532">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1533">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1535">fx_file_write</span></span>
- <span data-ttu-id="457c7-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="457c7-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="457c7-1542">Tar bort fil</span><span class="sxs-lookup"><span data-stu-id="457c7-1542">Deletes file</span></span>

<span data-ttu-id="457c7-1543">Filborttagning</span><span class="sxs-lookup"><span data-stu-id="457c7-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1544">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="457c7-1545">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1545">Description</span></span>

<span data-ttu-id="457c7-1546">Den här tjänsten tar bort den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="457c7-1547">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1547">Input Parameters</span></span>

- <span data-ttu-id="457c7-1548">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-1549">**file_name:** Pekare till namnet på filen som ska tas bort (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1550">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1550">Return Values</span></span>

- <span data-ttu-id="457c7-1551">**FX_SUCCESS** (0x00) Borttagningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="457c7-1552">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-1553">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="457c7-1554">**FX_NOT_A_FILE** (0x05) Det angivna filnamnet var en katalog eller volym.</span><span class="sxs-lookup"><span data-stu-id="457c7-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="457c7-1555">**FX_ACCESS_ERROR** (0x06) Angiven fil är öppen för tillfället.</span><span class="sxs-lookup"><span data-stu-id="457c7-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="457c7-1556">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1557">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1558">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1559">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1560">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1561">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1562">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1563">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-1564">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-1565">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1566">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1566">Allowed From</span></span>

<span data-ttu-id="457c7-1567">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1568">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1569">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1569">See Also</span></span>

- <span data-ttu-id="457c7-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1570">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1574">fx_file_close</span></span>
- <span data-ttu-id="457c7-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1575">fx_file_create</span></span>
- <span data-ttu-id="457c7-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1583">fx_file_open</span></span>
- <span data-ttu-id="457c7-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1584">fx_file_read</span></span>
- <span data-ttu-id="457c7-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1586">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1587">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1588">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1590">fx_file_write</span></span>
- <span data-ttu-id="457c7-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="457c7-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="457c7-1597">Allokerar utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="457c7-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1598">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="457c7-1599">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1599">Description</span></span>

<span data-ttu-id="457c7-1600">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="457c7-1601">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="457c7-1602">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="457c7-1603">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="457c7-1604">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan allokera utrymme i förväg över 4 GB. </span><span class="sxs-lookup"><span data-stu-id="457c7-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1605">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1605">Input Parameters</span></span>

- <span data-ttu-id="457c7-1606">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-1607">**size**: Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1608">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1608">Return Values</span></span>

- <span data-ttu-id="457c7-1609">**FX_SUCCESS** (0x00) Lyckad filallokering.</span><span class="sxs-lookup"><span data-stu-id="457c7-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="457c7-1610">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-1611">**FX_NOT_OPEN** (0x07) Den angivna filen är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-1612">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="457c7-1613">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1614">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1615">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1616">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1617">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1618">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1619">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-1620">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1621">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1621">Allowed From</span></span>

<span data-ttu-id="457c7-1622">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1623">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1624">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1624">See Also</span></span>

- <span data-ttu-id="457c7-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1625">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1629">fx_file_close</span></span>
- <span data-ttu-id="457c7-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1630">fx_file_create</span></span>
- <span data-ttu-id="457c7-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1632">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1638">fx_file_open</span></span>
- <span data-ttu-id="457c7-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1639">fx_file_read</span></span>
- <span data-ttu-id="457c7-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1641">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1642">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1643">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1645">fx_file_write</span></span>
- <span data-ttu-id="457c7-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="457c7-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="457c7-1652">Bästa möjliga tid för att allokera utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="457c7-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1653">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="457c7-1654">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1654">Description</span></span>

<span data-ttu-id="457c7-1655">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="457c7-1656">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="457c7-1657">Resultatet avrundas sedan uppåt till nästa helt kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="457c7-1658">Om det inte finns tillräckligt många kluster i följd tillgängliga på mediet länkar den här tjänsten det största tillgängliga blocket med kluster i följd till filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="457c7-1659">Mängden utrymme som faktiskt allokerats till filen returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="457c7-1660">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="457c7-1661">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan allokera utrymme i förväg över 4 GB. </span><span class="sxs-lookup"><span data-stu-id="457c7-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1662">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1662">Input Parameters</span></span>

- <span data-ttu-id="457c7-1663">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-1664">**size**: Antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1665">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1665">Return Values</span></span>

- <span data-ttu-id="457c7-1666">**FX_SUCCESS** (0x00) Lyckad filallokering.</span><span class="sxs-lookup"><span data-stu-id="457c7-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="457c7-1667">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-1668">**FX_NOT_OPEN** (0x07) Den angivna filen är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-1669">**FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="457c7-1670">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1671">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1672">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1673">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1674">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1675">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1676">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-1677">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1678">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1678">Allowed From</span></span>

<span data-ttu-id="457c7-1679">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1680">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1680">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-1681">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1681">See Also</span></span>

- <span data-ttu-id="457c7-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1682">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1686">fx_file_close</span></span>
- <span data-ttu-id="457c7-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1687">fx_file_create</span></span>
- <span data-ttu-id="457c7-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1689">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1695">fx_file_open</span></span>
- <span data-ttu-id="457c7-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1696">fx_file_read</span></span>
- <span data-ttu-id="457c7-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1698">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1699">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1700">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1702">fx_file_write</span></span>
- <span data-ttu-id="457c7-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="457c7-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="457c7-1709">Positioner till en relativ byteförskjutning</span><span class="sxs-lookup"><span data-stu-id="457c7-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1710">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="457c7-1711">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1711">Description</span></span>

<span data-ttu-id="457c7-1712">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna relativa byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="457c7-1713">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="457c7-1714">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="457c7-1715">Parametern *byte_offset* tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan flytta läs-/skrivpekaren över 4 GB.</span><span class="sxs-lookup"><span data-stu-id="457c7-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-1716">*Om sökåtgärden försöker att söka förbi slutet av filen placeras filens läs-/skriv pekare i slutet av filen. Om sökåtgärden försöker placera sig förbi början av filen placeras däremot filens läs-/skriv pekare i början av filen.*</span><span class="sxs-lookup"><span data-stu-id="457c7-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1717">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1717">Input Parameters</span></span>

- <span data-ttu-id="457c7-1718">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-1719">**byte_offset:** Önskad relativ byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="457c7-1720">**seek_from:** Riktningen och platsen för var du ska utföra det relativa söket.</span><span class="sxs-lookup"><span data-stu-id="457c7-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="457c7-1721">Giltiga sökalternativ definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="457c7-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="457c7-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="457c7-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="457c7-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="457c7-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="457c7-1725">FX_SEEK_BACK (0x03) Om FX_SEEK_BEGIN har angetts utförs sökåtgärden från början av filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="457c7-1726">Om FX_SEEK_END har angetts utförs sökåtgärden bakåt från slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="457c7-1727">Om FX_SEEK_FORWARD har angetts utförs sökåtgärden framåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="457c7-1728">Om FX_SEEK_BACK har angetts utförs sökåtgärden bakåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1729">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1729">Return Values</span></span>

- <span data-ttu-id="457c7-1730">**FX_SUCCESS** (0x00) Lyckad relativ filsökning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="457c7-1731">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-1732">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1733">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1734">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1735">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1736">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-1737">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1738">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1738">Allowed From</span></span>

<span data-ttu-id="457c7-1739">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1740">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1741">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1741">See Also</span></span>

- <span data-ttu-id="457c7-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1742">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1746">fx_file_close</span></span>
- <span data-ttu-id="457c7-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1747">fx_file_create</span></span>
- <span data-ttu-id="457c7-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1749">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1755">fx_file_open</span></span>
- <span data-ttu-id="457c7-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1756">fx_file_read</span></span>
- <span data-ttu-id="457c7-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1758">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1759">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1760">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1762">fx_file_write</span></span>
- <span data-ttu-id="457c7-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="457c7-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="457c7-1769">Positioner till byte-förskjutning</span><span class="sxs-lookup"><span data-stu-id="457c7-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1770">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="457c7-1771">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1771">Description</span></span>

<span data-ttu-id="457c7-1772">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="457c7-1773">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="457c7-1774">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="457c7-1775">Parametern *byte_offset* tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan flytta läs-/skrivpekaren över 4 GB.</span><span class="sxs-lookup"><span data-stu-id="457c7-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1776">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1776">Input Parameters</span></span>

- <span data-ttu-id="457c7-1777">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-1778">**byte_offset:** Önskad byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="457c7-1779">Värdet noll placerar läs-/skriv pekaren i början av filen, medan ett värde som är större än filens storlek placerar läs-/skriv pekaren i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1780">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1780">Return Values</span></span>

- <span data-ttu-id="457c7-1781">**FX_SUCCESS** (0x00) Lyckad filsökning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="457c7-1782">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="457c7-1783">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1784">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1785">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1786">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1787">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-1788">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1789">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1789">Allowed From</span></span>

<span data-ttu-id="457c7-1790">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1791">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1792">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1792">See Also</span></span>

- <span data-ttu-id="457c7-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1793">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1797">fx_file_close</span></span>
- <span data-ttu-id="457c7-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1798">fx_file_create</span></span>
- <span data-ttu-id="457c7-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1800">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1806">fx_file_open– fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="457c7-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1808">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1809">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1810">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1812">fx_file_write</span></span>
- <span data-ttu-id="457c7-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="457c7-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="457c7-1819">Trunkeringsfil</span><span class="sxs-lookup"><span data-stu-id="457c7-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1820">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="457c7-1821">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1821">Description</span></span>

<span data-ttu-id="457c7-1822">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="457c7-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="457c7-1823">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="457c7-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="457c7-1824">Inget av de mediekluster som är associerade med filen släpps.</span><span class="sxs-lookup"><span data-stu-id="457c7-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-1825">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="457c7-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="457c7-1826">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="457c7-1827">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta utanför 4 GB intervall. </span><span class="sxs-lookup"><span data-stu-id="457c7-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1828">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1828">Input Parameters</span></span>

- <span data-ttu-id="457c7-1829">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-1830">**storlek:** Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="457c7-1830">**size**: New file size.</span></span> <span data-ttu-id="457c7-1831">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="457c7-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1832">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1832">Return Values</span></span>

- <span data-ttu-id="457c7-1833">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="457c7-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="457c7-1834">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="457c7-1835">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-1836">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1837">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1838">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1839">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1840">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1841">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="457c7-1842">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-1843">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1844">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1844">Allowed From</span></span>

<span data-ttu-id="457c7-1845">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1846">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1847">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1847">See Also</span></span>

- <span data-ttu-id="457c7-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1848">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1852">fx_file_close</span></span>
- <span data-ttu-id="457c7-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1853">fx_file_create</span></span>
- <span data-ttu-id="457c7-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1855">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1861">fx_file_open</span></span>
- <span data-ttu-id="457c7-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1862">fx_file_read</span></span>
- <span data-ttu-id="457c7-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1864">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1865">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1866">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1868">fx_file_write</span></span>
- <span data-ttu-id="457c7-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="457c7-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="457c7-1875">Trunkerar fil- och versionskluster</span><span class="sxs-lookup"><span data-stu-id="457c7-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1876">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="457c7-1877">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1877">Description</span></span>

<span data-ttu-id="457c7-1878">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="457c7-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="457c7-1879">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="457c7-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="457c7-1880">Till skillnad ***fx_file_extended_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-1881">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="457c7-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="457c7-1882">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="457c7-1883">Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta utanför 4 GB intervall. </span><span class="sxs-lookup"><span data-stu-id="457c7-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1884">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1884">Input Parameters</span></span>

- <span data-ttu-id="457c7-1885">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-1886">**storlek:** Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="457c7-1886">**size**: New file size.</span></span> <span data-ttu-id="457c7-1887">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="457c7-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1888">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1888">Return Values</span></span>

- <span data-ttu-id="457c7-1889">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="457c7-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="457c7-1890">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-1891">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-1892">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1893">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-1894">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1895">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-1896">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1897">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1898">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-1899">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-1900">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1901">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1901">Allowed From</span></span>

<span data-ttu-id="457c7-1902">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1903">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1904">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1904">See Also</span></span>

- <span data-ttu-id="457c7-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1905">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-1909">fx_file_close</span></span>
- <span data-ttu-id="457c7-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1910">fx_file_create</span></span>
- <span data-ttu-id="457c7-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1912">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1918">fx_file_open</span></span>
- <span data-ttu-id="457c7-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1919">fx_file_read</span></span>
- <span data-ttu-id="457c7-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1921">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1922">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1923">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1925">fx_file_write</span></span>
- <span data-ttu-id="457c7-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="457c7-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-1931">fx_file_open</span></span>

<span data-ttu-id="457c7-1932">Öppnar filen</span><span class="sxs-lookup"><span data-stu-id="457c7-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1933">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="457c7-1934">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1934">Description</span></span>

<span data-ttu-id="457c7-1935">Den här tjänsten öppnar den angivna filen för läsning eller skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="457c7-1936">En fil kan öppnas för läsning flera gånger, medan en fil bara kan öppnas för skrivning en gång tills skrivaren stänger filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-1937">*Var försiktig om en fil är öppen samtidigt för läsning och skrivning. Filskrivning som utförs när en fil öppnas samtidigt för läsning kanske inte kan ses av läsaren, såvida inte läsaren stänger och öppnar filen igen för läsning. På samma sätt bör filskrivaren vara försiktig när du använder tjänster för trunkering av filer. Om en fil trunkeras av skrivaren kan läsare av samma fil returnera ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="457c7-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-1938">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-1938">Input Parameters</span></span>

- <span data-ttu-id="457c7-1939">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-1940">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-1941">**file_name:** Pekare till namnet på filen som ska öppnas (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="457c7-1942">**open_type:** Typ av fil som är öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="457c7-1943">Giltiga alternativ för öppen typ är:</span><span class="sxs-lookup"><span data-stu-id="457c7-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="457c7-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="457c7-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="457c7-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="457c7-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="457c7-1947">Att öppna filer med FX_OPEN_FOR_READ och FX_OPEN_FOR_READ_FAST liknar följande:</span><span class="sxs-lookup"><span data-stu-id="457c7-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="457c7-1948">FX_OPEN_FOR_READ verifiering att den länkade listan över kluster som utgör filen är intakt och FX_OPEN_FOR_READ_FAST utför inte den här verifieringen, vilket gör den snabbare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-1949">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1949">Return Values</span></span>

- <span data-ttu-id="457c7-1950">**FX_SUCCESS** (0x00) Filen lyckades öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="457c7-1951">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-1952">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="457c7-1953">**FX_NOT_A_FILE** (0x05) Det angivna filnamnet var en katalog eller volym.</span><span class="sxs-lookup"><span data-stu-id="457c7-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="457c7-1954">**FX_FILE_CORRUPT** (0x08) Angiven fil är skadad och det gick inte att öppna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="457c7-1955">**FX_ACCESS_ERROR** (0x06) Angiven fil är redan öppen eller öppen typ är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="457c7-1956">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-1957">**FX_MEDIA_INVALID** (0x02) Ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="457c7-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="457c7-1958">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-1959">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-1960">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-1961">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="457c7-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="457c7-1962">**FX_PTR_ERROR** (0x18) Ogiltig media eller fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="457c7-1963">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-1964">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-1964">Allowed From</span></span>

<span data-ttu-id="457c7-1965">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-1966">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-1967">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-1967">See Also</span></span>

- <span data-ttu-id="457c7-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1968">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1972">fx_file_close – fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="457c7-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-1974">fx_file_delete</span></span>
- <span data-ttu-id="457c7-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1981">fx_file_read</span></span>
- <span data-ttu-id="457c7-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1983">fx_file_rename</span></span>
- <span data-ttu-id="457c7-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-1984">fx_file_seek</span></span>
- <span data-ttu-id="457c7-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-1985">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-1987">fx_file_write</span></span>
- <span data-ttu-id="457c7-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="457c7-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-1993">fx_file_read</span></span>

<span data-ttu-id="457c7-1994">Läser byte från fil</span><span class="sxs-lookup"><span data-stu-id="457c7-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-1995">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="457c7-1996">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-1996">Description</span></span>

<span data-ttu-id="457c7-1997">Den här tjänsten läser byte från filen och lagrar dem i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="457c7-1998">När läsningen är klar justeras filens interna läs pekare så att den pekar vid nästa byte i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="457c7-1999">Om det finns färre byte kvar i begäran lagras bara återstående byte i bufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="457c7-2000">I vilket fall som helst returneras det totala antalet byte som placerats i bufferten till anroparen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2001">*Programmet måste se till att den angivna bufferten kan lagra det angivna antalet begärda byte.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2002">*Snabbare prestanda uppnås om målbufferten ligger på en lång ordgräns och den begärda storleken är jämnt delbar efter sizeof(\*\*ULONG).*\*\*</span><span class="sxs-lookup"><span data-stu-id="457c7-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2003">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2003">Input Parameters</span></span>

- <span data-ttu-id="457c7-2004">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-2005">**buffer_ptr:** Pekare till målbufferten för läsningen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="457c7-2006">**request_size:** Maximalt antal byte som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="457c7-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="457c7-2007">**actual_size:** Pekare till variabeln för det faktiska antalet lästa byte i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2008">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2008">Return Values</span></span>

- <span data-ttu-id="457c7-2009">**FX_SUCCESS** (0x00) Filen har lästs.</span><span class="sxs-lookup"><span data-stu-id="457c7-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="457c7-2010">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="457c7-2011">**FX_FILE_CORRUPT** (0x08) Angiven fil är skadad och läsningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="457c7-2012">**FX_END_OF_FILE** (0x09) Slutet av filen har nåtts.</span><span class="sxs-lookup"><span data-stu-id="457c7-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="457c7-2013">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2014">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-2015">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2016">**FX_PTR_ERROR** (0x18) Ogiltig fil eller buffertpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="457c7-2017">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2018">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2018">Allowed From</span></span>

<span data-ttu-id="457c7-2019">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2020">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2020">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="457c7-2021">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2021">See Also</span></span>

- <span data-ttu-id="457c7-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="457c7-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="457c7-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="457c7-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="457c7-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="457c7-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="457c7-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="457c7-2026">fx_file_close,</span></span>
- <span data-ttu-id="457c7-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="457c7-2027">fx_file_create,</span></span>
- <span data-ttu-id="457c7-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="457c7-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="457c7-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="457c7-2029">fx_file_delete,</span></span>
- <span data-ttu-id="457c7-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="457c7-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="457c7-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="457c7-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="457c7-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="457c7-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="457c7-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="457c7-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="457c7-2036">fx_file_open,</span></span>
- <span data-ttu-id="457c7-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="457c7-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="457c7-2038">fx_file_rename,</span></span>
- <span data-ttu-id="457c7-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2039">fx_file_seek,</span></span>
- <span data-ttu-id="457c7-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="457c7-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="457c7-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="457c7-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="457c7-2042">fx_file_write,</span></span>
- <span data-ttu-id="457c7-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="457c7-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="457c7-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="457c7-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="457c7-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="457c7-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="457c7-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="457c7-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="457c7-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="457c7-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="457c7-2049">Positioner till en relativ byteförskjutning</span><span class="sxs-lookup"><span data-stu-id="457c7-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2050">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="457c7-2051">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2051">Description</span></span>

<span data-ttu-id="457c7-2052">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna relativa byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="457c7-2053">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-2054">*Om sökåtgärden försöker att söka förbi slutet av filen placeras filens pekare för läsning/skrivning i slutet av filen. Om sökåtgärden försöker placera förbi början av filen placeras däremot filens läs-/skriv pekare till början av filen.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="457c7-2055">Om du vill söka med ett förskjutningsvärde över 4 GB ska programmet använda tjänsten *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="457c7-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2056">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2056">Input Parameters</span></span>

- <span data-ttu-id="457c7-2057">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-2058">**byte_offset:** Önskad relativ byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="457c7-2059">**seek_from:** Riktning och plats för var den relativa söken ska utföras.</span><span class="sxs-lookup"><span data-stu-id="457c7-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="457c7-2060">Giltiga sökalternativ definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="457c7-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="457c7-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="457c7-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="457c7-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="457c7-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="457c7-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="457c7-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="457c7-2065">Om FX_SEEK_BEGIN har angetts utförs sökåtgärden från början av filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="457c7-2066">Om FX_SEEK_END har angetts utförs sökåtgärden bakåt från slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="457c7-2067">Om FX_SEEK_FORWARD har angetts utförs sökåtgärden framåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="457c7-2068">Om FX_SEEK_BACK har angetts utförs sökåtgärden bakåt från den aktuella filpositionen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2069">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2069">Return Values</span></span>

- <span data-ttu-id="457c7-2070">**FX_SUCCESS** (0x00) Lyckad relativ filsökning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="457c7-2071">**FX_NOT_OPEN** (0x07) Den angivna filen är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-2072">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2073">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2074">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2075">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-2076">**FX_PTR_ERROR** (0x18) Ogiltig filpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-2077">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2078">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2078">Allowed From</span></span>

<span data-ttu-id="457c7-2079">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2080">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-2081">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2081">See Also</span></span>

- <span data-ttu-id="457c7-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2082">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2086">fx_file_close</span></span>
- <span data-ttu-id="457c7-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2087">fx_file_create</span></span>
- <span data-ttu-id="457c7-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-2089">fx_file_delete</span></span>
- <span data-ttu-id="457c7-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2096">fx_file_open</span></span>
- <span data-ttu-id="457c7-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2097">fx_file_read</span></span>
- <span data-ttu-id="457c7-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2098">fx_file_rename</span></span>
- <span data-ttu-id="457c7-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2099">fx_file_seek</span></span>
- <span data-ttu-id="457c7-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2100">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2102">fx_file_write</span></span>
- <span data-ttu-id="457c7-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="457c7-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2108">fx_file_rename</span></span>

<span data-ttu-id="457c7-2109">Byter namn på filen</span><span class="sxs-lookup"><span data-stu-id="457c7-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2110">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="457c7-2111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2111">Description</span></span>

<span data-ttu-id="457c7-2112">Den här tjänsten ändrar namnet på filen som anges av *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="457c7-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="457c7-2113">Namnbyte görs också i förhållande till den angivna sökvägen eller standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="457c7-2114">Om en sökväg anges i det nya filnamnet flyttas den omdöpta filen effektivt till den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="457c7-2115">Om ingen sökväg anges placeras den omdöpta filen i den aktuella standardsökvägen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2116">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2116">Input Parameters</span></span>

- <span data-ttu-id="457c7-2117">**media_ptr:** Pekare till ett mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="457c7-2118">**old_file_name:** Pekare till namnet på filen som ska byta namn (katalogsökvägen är valfri).</span><span class="sxs-lookup"><span data-stu-id="457c7-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="457c7-2119">**new_file_name**: Pekare till det nya filnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="457c7-2120">Katalogsökvägen tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="457c7-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2121">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2121">Return Values</span></span>

- <span data-ttu-id="457c7-2122">**FX_SUCCESS** (0x00) Namnbyte av fil.</span><span class="sxs-lookup"><span data-stu-id="457c7-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="457c7-2123">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2124">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="457c7-2125">**FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.</span><span class="sxs-lookup"><span data-stu-id="457c7-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="457c7-2126">**FX_ACCESS_ERROR** (0x06) Angiven fil är redan öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="457c7-2127">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2128">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-2129">**FX_INVALID_NAME** (0x0C) Angivet nytt filnamn är inte ett giltigt filnamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="457c7-2130">**FX_INVALID_PATH** (0x0D) Sökvägen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="457c7-2131">**FX_ALREADY_CREATED** (0x0B) Det nya filnamnet används.</span><span class="sxs-lookup"><span data-stu-id="457c7-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="457c7-2132">**FX_MEDIA_INVALID** (0x02) Media är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="457c7-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="457c7-2133">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2134">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2135">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-2136">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-2137">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="457c7-2138">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-2139">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2140">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2140">Allowed From</span></span>

<span data-ttu-id="457c7-2141">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2142">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-2143">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2143">See Also</span></span>

- <span data-ttu-id="457c7-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2144">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2148">fx_file_close</span></span>
- <span data-ttu-id="457c7-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2149">fx_file_create</span></span>
- <span data-ttu-id="457c7-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-2151">fx_file_delete</span></span>
- <span data-ttu-id="457c7-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2158">fx_file_open</span></span>
- <span data-ttu-id="457c7-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2159">fx_file_read</span></span>
- <span data-ttu-id="457c7-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2161">fx_file_seek</span></span>
- <span data-ttu-id="457c7-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2162">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2164">fx_file_write</span></span>
- <span data-ttu-id="457c7-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="457c7-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2170">fx_file_seek</span></span>

<span data-ttu-id="457c7-2171">Positioner till byte-förskjutning</span><span class="sxs-lookup"><span data-stu-id="457c7-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2172">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="457c7-2173">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2173">Description</span></span>

<span data-ttu-id="457c7-2174">Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna byteförskjutningen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="457c7-2175">Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="457c7-2176">Om du vill söka med ett förskjutningsvärde över 4 GB ska programmet använda tjänsten *fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="457c7-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2177">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2177">Input Parameters</span></span>

- <span data-ttu-id="457c7-2178">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-2179">**byte_offset:** Önskad byteförskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="457c7-2180">Värdet noll placerar läs-/skriv pekaren i början av filen, medan ett värde som är större än filens storlek placerar läs-/skriv pekaren i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2181">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2181">Return Values</span></span>

- <span data-ttu-id="457c7-2182">**FX_SUCCESS** (0x00) Lyckad filsökning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="457c7-2183">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="457c7-2184">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2185">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2186">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2187">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-2188">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-2189">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2190">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2190">Allowed From</span></span>

<span data-ttu-id="457c7-2191">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2192">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-2193">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2193">See Also</span></span>

- <span data-ttu-id="457c7-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2194">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2198">fx_file_close</span></span>
- <span data-ttu-id="457c7-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2199">fx_file_create</span></span>
- <span data-ttu-id="457c7-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-2201">fx_file_delete</span></span>
- <span data-ttu-id="457c7-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2208">fx_file_open</span></span>
- <span data-ttu-id="457c7-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2209">fx_file_read</span></span>
- <span data-ttu-id="457c7-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2210">fx_file_rename</span></span>
- <span data-ttu-id="457c7-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2211">fx_file_seek</span></span>
- <span data-ttu-id="457c7-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2212">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2214">fx_file_write</span></span>
- <span data-ttu-id="457c7-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="457c7-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2220">fx_file_truncate</span></span>

<span data-ttu-id="457c7-2221">Trunkeringsfil</span><span class="sxs-lookup"><span data-stu-id="457c7-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2222">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="457c7-2223">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2223">Description</span></span>

<span data-ttu-id="457c7-2224">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="457c7-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="457c7-2225">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="457c7-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="457c7-2226">Inget av de mediekluster som är associerade med filen släpps.</span><span class="sxs-lookup"><span data-stu-id="457c7-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2227">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="457c7-2228">För att kunna arbeta mer än 4 GB ska programmet använda tjänsten *fx_file_extended_truncate*.</span><span class="sxs-lookup"><span data-stu-id="457c7-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2229">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2229">Input Parameters</span></span>

- <span data-ttu-id="457c7-2230">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-2231">**storlek:** Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="457c7-2231">**size**: New file size.</span></span> <span data-ttu-id="457c7-2232">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="457c7-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2233">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2233">Return Values</span></span>

- <span data-ttu-id="457c7-2234">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="457c7-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="457c7-2235">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="457c7-2236">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-2237">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2238">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-2239">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2240">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2241">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-2242">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="457c7-2243">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-2244">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2245">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2245">Allowed From</span></span>

<span data-ttu-id="457c7-2246">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2247">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-2248">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2248">See Also</span></span>

- <span data-ttu-id="457c7-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2249">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2253">fx_file_close</span></span>
- <span data-ttu-id="457c7-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2254">fx_file_create</span></span>
- <span data-ttu-id="457c7-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-2256">fx_file_delete</span></span>
- <span data-ttu-id="457c7-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2263">fx_file_open</span></span>
- <span data-ttu-id="457c7-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2264">fx_file_read</span></span>
- <span data-ttu-id="457c7-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2266">fx_file_rename</span></span>
- <span data-ttu-id="457c7-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2267">fx_file_seek</span></span>
- <span data-ttu-id="457c7-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2269">fx_file_write</span></span>
- <span data-ttu-id="457c7-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="457c7-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="457c7-2276">Trunkerar fil- och versionskluster</span><span class="sxs-lookup"><span data-stu-id="457c7-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2277">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="457c7-2278">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2278">Description</span></span>

<span data-ttu-id="457c7-2279">Den här tjänsten trunkerar storleken på filen till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="457c7-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="457c7-2280">Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting.</span><span class="sxs-lookup"><span data-stu-id="457c7-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="457c7-2281">Till skillnad ***fx_file_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2282">*Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="457c7-2283">För att kunna arbeta mer än 4 GB ska programmet använda tjänsten *fx_file_extended_truncate_release*.</span><span class="sxs-lookup"><span data-stu-id="457c7-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2284">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2284">Input Parameters</span></span>

- <span data-ttu-id="457c7-2285">**file_ptr:** Pekare till en fil som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="457c7-2286">**storlek:** Ny filstorlek.</span><span class="sxs-lookup"><span data-stu-id="457c7-2286">**size**: New file size.</span></span> <span data-ttu-id="457c7-2287">Byte som har gått förbi den nya filstorleken tas bort.</span><span class="sxs-lookup"><span data-stu-id="457c7-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2288">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2288">Return Values</span></span>

- <span data-ttu-id="457c7-2289">**FX_SUCCESS** (0x00) Lyckad fil trunkering.</span><span class="sxs-lookup"><span data-stu-id="457c7-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="457c7-2290">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-2291">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.</span><span class="sxs-lookup"><span data-stu-id="457c7-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="457c7-2292">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2293">**FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="457c7-2294">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="457c7-2295">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2296">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-2297">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-2298">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="457c7-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="457c7-2299">**FX_PTR_ERROR** (0x18) Ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="457c7-2300">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2301">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2301">Allowed From</span></span>

<span data-ttu-id="457c7-2302">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2303">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="457c7-2304">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2304">See Also</span></span>

- <span data-ttu-id="457c7-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2305">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2309">fx_file_close</span></span>
- <span data-ttu-id="457c7-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2310">fx_file_create</span></span>
- <span data-ttu-id="457c7-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-2312">fx_file_delete</span></span>
- <span data-ttu-id="457c7-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2319">fx_file_open</span></span>
- <span data-ttu-id="457c7-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2320">fx_file_read</span></span>
- <span data-ttu-id="457c7-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2322">fx_file_rename</span></span>
- <span data-ttu-id="457c7-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2323">fx_file_seek</span></span>
- <span data-ttu-id="457c7-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2324">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2325">fx_file_write</span></span>
- <span data-ttu-id="457c7-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="457c7-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2331">fx_file_write</span></span>

<span data-ttu-id="457c7-2332">Skriver byte till fil</span><span class="sxs-lookup"><span data-stu-id="457c7-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="457c7-2334">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2334">Description</span></span>

<span data-ttu-id="457c7-2335">Den här tjänsten skriver byte från den angivna bufferten med början vid filens aktuella position.</span><span class="sxs-lookup"><span data-stu-id="457c7-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="457c7-2336">När skriven är klar justeras filens interna läs pekare så att den pekar på nästa byte i filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2337">*Snabbare prestanda uppnås om källbufferten finns på en lång ordgräns och den begärda storleken är jämnt delbar efter sizeof(\*\*ULONG).*\*\*</span><span class="sxs-lookup"><span data-stu-id="457c7-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2338">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2338">Input Parameters</span></span>

- <span data-ttu-id="457c7-2339">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-2340">**buffer_ptr:** Pekare till källbufferten för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="457c7-2341">**size**: Antal byte som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="457c7-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2342">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2342">Return Values</span></span>

- <span data-ttu-id="457c7-2343">**FX_SUCCESS** (0x00) Lyckad filskrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="457c7-2344">**FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="457c7-2345">**FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="457c7-2346">**FX_NO_MORE_SPACE** (0x0A) Det finns inte mer utrymme tillgängligt på mediet för att utföra den här skriven.</span><span class="sxs-lookup"><span data-stu-id="457c7-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="457c7-2347">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2348">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-2349">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2350">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2351">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="457c7-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="457c7-2352">**FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="457c7-2353">**FX_PTR_ERROR** (0x18) Ogiltig fil eller buffertpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="457c7-2354">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2355">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2355">Allowed From</span></span>

<span data-ttu-id="457c7-2356">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2357">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-2358">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2358">See Also</span></span>

- <span data-ttu-id="457c7-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="457c7-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="457c7-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="457c7-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="457c7-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="457c7-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="457c7-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="457c7-2363">fx_file_close,</span></span>
- <span data-ttu-id="457c7-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="457c7-2364">fx_file_create,</span></span>
- <span data-ttu-id="457c7-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="457c7-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="457c7-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="457c7-2366">fx_file_delete,</span></span>
- <span data-ttu-id="457c7-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="457c7-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="457c7-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="457c7-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="457c7-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="457c7-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="457c7-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="457c7-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="457c7-2373">fx_file_open,</span></span>
- <span data-ttu-id="457c7-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="457c7-2374">fx_file_read,</span></span>
- <span data-ttu-id="457c7-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="457c7-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="457c7-2376">fx_file_rename,</span></span>
- <span data-ttu-id="457c7-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="457c7-2377">fx_file_seek,</span></span>
- <span data-ttu-id="457c7-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="457c7-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="457c7-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="457c7-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="457c7-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="457c7-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="457c7-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="457c7-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="457c7-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="457c7-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="457c7-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="457c7-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="457c7-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="457c7-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="457c7-2386">Anger funktionen för att meddela om filskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2387">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="457c7-2388">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2388">Description</span></span>

<span data-ttu-id="457c7-2389">Den här tjänsten installerar återanropsfunktionen som anropas efter en lyckad filskrivningsåtgärd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2390">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2390">Input Parameters</span></span>

- <span data-ttu-id="457c7-2391">**file_ptr:** Pekare till filkontrollblocket.</span><span class="sxs-lookup"><span data-stu-id="457c7-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="457c7-2392">**file_write_notify:** Återanropsfunktionen för filskrivning som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="457c7-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="457c7-2393">Om du ställer in återanropsfunktionen på NULL inaktiveras återanropsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2394">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2394">Return Values</span></span>

- <span data-ttu-id="457c7-2395">**FX_SUCCESS** (0x00) Återanropsfunktionen har installerats.</span><span class="sxs-lookup"><span data-stu-id="457c7-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="457c7-2396">**FX_PTR_ERROR** (0x18) file_ptr är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="457c7-2397">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2398">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2398">Allowed From</span></span>

<span data-ttu-id="457c7-2399">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2400">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="457c7-2401">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2401">See Also</span></span>

- <span data-ttu-id="457c7-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2402">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2406">fx_file_close</span></span>
- <span data-ttu-id="457c7-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2407">fx_file_create</span></span>
- <span data-ttu-id="457c7-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-2409">fx_file_delete</span></span>
- <span data-ttu-id="457c7-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2416">fx_file_open</span></span>
- <span data-ttu-id="457c7-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2417">fx_file_read</span></span>
- <span data-ttu-id="457c7-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2419">fx_file_rename</span></span>
- <span data-ttu-id="457c7-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-2420">fx_file_seek</span></span>
- <span data-ttu-id="457c7-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-2421">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2423">fx_file_write</span></span>
- <span data-ttu-id="457c7-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="457c7-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2428">fx_media_abort</span></span>

<span data-ttu-id="457c7-2429">Avbryter medieaktiviteter</span><span class="sxs-lookup"><span data-stu-id="457c7-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2430">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-2431">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2431">Description</span></span>

<span data-ttu-id="457c7-2432">Den här tjänsten avbryter alla aktuella aktiviteter som är associerade med mediet, inklusive att stänga alla öppna filer, skicka en begäran om avbrott till den associerade drivrutinen och placera mediet i ett avbrutna tillstånd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="457c7-2433">Den här tjänsten anropas vanligtvis när I/O-fel identifieras.</span><span class="sxs-lookup"><span data-stu-id="457c7-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2434">*Mediet måste öppnas igen för att det ska kunna användas igen när en avbrottsåtgärd har utförts.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2435">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2435">Input Parameters</span></span>

- <span data-ttu-id="457c7-2436">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2437">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2437">Return Values</span></span>

- <span data-ttu-id="457c7-2438">**FX_SUCCESS** (0x00) Lyckad medie abort.</span><span class="sxs-lookup"><span data-stu-id="457c7-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="457c7-2439">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2440">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-2441">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2442">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2442">Allowed From</span></span>

<span data-ttu-id="457c7-2443">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2444">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2445">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2445">See Also</span></span>

- <span data-ttu-id="457c7-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2448">fx_media_check</span></span>
- <span data-ttu-id="457c7-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2449">fx_media_close</span></span>
- <span data-ttu-id="457c7-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2453">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2454">fx_media_format</span></span>
- <span data-ttu-id="457c7-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2455">fx_media_open</span></span>
- <span data-ttu-id="457c7-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2457">fx_media_read</span></span>
- <span data-ttu-id="457c7-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2458">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2461">fx_media_write</span></span>
- <span data-ttu-id="457c7-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="457c7-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="457c7-2464">Ogiltigförklarar logisk sektorcache</span><span class="sxs-lookup"><span data-stu-id="457c7-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2465">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="457c7-2466">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2466">Description</span></span>

<span data-ttu-id="457c7-2467">Den här tjänsten rensar alla felaktiga sektorer i cacheminnet och ogiltigförklarar sedan hela cacheminnet för den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="457c7-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2468">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2468">Input Parameters</span></span>

- <span data-ttu-id="457c7-2469">**media_ptr:** Pekare till mediakontrollblock</span><span class="sxs-lookup"><span data-stu-id="457c7-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2470">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2470">Return Values</span></span>

- <span data-ttu-id="457c7-2471">**FX_SUCCESS** (0x00) Lyckad mediecache ogiltigförklaras.</span><span class="sxs-lookup"><span data-stu-id="457c7-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="457c7-2472">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2473">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2474">**FX_PTR_ERROR** (0x18) Ogiltig media eller scratch-pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="457c7-2475">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2476">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2476">Allowed From</span></span>

<span data-ttu-id="457c7-2477">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2478">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2479">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2479">See Also</span></span>

- <span data-ttu-id="457c7-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2481">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2482">fx_media_check</span></span>
- <span data-ttu-id="457c7-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2483">fx_media_close</span></span>
- <span data-ttu-id="457c7-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2487">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2488">fx_media_format</span></span>
- <span data-ttu-id="457c7-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2489">fx_media_open</span></span>
- <span data-ttu-id="457c7-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2491">fx_media_read</span></span>
- <span data-ttu-id="457c7-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2492">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2495">fx_media_write</span></span>
- <span data-ttu-id="457c7-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="457c7-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2497">fx_media_check</span></span>

<span data-ttu-id="457c7-2498">Söker efter fel i media</span><span class="sxs-lookup"><span data-stu-id="457c7-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2499">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-2500">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2500">Description</span></span>

<span data-ttu-id="457c7-2501">Den här tjänsten söker efter grundläggande strukturella fel i det angivna mediet, inklusive korslänkning mellan filer/kataloger, ogiltiga FAT-kedjor och förlorade kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="457c7-2502">Den här tjänsten ger också möjlighet att korrigera identifierade fel.</span><span class="sxs-lookup"><span data-stu-id="457c7-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="457c7-2503">Tjänsten fx_media_check för att kunna analysera kataloger och filer på mediet på djupet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="457c7-2504">Mer specifikt måste det scratch-minne som tillhandahålls till mediekontrolltjänsten vara tillräckligt stort för att rymma flera katalogposter, en datastruktur för att "stapla" den aktuella katalogpostpositionen innan du går in i underkataloger och slutligen den logiska FAT-bitmappningen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="457c7-2505">Det scratchminnet ska vara minst 512–1 024 byte plus minne för den logiska FAT-bitkartan, vilket kräver lika många bitar som det finns kluster på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="457c7-2506">Till exempel skulle en enhet med 8 000 kluster kräva 1 000 byte för att representera och därmed kräva en total scratch area med en ordning på 2 048 byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2507">*Den här tjänsten bör bara anropas omedelbart efter fx_media_open och utan någon annan filsystemaktivitet.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2508">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2508">Input Parameters</span></span>

- <span data-ttu-id="457c7-2509">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-2510">**scratch_memory_ptr:** Pekaren till början av det scratch-minnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="457c7-2511">**scratch_memory_size:** Storleken på det scratch-minnet i byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="457c7-2512">**error_correction_option:** Bitarna för felkorrigeringsalternativ, när biten har angetts utförs felkorrigering.</span><span class="sxs-lookup"><span data-stu-id="457c7-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="457c7-2513">Bitarna för felkorrigeringsalternativet definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="457c7-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="457c7-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="457c7-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="457c7-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="457c7-2516">FX_LOST_CLUSTER_ERROR (0x04) Helt enkelt ELLER tillsammans de felkorrigeringsalternativ som krävs.</span><span class="sxs-lookup"><span data-stu-id="457c7-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="457c7-2517">Om ingen felkorrigering krävs ska värdet 0 anges.</span><span class="sxs-lookup"><span data-stu-id="457c7-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="457c7-2518">**errors_detected_ptr:** Mål för felidentifierings bitar enligt definitionen nedan:</span><span class="sxs-lookup"><span data-stu-id="457c7-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="457c7-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="457c7-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="457c7-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="457c7-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="457c7-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="457c7-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2522">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2522">Return Values</span></span>

- <span data-ttu-id="457c7-2523">**FX_SUCCESS** (0x00) Lyckad mediekontroll visar du de fel som identifierats för mer information.</span><span class="sxs-lookup"><span data-stu-id="457c7-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="457c7-2524">**FX_ACCESS_ERROR** (0x06) Det går inte att kontrollera med öppna filer.</span><span class="sxs-lookup"><span data-stu-id="457c7-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="457c7-2525">**FX_FILE_CORRUPT** (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2526">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2527">**FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="457c7-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Det tillhandahållna minnet är inte tillräckligt stort.</span><span class="sxs-lookup"><span data-stu-id="457c7-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="457c7-2529">**FX_ERROR_NOT_FIXED** (0x93) Fel i FAT32-rotkatalogen som inte kunde åtgärdas.</span><span class="sxs-lookup"><span data-stu-id="457c7-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="457c7-2530">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2531">**FX_SECTOR_INVALID** (0x89) Sektor är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="457c7-2532">**FX_PTR_ERROR** (0x18) Ogiltig media eller scratch-pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="457c7-2533">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="457c7-2534">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2534">Allowed From</span></span>

<span data-ttu-id="457c7-2535">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2536">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2536">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-2537">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2537">See Also</span></span>

- <span data-ttu-id="457c7-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2539">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2541">fx_media_close</span></span>
- <span data-ttu-id="457c7-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2545">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2546">fx_media_format</span></span>
- <span data-ttu-id="457c7-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2547">fx_media_open</span></span>
- <span data-ttu-id="457c7-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2549">fx_media_read</span></span>
- <span data-ttu-id="457c7-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2550">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2553">fx_media_write</span></span>
- <span data-ttu-id="457c7-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="457c7-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2555">fx_media_close</span></span>

<span data-ttu-id="457c7-2556">Stänger media</span><span class="sxs-lookup"><span data-stu-id="457c7-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2557">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-2558">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2558">Description</span></span>

<span data-ttu-id="457c7-2559">Den här tjänsten stänger det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2559">This service closes the specified media.</span></span> <span data-ttu-id="457c7-2560">När mediet stängs stängs alla öppna filer och eventuella återstående buffertar rensas till det fysiska mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2561">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2561">Input Parameters</span></span>

- <span data-ttu-id="457c7-2562">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2563">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2563">Return Values</span></span>

- <span data-ttu-id="457c7-2564">**FX_SUCCESS** (0x00) Lyckad media stäng.</span><span class="sxs-lookup"><span data-stu-id="457c7-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="457c7-2565">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2566">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2567">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-2568">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2569">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2569">Allowed From</span></span>

<span data-ttu-id="457c7-2570">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2571">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2572">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2572">See Also</span></span>

- <span data-ttu-id="457c7-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2574">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2576">fx_media_check</span></span>
- <span data-ttu-id="457c7-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2580">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2581">fx_media_format</span></span>
- <span data-ttu-id="457c7-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2582">fx_media_open</span></span>
- <span data-ttu-id="457c7-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2584">fx_media_read</span></span>
- <span data-ttu-id="457c7-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2585">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2588">fx_media_write</span></span>
- <span data-ttu-id="457c7-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="457c7-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="457c7-2591">Ställer in funktionen media close notify</span><span class="sxs-lookup"><span data-stu-id="457c7-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2592">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="457c7-2593">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2593">Description</span></span>

<span data-ttu-id="457c7-2594">Den här tjänsten anger en återanropsfunktion för att meddela som anropas när ett medium har stängts.</span><span class="sxs-lookup"><span data-stu-id="457c7-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2595">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2595">Input Parameters</span></span>

- <span data-ttu-id="457c7-2596">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-2597">**media_close_notify: Media** Close meddelar återanropsfunktionen att installeras.</span><span class="sxs-lookup"><span data-stu-id="457c7-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="457c7-2598">Om null-värdet passerar som återanropsfunktionen inaktiveras återanropet av media.</span><span class="sxs-lookup"><span data-stu-id="457c7-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2599">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2599">Return Values</span></span>

- <span data-ttu-id="457c7-2600">**FX_SUCCESS** (0x00) Återanropsfunktionen har installerats.</span><span class="sxs-lookup"><span data-stu-id="457c7-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="457c7-2601">**FX_PTR_ERROR** (0x18) media_ptr är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="457c7-2602">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2603">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2603">Allowed From</span></span>

<span data-ttu-id="457c7-2604">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2605">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="457c7-2606">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2606">See Also</span></span>

- <span data-ttu-id="457c7-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2608">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2610">fx_media_check</span></span>
- <span data-ttu-id="457c7-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2611">fx_media_close</span></span>
- <span data-ttu-id="457c7-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2614">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2615">fx_media_format</span></span>
- <span data-ttu-id="457c7-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2616">fx_media_open</span></span>
- <span data-ttu-id="457c7-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2618">fx_media_read</span></span>
- <span data-ttu-id="457c7-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2619">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2622">fx_media_write</span></span>
- <span data-ttu-id="457c7-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="457c7-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="457c7-2625">Formatera media</span><span class="sxs-lookup"><span data-stu-id="457c7-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2626">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2626">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="457c7-2627">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2627">Description</span></span>

<span data-ttu-id="457c7-2628">Den här tjänsten formaterar det angivna mediet på ett exFAT-kompatibelt sätt baserat på de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="457c7-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="457c7-2629">Den här tjänsten måste anropas innan mediet öppnas.</span><span class="sxs-lookup"><span data-stu-id="457c7-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2630">*Om du formaterar ett redan formaterat medium raderas effektivt alla filer och kataloger på mediet.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-2631">*ExFAT-volymstorleken ska matcha storleken på partitionen (om det finns en MBR- eller GPT-layout) eller storleken på hela enheten om det inte finns någon partitionslayout (ingen MBR eller GPT). Det finns en begränsning Windows att exFAT Disk inte kommer att formateras om med vissa värden för totala sektorer som är mindre än tillgängliga sektorer*</span><span class="sxs-lookup"><span data-stu-id="457c7-2631">*The exFAT volume size should match the size of the partition (if there is an MBR or GPT layout), or the size of the whole device if there is no partition layout (no MBR or GPT). There is a limitation on Windows that exFAT Disk will not be recoginzed if formatted with some values of total sectors that are less than available sectors*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2632">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2632">Input Parameters</span></span>

- <span data-ttu-id="457c7-2633">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2633">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="457c7-2634">Detta används endast för att tillhandahålla viss grundläggande information som krävs för att drivrutinen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="457c7-2634">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="457c7-2635">**driver**: Pekare till I/O-drivrutinen för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2635">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="457c7-2636">Detta är vanligtvis samma drivrutin som angavs för efterföljande fx_media_open anropet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2636">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="457c7-2637">**driver_info_ptr:** Pekare till valfri information som I/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="457c7-2637">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="457c7-2638">**memory_ptr:** Pekare till arbetsminnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2638">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="457c7-2639">memory_size Anger storleken på arbetsmediaminnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2639">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="457c7-2640">Storleken måste vara minst lika stor som mediets sektorstorlek.</span><span class="sxs-lookup"><span data-stu-id="457c7-2640">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="457c7-2641">**volume_name:** Pekare till volymnamnssträngen, som är högst 11 tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-2641">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="457c7-2642">**number_of_fats:** Antal vanliga frågor och svar på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2642">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="457c7-2643">Den aktuella implementeringen stöder en FAT på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2643">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="457c7-2644">**hidden_sectors:** Antalet sektorer som är dolda före det här mediets startsektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2644">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="457c7-2645">Detta är vanligt när det finns flera partitioner.</span><span class="sxs-lookup"><span data-stu-id="457c7-2645">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="457c7-2646">**total_sectors:** Totalt antal sektorer i mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2646">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="457c7-2647">**bytes_per_sector:** Antal byte per sektor, vilket vanligtvis är 512.</span><span class="sxs-lookup"><span data-stu-id="457c7-2647">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="457c7-2648">FileX kräver att detta är en multipel av 32.</span><span class="sxs-lookup"><span data-stu-id="457c7-2648">FileX requires this to be a multiple of 32.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="457c7-2649">*Med referens till specifikationen kan byte per sektor endast ha följande värden: 512, 1024, 2048 eller 4096.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2649">*With reference to the specification the bytes per sector may take on only the following values: 512, 1024, 2048 or 4096.*</span></span>

- <span data-ttu-id="457c7-2650">**sectors_per_cluster:** Antalet sektorer i varje kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2650">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="457c7-2651">Klustret är den minsta allokeringsenheten i ett FAT-filsystem.</span><span class="sxs-lookup"><span data-stu-id="457c7-2651">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="457c7-2652">**volumne_serial_number:** Serienummer som ska användas för den här volymen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2652">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="457c7-2653">**boundary_unit:** Storlek på fysisk dataområdesjustering i antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="457c7-2653">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2654">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2654">Return Values</span></span>

- <span data-ttu-id="457c7-2655">**FX_SUCCESS** (0x00) Medieformatet lyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-2655">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="457c7-2656">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2656">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2657">**FX_PTR_ERROR** (0x18) Ogiltig media-, drivrutins- eller minnespekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2657">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="457c7-2658">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2658">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2659">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2659">Allowed From</span></span>

<span data-ttu-id="457c7-2660">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2660">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2661">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2661">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-2662">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2662">See Also</span></span>

- <span data-ttu-id="457c7-2663">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2663">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2664">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2664">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2665">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2665">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2666">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2666">fx_media_check</span></span>
- <span data-ttu-id="457c7-2667">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2667">fx_media_close</span></span>
- <span data-ttu-id="457c7-2668">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2668">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2669">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2669">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2670">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2670">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2671">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2671">fx_media_format</span></span>
- <span data-ttu-id="457c7-2672">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2672">fx_media_open</span></span>
- <span data-ttu-id="457c7-2673">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2673">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2674">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2674">fx_media_read</span></span>
- <span data-ttu-id="457c7-2675">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2675">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2676">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2676">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2677">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2677">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2678">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2678">fx_media_write</span></span>
- <span data-ttu-id="457c7-2679">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2679">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="457c7-2680">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2680">fx_media_extended_space_available</span></span>

<span data-ttu-id="457c7-2681">Returnerar tillgängligt medieutrymme</span><span class="sxs-lookup"><span data-stu-id="457c7-2681">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2682">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2682">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-2683">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2683">Description</span></span>

<span data-ttu-id="457c7-2684">Den här tjänsten returnerar antalet tillgängliga byte på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2684">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="457c7-2685">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-2685">This service is designed for exFAT.</span></span> <span data-ttu-id="457c7-2686">Pekaren till *available_bytes* parametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta med medier utanför 4 GB intervall.</span><span class="sxs-lookup"><span data-stu-id="457c7-2686">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2687">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2687">Input Parameters</span></span>

- <span data-ttu-id="457c7-2688">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2688">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="457c7-2689">**available_bytes_ptr:** Tillgängliga byte kvar på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2689">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2690">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2690">Return Values</span></span>

- <span data-ttu-id="457c7-2691">**FX_SUCCESS** (0x00) Tillgängligt utrymme på mediet har hämtats.</span><span class="sxs-lookup"><span data-stu-id="457c7-2691">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="457c7-2692">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2693">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare eller tillgänglig byte-pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-2693">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="457c7-2694">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2694">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2695">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2695">Allowed From</span></span>

<span data-ttu-id="457c7-2696">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2696">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2697">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2697">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2698">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2698">See Also</span></span>

- <span data-ttu-id="457c7-2699">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2699">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2700">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2700">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2701">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2701">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2702">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2702">fx_media_check</span></span>
- <span data-ttu-id="457c7-2703">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2703">fx_media_close</span></span>
- <span data-ttu-id="457c7-2704">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2704">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2705">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2705">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2706">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2706">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2707">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2707">fx_media_format</span></span>
- <span data-ttu-id="457c7-2708">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2708">fx_media_open</span></span>
- <span data-ttu-id="457c7-2709">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2709">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2710">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2710">fx_media_read</span></span>
- <span data-ttu-id="457c7-2711">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2711">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2712">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2712">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2713">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2713">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2714">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2714">fx_media_write</span></span>
- <span data-ttu-id="457c7-2715">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2715">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="457c7-2716">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2716">fx_media_flush</span></span>

<span data-ttu-id="457c7-2717">Rensar data till fysiska media</span><span class="sxs-lookup"><span data-stu-id="457c7-2717">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2718">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2718">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-2719">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2719">Description</span></span>

<span data-ttu-id="457c7-2720">Den här tjänsten rensar alla cachelagrade sektorer och katalogposter för ändrade filer till det fysiska mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2720">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2721">*Den här rutinen kan anropas regelbundet av programmet för att minska risken för skadade filer och/eller dataförlust i händelse av plötslig strömförlust på målet.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2721">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2722">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2722">Input Parameters</span></span>

- <span data-ttu-id="457c7-2723">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2723">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2724">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2724">Return Values</span></span>

- <span data-ttu-id="457c7-2725">**FX_SUCCESS** (0x00) Lyckad medieström.</span><span class="sxs-lookup"><span data-stu-id="457c7-2725">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="457c7-2726">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2726">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2727">**FX_FILE_CORRUPT**    (0x08) Filen är skadad.</span><span class="sxs-lookup"><span data-stu-id="457c7-2727">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="457c7-2728">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2728">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2729">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2729">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2730">**FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="457c7-2730">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-2731">**FX_PTR_ERROR** (0x18) Ogiltig mediepekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2731">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-2732">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2732">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2733">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2733">Allowed From</span></span>

<span data-ttu-id="457c7-2734">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2734">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2735">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2735">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2736">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2736">See Also</span></span>

- <span data-ttu-id="457c7-2737">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2737">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2738">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2738">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2739">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2739">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2740">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2740">fx_media_check</span></span>
- <span data-ttu-id="457c7-2741">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2741">fx_media_close</span></span>
- <span data-ttu-id="457c7-2742">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2742">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2743">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2743">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2744">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2744">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2745">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2745">fx_media_format</span></span>
- <span data-ttu-id="457c7-2746">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2746">fx_media_open</span></span>
- <span data-ttu-id="457c7-2747">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2747">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2748">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2748">fx_media_read</span></span>
- <span data-ttu-id="457c7-2749">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2749">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2750">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2750">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2751">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2751">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2752">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2752">fx_media_write</span></span>
- <span data-ttu-id="457c7-2753">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2753">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="457c7-2754">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2754">fx_media_format</span></span>

<span data-ttu-id="457c7-2755">Formaterar media</span><span class="sxs-lookup"><span data-stu-id="457c7-2755">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2756">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2756">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="457c7-2757">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2757">Description</span></span>

<span data-ttu-id="457c7-2758">Den här tjänsten formaterar det angivna mediet på ett FAT 12/16/32-kompatibelt sätt baserat på de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="457c7-2758">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="457c7-2759">Den här tjänsten måste anropas innan mediet öppnas.</span><span class="sxs-lookup"><span data-stu-id="457c7-2759">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2760">*Om du formaterar ett redan formaterat medium raderas effektivt alla filer och kataloger på mediet.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2760">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2761">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2761">Input Parameters</span></span>

- <span data-ttu-id="457c7-2762">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2762">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="457c7-2763">Detta används endast för att tillhandahålla viss grundläggande information som krävs för att drivrutinen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="457c7-2763">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="457c7-2764">**driver**: Pekare till I/O-drivrutinen för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2764">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="457c7-2765">Detta är vanligtvis samma drivrutin som tillhandahålls till efterföljande fx_media_open anrop.</span><span class="sxs-lookup"><span data-stu-id="457c7-2765">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="457c7-2766">**driver_info_ptr:** Pekare till valfri information som I/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="457c7-2766">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="457c7-2767">**memory_ptr:** Pekare till arbetsminnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2767">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="457c7-2768">**memory_size:** Anger storleken på arbetsmediaminnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2768">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="457c7-2769">Storleken måste vara minst lika stor som mediets sektorstorlek.</span><span class="sxs-lookup"><span data-stu-id="457c7-2769">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="457c7-2770">**volume_name:** Pekare till volymnamnssträngen, som är högst 11 tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-2770">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="457c7-2771">**number_of_fats:** Antal vanliga frågor och svar på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2771">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="457c7-2772">Det minimala värdet är 1 för primärt FAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-2772">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="457c7-2773">Värden större än 1 resulterar i att ytterligare FAT-kopior underhålls vid körning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2773">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="457c7-2774">**directory_entries:** Antal katalogposter i rotkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2774">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="457c7-2775">**hidden_sectors:** Antalet sektorer som är dolda före det här mediets startsektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2775">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="457c7-2776">Detta är vanligt när det finns flera partitioner.</span><span class="sxs-lookup"><span data-stu-id="457c7-2776">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="457c7-2777">**total_sectors:** Totalt antal sektorer i mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2777">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="457c7-2778">**bytes_per_sector:** Antal byte per sektor, vilket vanligtvis är 512.</span><span class="sxs-lookup"><span data-stu-id="457c7-2778">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="457c7-2779">FileX kräver att detta är en multipel av 32.</span><span class="sxs-lookup"><span data-stu-id="457c7-2779">FileX requires this to be a multiple of 32.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="457c7-2780">*Med referens till specifikationen kan byte per sektor endast ha följande värden: 512, 1024, 2048 eller 4096.*</span><span class="sxs-lookup"><span data-stu-id="457c7-2780">*With reference to the specification the bytes per sector may take on only the following values: 512, 1024, 2048 or 4096.*</span></span>

- <span data-ttu-id="457c7-2781">**sectors_per_cluster:** Antal sektorer i varje kluster.</span><span class="sxs-lookup"><span data-stu-id="457c7-2781">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="457c7-2782">Klustret är den minsta allokeringsenheten i ett FAT-filsystem.</span><span class="sxs-lookup"><span data-stu-id="457c7-2782">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="457c7-2783">**heads**: Antal fysiska krona.</span><span class="sxs-lookup"><span data-stu-id="457c7-2783">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="457c7-2784">**sectors_per_track:** Antal sektorer per spår.</span><span class="sxs-lookup"><span data-stu-id="457c7-2784">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2785">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2785">Return Values</span></span>

- <span data-ttu-id="457c7-2786">**FX_SUCCESS** (0x00) Medieformatet lyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-2786">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="457c7-2787">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-2787">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2788">**FX_PTR_ERROR** (0x18) Ogiltig media, drivrutin eller minnespekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2788">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="457c7-2789">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2789">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2790">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2790">Allowed From</span></span>

<span data-ttu-id="457c7-2791">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2791">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2792">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2792">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-2793">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2793">See Also</span></span>

- <span data-ttu-id="457c7-2794">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2794">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2795">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2795">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2796">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2796">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2797">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2797">fx_media_check</span></span>
- <span data-ttu-id="457c7-2798">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2798">fx_media_close</span></span>
- <span data-ttu-id="457c7-2799">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2799">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2800">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2800">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2801">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2801">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2802">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2802">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2803">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2803">fx_media_open</span></span>
- <span data-ttu-id="457c7-2804">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2804">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2805">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2805">fx_media_read</span></span>
- <span data-ttu-id="457c7-2806">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2806">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2807">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2807">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2808">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2808">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2809">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2809">fx_media_write</span></span>
- <span data-ttu-id="457c7-2810">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2810">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="457c7-2811">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2811">fx_media_open</span></span>

<span data-ttu-id="457c7-2812">Öppnar media för filåtkomst</span><span class="sxs-lookup"><span data-stu-id="457c7-2812">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2813">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2813">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="457c7-2814">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2814">Description</span></span>

<span data-ttu-id="457c7-2815">Den här tjänsten öppnar ett medium för filåtkomst med hjälp av den angivna I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2815">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-2816">*Det minne som tillhandahålls till den här tjänsten används för att implementera en intern logisk sektorcache, och ju mer minne som tillhandahålls desto mer fysisk I/O minskas. FileX kräver en cache med minst en logisk sektor (byte per sektor av mediet).*</span><span class="sxs-lookup"><span data-stu-id="457c7-2816">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2817">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2817">Input Parameters</span></span>

- <span data-ttu-id="457c7-2818">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2818">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-2819">**media_name:** Pekare till mediets namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-2819">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="457c7-2820">**media_driver:** Pekare till I/O-drivrutin för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2820">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="457c7-2821">I/O-drivrutinen måste uppfylla kraven för FileX-drivrutinen som definieras i kapitel 5.</span><span class="sxs-lookup"><span data-stu-id="457c7-2821">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="457c7-2822">**driver_info_ptr:** Pekare till valfri information som den angivna I/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="457c7-2822">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="457c7-2823">**memory_ptr:** Pekare till arbetsminnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2823">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="457c7-2824">**memory_size:** Anger storleken på arbetsmediaminnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2824">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="457c7-2825">Storleken måste vara lika stor som mediets sektorstorlek (vanligtvis 512 byte).</span><span class="sxs-lookup"><span data-stu-id="457c7-2825">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2826">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2826">Return Values</span></span>

- <span data-ttu-id="457c7-2827">**FX_SUCCESS** (0x00) Lyckad media är öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2827">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="457c7-2828">**FX_BOOT_ERROR** (0x01) Fel vid läsning av mediets startsektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2828">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="457c7-2829">**FX_MEDIA_INVALID** (0x02) Det angivna mediets startsektor är skadad eller ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-2829">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="457c7-2830">Dessutom används den här returkoden för att ange att antingen cachestorleken för den logiska sektorn eller FAT-poststorleken inte är en strömförsörjning på 2.</span><span class="sxs-lookup"><span data-stu-id="457c7-2830">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="457c7-2831">**FX_FAT_READ_ERROR** (0x03) Fel vid läsning av mediet FAT.</span><span class="sxs-lookup"><span data-stu-id="457c7-2831">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="457c7-2832">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2832">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2833">**FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-2833">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="457c7-2834">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2834">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2835">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2835">Allowed From</span></span>

<span data-ttu-id="457c7-2836">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2836">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2837">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2837">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2838">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2838">See Also</span></span>

- <span data-ttu-id="457c7-2839">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2839">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2840">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2840">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2841">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2841">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2842">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2842">fx_media_check</span></span>
- <span data-ttu-id="457c7-2843">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2843">fx_media_close</span></span>
- <span data-ttu-id="457c7-2844">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2844">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2845">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2845">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2846">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2846">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2847">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2847">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2848">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2848">fx_media_format</span></span>
- <span data-ttu-id="457c7-2849">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2849">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2850">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2850">fx_media_read</span></span>
- <span data-ttu-id="457c7-2851">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2851">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2852">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2852">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2853">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2853">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2854">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2854">fx_media_write</span></span>
- <span data-ttu-id="457c7-2855">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2855">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="457c7-2856">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2856">fx_media_open_notify_set</span></span>

<span data-ttu-id="457c7-2857">Anger media open notify-funktionen</span><span class="sxs-lookup"><span data-stu-id="457c7-2857">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2858">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2858">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="457c7-2859">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2859">Description</span></span>

<span data-ttu-id="457c7-2860">Den här tjänsten anger en avanropsfunktion som anropas när ett medium har öppnats.</span><span class="sxs-lookup"><span data-stu-id="457c7-2860">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2861">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2861">Input Parameters</span></span>

- <span data-ttu-id="457c7-2862">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2862">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-2863">**media_open_notify: Media** open notify callback function to be installed.</span><span class="sxs-lookup"><span data-stu-id="457c7-2863">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="457c7-2864">Om null-värdet används som återanropsfunktion inaktiveras återanropet från mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2864">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2865">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2865">Return Values</span></span>


- <span data-ttu-id="457c7-2866">**FX_SUCCESS** (0x00) Successfuly installerade återanropsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2866">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="457c7-2867">**FX_PTR_ERROR** (0x18) media_ptr är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-2867">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="457c7-2868">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2868">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2869">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2869">Allowed From</span></span>

<span data-ttu-id="457c7-2870">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2871">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2871">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="457c7-2872">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2872">See Also</span></span>

- <span data-ttu-id="457c7-2873">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2873">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2874">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2874">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2875">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2875">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2876">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2876">fx_media_check</span></span>
- <span data-ttu-id="457c7-2877">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2877">fx_media_close</span></span>
- <span data-ttu-id="457c7-2878">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2878">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2879">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2879">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2880">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2880">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2881">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2881">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2882">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2882">fx_media_format</span></span>
- <span data-ttu-id="457c7-2883">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2883">fx_media_open</span></span>
- <span data-ttu-id="457c7-2884">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2884">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2885">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2885">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2886">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2886">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2887">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2887">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2888">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2888">fx_media_write</span></span>
- <span data-ttu-id="457c7-2889">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2889">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="457c7-2890">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2890">fx_media_read</span></span>

<span data-ttu-id="457c7-2891">Läser logisk sektor från media</span><span class="sxs-lookup"><span data-stu-id="457c7-2891">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2892">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2892">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-2893">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2893">Description</span></span>

<span data-ttu-id="457c7-2894">Den här tjänsten läser en logisk sektor från mediet och placerar den i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-2894">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2895">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2895">Input Parameters</span></span>

- <span data-ttu-id="457c7-2896">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2896">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="457c7-2897">**logical_sector:** Logisk sektor att läsa.</span><span class="sxs-lookup"><span data-stu-id="457c7-2897">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="457c7-2898">**buffer_ptr:** Pekare till målet för den logiska sektorn läsa.</span><span class="sxs-lookup"><span data-stu-id="457c7-2898">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2899">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2899">Return Values</span></span>

- <span data-ttu-id="457c7-2900">**FX_SUCCESS** (0x00) Lyckad medieläsning.</span><span class="sxs-lookup"><span data-stu-id="457c7-2900">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="457c7-2901">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2901">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2902">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2902">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2903">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-2903">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-2904">**FX_PTR_ERROR** (0x18) Ogiltig media eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2904">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="457c7-2905">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2905">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2906">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2906">Allowed From</span></span>

<span data-ttu-id="457c7-2907">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2907">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2908">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2908">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="457c7-2909">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2909">See Also</span></span>

- <span data-ttu-id="457c7-2910">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2910">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2911">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2911">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2912">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2912">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2913">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2913">fx_media_check</span></span>
- <span data-ttu-id="457c7-2914">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2914">fx_media_close</span></span>
- <span data-ttu-id="457c7-2915">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2915">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2916">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2916">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2917">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2917">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2918">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2918">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2919">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2919">fx_media_format</span></span>
- <span data-ttu-id="457c7-2920">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2920">fx_media_open</span></span>
- <span data-ttu-id="457c7-2921">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2921">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2922">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2922">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-2923">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2923">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2924">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2924">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2925">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2925">fx_media_write</span></span>
- <span data-ttu-id="457c7-2926">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2926">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="457c7-2927">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2927">fx_media_space_available</span></span>

<span data-ttu-id="457c7-2928">Returnerar tillgängligt medieutrymme</span><span class="sxs-lookup"><span data-stu-id="457c7-2928">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2929">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2929">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="457c7-2930">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2930">Description</span></span>

<span data-ttu-id="457c7-2931">Den här tjänsten returnerar antalet tillgängliga byte på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2931">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="457c7-2932">Om du vill arbeta med media som är större än 4 GB ska programmet använda tjänsten *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="457c7-2932">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2933">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2933">Input Parameters</span></span>

- <span data-ttu-id="457c7-2934">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2934">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="457c7-2935">**available_bytes_ptr:** Tillgängliga byte kvar på mediet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2935">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2936">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2936">Return Values</span></span>

- <span data-ttu-id="457c7-2937">**FX_SUCCESS** (0x00) Tillgängligt utrymme på mediet har returnerats.</span><span class="sxs-lookup"><span data-stu-id="457c7-2937">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="457c7-2938">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2938">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2939">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare eller tillgänglig byte-pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-2939">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="457c7-2940">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2940">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2941">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2941">Allowed From</span></span>

<span data-ttu-id="457c7-2942">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2942">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2943">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2943">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2944">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2944">See Also</span></span>

- <span data-ttu-id="457c7-2945">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2945">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2946">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2946">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2947">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2947">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2948">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2948">fx_media_check</span></span>
- <span data-ttu-id="457c7-2949">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2949">fx_media_close</span></span>
- <span data-ttu-id="457c7-2950">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2950">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2951">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2951">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2952">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2952">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2953">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2953">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2954">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2954">fx_media_format</span></span>
- <span data-ttu-id="457c7-2955">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2955">fx_media_open</span></span>
- <span data-ttu-id="457c7-2956">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2956">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2957">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2957">fx_media_read</span></span>
- <span data-ttu-id="457c7-2958">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2958">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-2959">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2959">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-2960">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-2960">fx_media_write</span></span>
- <span data-ttu-id="457c7-2961">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-2961">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="457c7-2962">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-2962">fx_media_volume_get</span></span>

<span data-ttu-id="457c7-2963">Hämtar medievolymens namn</span><span class="sxs-lookup"><span data-stu-id="457c7-2963">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-2964">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-2964">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="457c7-2965">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-2965">Description</span></span>

<span data-ttu-id="457c7-2966">Den här tjänsten hämtar volymnamnet för det media som öppnades tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2966">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-2967">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-2967">Input Parameters</span></span>

- <span data-ttu-id="457c7-2968">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-2968">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-2969">**volume_name:** Pekare till mål för volymnamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-2969">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="457c7-2970">Observera att målet måste vara minst tillräckligt stort för att innehålla 12 tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-2970">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="457c7-2971">**volume_source:** Anger var namnet ska hämtas, antingen från startsektorn eller rotkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2971">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="457c7-2972">Giltiga värden för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="457c7-2972">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="457c7-2973">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="457c7-2973">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="457c7-2974">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="457c7-2974">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-2975">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-2975">Return Values</span></span>

- <span data-ttu-id="457c7-2976">**FX_SUCCESS** (0x00) Lyckad medievolym get.</span><span class="sxs-lookup"><span data-stu-id="457c7-2976">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="457c7-2977">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-2977">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-2978">**FX_NOT_FOUND** (0x04) Det går inte att hitta volymen.</span><span class="sxs-lookup"><span data-stu-id="457c7-2978">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="457c7-2979">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-2979">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-2980">**FX_PTR_ERROR** (0x18) Ogiltig media- eller volymmål pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-2980">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="457c7-2981">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-2981">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-2982">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-2982">Allowed From</span></span>

<span data-ttu-id="457c7-2983">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-2983">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-2984">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-2984">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="457c7-2985">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-2985">See Also</span></span>

- <span data-ttu-id="457c7-2986">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-2986">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-2987">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-2987">fx_media_abort</span></span>
- <span data-ttu-id="457c7-2988">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-2988">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-2989">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-2989">fx_media_check</span></span>
- <span data-ttu-id="457c7-2990">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-2990">fx_media_close</span></span>
- <span data-ttu-id="457c7-2991">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2991">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-2992">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2992">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-2993">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2993">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-2994">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-2994">fx_media_flush</span></span>
- <span data-ttu-id="457c7-2995">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-2995">fx_media_format</span></span>
- <span data-ttu-id="457c7-2996">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-2996">fx_media_open</span></span>
- <span data-ttu-id="457c7-2997">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-2997">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-2998">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-2998">fx_media_read</span></span>
- <span data-ttu-id="457c7-2999">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-2999">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-3000">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3000">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-3001">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3001">fx_media_write</span></span>
- <span data-ttu-id="457c7-3002">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3002">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="457c7-3003">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="457c7-3003">fx_media_volume_get_extended</span></span>

<span data-ttu-id="457c7-3004">Hämtar medievolymnamnet för media som öppnats tidigare</span><span class="sxs-lookup"><span data-stu-id="457c7-3004">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3005">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3005">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="457c7-3006">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3006">Description</span></span>

<span data-ttu-id="457c7-3007">Den här tjänsten hämtar volymnamnet för det media som öppnades tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3007">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3008">Den här tjänsten är identisk med \***fx_media_volume_get()** _ förutom att anroparen skickar storleken på *bufferten* _ volume_name \* .</span><span class="sxs-lookup"><span data-stu-id="457c7-3008">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3009">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3009">Input Parameters</span></span>


- <span data-ttu-id="457c7-3010">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3010">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3011">**volume_name:** Pekare till mål för volymnamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3011">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="457c7-3012">Observera att målet måste vara minst tillräckligt stort för att innehålla 12 tecken.</span><span class="sxs-lookup"><span data-stu-id="457c7-3012">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="457c7-3013">**volume_name_buffer_length:** Storleken på volume_name buffert.</span><span class="sxs-lookup"><span data-stu-id="457c7-3013">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="457c7-3014">**volume_source:** Anger var namnet ska hämtas, antingen från startsektorn eller rotkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3014">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="457c7-3015">Giltiga värden för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="457c7-3015">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="457c7-3016">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="457c7-3016">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="457c7-3017">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="457c7-3017">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3018">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3018">Return Values</span></span>

- <span data-ttu-id="457c7-3019">**FX_SUCCESS** (0x00) Lyckad medievolym get.</span><span class="sxs-lookup"><span data-stu-id="457c7-3019">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="457c7-3020">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3020">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3021">**FX_NOT_FOUND** (0x04) Det går inte att hitta volymen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3021">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="457c7-3022">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-3022">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3023">**FX_PTR_ERROR** (0x18) Ogiltig media- eller volymmål pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3023">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="457c7-3024">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3024">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3025">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3025">Allowed From</span></span>

<span data-ttu-id="457c7-3026">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3026">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3027">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3027">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-3028">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3028">See Also</span></span>

- <span data-ttu-id="457c7-3029">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-3029">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-3030">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-3030">fx_media_abort</span></span>
- <span data-ttu-id="457c7-3031">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-3031">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-3032">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-3032">fx_media_check</span></span>
- <span data-ttu-id="457c7-3033">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3033">fx_media_close</span></span>
- <span data-ttu-id="457c7-3034">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3034">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-3035">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-3035">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-3036">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-3036">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-3037">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-3037">fx_media_flush</span></span>
- <span data-ttu-id="457c7-3038">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-3038">fx_media_format</span></span>
- <span data-ttu-id="457c7-3039">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3039">fx_media_open</span></span>
- <span data-ttu-id="457c7-3040">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3040">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-3041">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3041">fx_media_read</span></span>
- <span data-ttu-id="457c7-3042">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-3042">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3043">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-3044">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3044">fx_media_write</span></span>
- <span data-ttu-id="457c7-3045">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3045">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="457c7-3046">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3046">fx_media_volume_set</span></span>

<span data-ttu-id="457c7-3047">Anger medievolymnamn</span><span class="sxs-lookup"><span data-stu-id="457c7-3047">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3048">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3048">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="457c7-3049">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3049">Description</span></span>

<span data-ttu-id="457c7-3050">Den här tjänsten anger volymnamnet för det media som öppnades tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3050">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3051">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3051">Input Parameters</span></span>

- <span data-ttu-id="457c7-3052">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3052">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3053">**volume_name:** Pekare till volymnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3053">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3054">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3054">Return Values</span></span>

- <span data-ttu-id="457c7-3055">**FX_SUCCESS** (0x00) Lyckad medievolymuppsättning.</span><span class="sxs-lookup"><span data-stu-id="457c7-3055">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="457c7-3056">**FX_INVALID_NAME** (0x0C) Volume_name är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-3056">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="457c7-3057">**FX_MEDIA_INVALID** (0x02) Det går inte att ange volymnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3057">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="457c7-3058">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3058">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3059">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-3059">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3060">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-3060">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-3061">**FX_PTR_ERROR** (0x18) Ogiltig media- eller volymnamnspekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3061">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="457c7-3062">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3062">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3063">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3063">Allowed From</span></span>

<span data-ttu-id="457c7-3064">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3064">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3065">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3065">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-3066">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3066">See Also</span></span>

- <span data-ttu-id="457c7-3067">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-3067">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-3068">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-3068">fx_media_abort</span></span>
- <span data-ttu-id="457c7-3069">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-3069">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-3070">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-3070">fx_media_check</span></span>
- <span data-ttu-id="457c7-3071">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3071">fx_media_close</span></span>
- <span data-ttu-id="457c7-3072">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3072">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-3073">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-3073">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-3074">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-3074">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-3075">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-3075">fx_media_flush</span></span>
- <span data-ttu-id="457c7-3076">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-3076">fx_media_format</span></span>
- <span data-ttu-id="457c7-3077">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3077">fx_media_open</span></span>
- <span data-ttu-id="457c7-3078">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3078">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-3079">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3079">fx_media_read</span></span>
- <span data-ttu-id="457c7-3080">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-3080">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-3081">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3081">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-3082">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3082">fx_media_write</span></span>
- <span data-ttu-id="457c7-3083">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3083">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="457c7-3084">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3084">fx_media_write</span></span>

<span data-ttu-id="457c7-3085">Skrivningar av logisk sektor</span><span class="sxs-lookup"><span data-stu-id="457c7-3085">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3086">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3086">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="457c7-3087">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3087">Description</span></span>

<span data-ttu-id="457c7-3088">Den här tjänsten skriver den angivna bufferten till den angivna logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3088">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3089">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3089">Input Parameters</span></span>

- <span data-ttu-id="457c7-3090">**media_ptr**: Pekare till ett media som öppnats tidigare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3090">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="457c7-3091">**logical_sector:** Logisk sektor att skriva.</span><span class="sxs-lookup"><span data-stu-id="457c7-3091">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="457c7-3092">**buffer_ptr:** Pekare till källan för den logiska sektorskrivningen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3092">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3093">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3093">Return Values</span></span>

- <span data-ttu-id="457c7-3094">**FX_SUCCESS** (0x00) Lyckad medieskrivning.</span><span class="sxs-lookup"><span data-stu-id="457c7-3094">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="457c7-3095">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3095">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3096">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-3096">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-3097">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-3097">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3098">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-3098">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-3099">**FX_PTR_ERROR** (0x18) Ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3099">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="457c7-3100">**FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3100">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3101">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3101">Allowed From</span></span>

<span data-ttu-id="457c7-3102">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3102">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3103">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3103">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3104">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3104">See Also</span></span>

- <span data-ttu-id="457c7-3105">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="457c7-3105">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="457c7-3106">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="457c7-3106">fx_media_abort</span></span>
- <span data-ttu-id="457c7-3107">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="457c7-3107">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="457c7-3108">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="457c7-3108">fx_media_check</span></span>
- <span data-ttu-id="457c7-3109">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3109">fx_media_close</span></span>
- <span data-ttu-id="457c7-3110">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3110">fx_media_close_notify_set</span></span>
- <span data-ttu-id="457c7-3111">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="457c7-3111">fx_media_exFAT_format</span></span>
- <span data-ttu-id="457c7-3112">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-3112">fx_media_extended_space_available</span></span>
- <span data-ttu-id="457c7-3113">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="457c7-3113">fx_media_flush</span></span>
- <span data-ttu-id="457c7-3114">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="457c7-3114">fx_media_format</span></span>
- <span data-ttu-id="457c7-3115">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3115">fx_media_open</span></span>
- <span data-ttu-id="457c7-3116">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3116">fx_media_open_notify_set</span></span>
- <span data-ttu-id="457c7-3117">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3117">fx_media_read</span></span>
- <span data-ttu-id="457c7-3118">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="457c7-3118">fx_media_space_available</span></span>
- <span data-ttu-id="457c7-3119">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3119">fx_media_volume_get</span></span>
- <span data-ttu-id="457c7-3120">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3120">fx_media_volume_set</span></span>
- <span data-ttu-id="457c7-3121">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3121">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="457c7-3122">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3122">fx_system_date_get</span></span>

<span data-ttu-id="457c7-3123">Hämtar filsystemdatum</span><span class="sxs-lookup"><span data-stu-id="457c7-3123">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3124">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3124">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="457c7-3125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3125">Description</span></span>

<span data-ttu-id="457c7-3126">Den här tjänsten returnerar det aktuella systemdatumet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3126">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3127">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3127">Input Parameters</span></span>

- <span data-ttu-id="457c7-3128">**year**: Pekare till mål för år.</span><span class="sxs-lookup"><span data-stu-id="457c7-3128">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="457c7-3129">**month**: Pekare till mål för månad.</span><span class="sxs-lookup"><span data-stu-id="457c7-3129">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="457c7-3130">**day**: Pekare till mål för dagen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3130">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3131">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3131">Return Values</span></span>

- <span data-ttu-id="457c7-3132">**FX_SUCCESS** (0x00) Lyckad datumhämtning.</span><span class="sxs-lookup"><span data-stu-id="457c7-3132">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="457c7-3133">**FX_PTR_ERROR** (0x18) En eller flera av indataparametrarna är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-3133">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3134">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3134">Allowed From</span></span>

<span data-ttu-id="457c7-3135">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3135">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3136">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3136">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3137">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3137">See Also</span></span>

- <span data-ttu-id="457c7-3138">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3138">fx_system_date_set</span></span>
- <span data-ttu-id="457c7-3139">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3139">fx_system_initialize</span></span>
- <span data-ttu-id="457c7-3140">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3140">fx_system_time_get</span></span>
- <span data-ttu-id="457c7-3141">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3141">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="457c7-3142">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3142">fx_system_date_set</span></span>

<span data-ttu-id="457c7-3143">Anger systemdatum</span><span class="sxs-lookup"><span data-stu-id="457c7-3143">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3144">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3144">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="457c7-3145">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3145">Description</span></span>

<span data-ttu-id="457c7-3146">Den här tjänsten anger systemdatumet som det anges.</span><span class="sxs-lookup"><span data-stu-id="457c7-3146">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-3147">*Den här tjänsten bör anropas strax efter **fx_system_initialize för** att ange det första systemdatumet. Som standard är systemdatumet den senaste allmänna FileX-versionen.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3147">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3148">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3148">Input Parameters</span></span>

- <span data-ttu-id="457c7-3149">**year**: Nytt år.</span><span class="sxs-lookup"><span data-stu-id="457c7-3149">**year**: New year.</span></span> <span data-ttu-id="457c7-3150">Det giltiga intervallet är från 1980 till och med år 2107.</span><span class="sxs-lookup"><span data-stu-id="457c7-3150">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="457c7-3151">**month**: Ny månad.</span><span class="sxs-lookup"><span data-stu-id="457c7-3151">**month**: New month.</span></span> <span data-ttu-id="457c7-3152">Det giltiga intervallet är mellan 1 och 12.</span><span class="sxs-lookup"><span data-stu-id="457c7-3152">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="457c7-3153">**day**: Ny dag.</span><span class="sxs-lookup"><span data-stu-id="457c7-3153">**day**: New day.</span></span> <span data-ttu-id="457c7-3154">Det giltiga intervallet är mellan 1 och 31, beroende på månad och skottår.</span><span class="sxs-lookup"><span data-stu-id="457c7-3154">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3155">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3155">Return Values</span></span>

- <span data-ttu-id="457c7-3156">**FX_SUCCESS** (0x00) Datuminställningen Lyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-3156">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="457c7-3157">**FX_INVALID_YEAR** (0x12) Ogiltigt år angivet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3157">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="457c7-3158">**FX_INVALID_MONTH** (0x13) Ogiltig månad har angetts.</span><span class="sxs-lookup"><span data-stu-id="457c7-3158">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="457c7-3159">**FX_INVALID_DAY** (0x14) Ogiltig dag har angetts.</span><span class="sxs-lookup"><span data-stu-id="457c7-3159">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3160">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3160">Allowed From</span></span>

<span data-ttu-id="457c7-3161">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3161">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3162">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3162">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-3163">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3163">See Also</span></span>

- <span data-ttu-id="457c7-3164">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3164">fx_system_date_get</span></span>
- <span data-ttu-id="457c7-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3165">fx_system_initialize</span></span>
- <span data-ttu-id="457c7-3166">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3166">fx_system_time_get</span></span>
- <span data-ttu-id="457c7-3167">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3167">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="457c7-3168">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3168">fx_system_initialize</span></span>

<span data-ttu-id="457c7-3169">Initierar hela systemet</span><span class="sxs-lookup"><span data-stu-id="457c7-3169">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3170">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3170">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="457c7-3171">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3171">Description</span></span>

<span data-ttu-id="457c7-3172">Den här tjänsten initierar alla större FileX-datastrukturer.</span><span class="sxs-lookup"><span data-stu-id="457c7-3172">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="457c7-3173">Den bör anropas antingen ***i tx_application_define*** eller möjligen från en initieringstråd och måste anropas innan du använder någon annan FileX-tjänst.</span><span class="sxs-lookup"><span data-stu-id="457c7-3173">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-3174">\*När det här anropet initieras ska programmet anropa fx_system_date_set _ och _ fx_system_time_set \* för att börja med ett *korrekt systemdatum och en korrekt tid.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3174">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3175">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3175">Input Parameters</span></span>

<span data-ttu-id="457c7-3176">Ingen</span><span class="sxs-lookup"><span data-stu-id="457c7-3176">None</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3177">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3177">Return Values</span></span>

<span data-ttu-id="457c7-3178">Inga.</span><span class="sxs-lookup"><span data-stu-id="457c7-3178">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3179">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3179">Allowed From</span></span>

<span data-ttu-id="457c7-3180">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3180">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3181">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3181">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3182">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3182">See Also</span></span>

- <span data-ttu-id="457c7-3183">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3183">fx_system_date_get</span></span>
- <span data-ttu-id="457c7-3184">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3184">fx_system_date_set</span></span>
- <span data-ttu-id="457c7-3185">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3185">fx_system_time_get</span></span>
- <span data-ttu-id="457c7-3186">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3186">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="457c7-3187">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3187">fx_system_time_get</span></span>

<span data-ttu-id="457c7-3188">Hämtar aktuell systemtid</span><span class="sxs-lookup"><span data-stu-id="457c7-3188">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3189">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3189">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="457c7-3190">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3190">Description</span></span>

<span data-ttu-id="457c7-3191">Den här tjänsten hämtar den aktuella systemtiden.</span><span class="sxs-lookup"><span data-stu-id="457c7-3191">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3192">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3192">Input Parameters</span></span>

- <span data-ttu-id="457c7-3193">**hour**: Pekare till målet för timme.</span><span class="sxs-lookup"><span data-stu-id="457c7-3193">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="457c7-3194">**minute**: Pekaren till målet för minut.</span><span class="sxs-lookup"><span data-stu-id="457c7-3194">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="457c7-3195">**second**: Pekare till målet för den andra.</span><span class="sxs-lookup"><span data-stu-id="457c7-3195">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3196">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3196">Return Values</span></span>

- <span data-ttu-id="457c7-3197">**FX_SUCCESS** (0x00) Lyckad systemtidshämtning.</span><span class="sxs-lookup"><span data-stu-id="457c7-3197">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="457c7-3198">**FX_PTR_ERROR** (0x18) En eller flera av indataparametrarna</span><span class="sxs-lookup"><span data-stu-id="457c7-3198">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3199">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3199">Allowed From</span></span>

<span data-ttu-id="457c7-3200">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3201">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3201">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3202">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3202">See Also</span></span>

- <span data-ttu-id="457c7-3203">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3203">fx_system_date_get</span></span>
- <span data-ttu-id="457c7-3204">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3204">fx_system_date_set</span></span>
- <span data-ttu-id="457c7-3205">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3205">fx_system_initialize</span></span>
- <span data-ttu-id="457c7-3206">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3206">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="457c7-3207">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3207">fx_system_time_set</span></span>

<span data-ttu-id="457c7-3208">Anger aktuell systemtid</span><span class="sxs-lookup"><span data-stu-id="457c7-3208">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3209">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3209">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="457c7-3210">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3210">Description</span></span>

<span data-ttu-id="457c7-3211">Den här tjänsten anger den aktuella systemtiden till den som anges av indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="457c7-3211">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-3212">*Den här tjänsten ska anropas strax efter **fx_system_initialize för** att ange den första systemtiden. Som standard är systemtiden 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3212">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3213">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3213">Input Parameters</span></span>

- <span data-ttu-id="457c7-3214">**hour**: Ny timme (0–23).</span><span class="sxs-lookup"><span data-stu-id="457c7-3214">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="457c7-3215">**minute**: Ny minut (0–59).</span><span class="sxs-lookup"><span data-stu-id="457c7-3215">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="457c7-3216">**second**: New second (0-59).</span><span class="sxs-lookup"><span data-stu-id="457c7-3216">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3217">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3217">Return Values</span></span>

- <span data-ttu-id="457c7-3218">**FX_SUCCESS** (0x00) Lyckad systemtidshämtning.</span><span class="sxs-lookup"><span data-stu-id="457c7-3218">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="457c7-3219">**FX_INVALID_HOUR**    (0x15) Ny timme är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-3219">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="457c7-3220">**FX_INVALID_MINUTE** (0x16) Ny minut är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-3220">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="457c7-3221">**FX_INVALID_SECOND** (0x17) Ny sekund är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="457c7-3221">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3222">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3222">Allowed From</span></span>

<span data-ttu-id="457c7-3223">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3224">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3224">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="457c7-3225">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3225">See Also</span></span>

- <span data-ttu-id="457c7-3226">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3226">fx_system_date_get</span></span>
- <span data-ttu-id="457c7-3227">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3227">fx_system_date_set</span></span>
- <span data-ttu-id="457c7-3228">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="457c7-3228">fx_system_initialize</span></span>
- <span data-ttu-id="457c7-3229">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3229">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="457c7-3230">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3230">fx_unicode_directory_create</span></span>

<span data-ttu-id="457c7-3231">Skapar en Unicode-katalog</span><span class="sxs-lookup"><span data-stu-id="457c7-3231">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3232">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3232">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="457c7-3233">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3233">Description</span></span>

<span data-ttu-id="457c7-3234">Den här tjänsten skapar en Unicode-namngiven underkatalog i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i parametern Unicode-källnamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3234">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="457c7-3235">Om det lyckas returneras det korta namnet (8.3-format) för den nyligen skapade Unicode-underkatalogen av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3235">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-3236">*Alla åtgärder i Unicode-underkatalogen (vilket gör den till standardsökväg, borttagning osv.) ska göras genom att ange det returnerade korta namnet (8.3-format) till Standard FileX-katalogtjänsterna.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3236">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3237">*Den här tjänsten stöds inte på exFAT-media.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3237">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3238">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3238">Input Parameters</span></span>

- <span data-ttu-id="457c7-3239">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3239">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3240">**source_unicode_name:** Pekare till Unicode-namnet för den nya underkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3240">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="457c7-3241">**source_unicode_length:** Längden på Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3241">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="457c7-3242">**short_name:** Pekare till mål för kortnamn (8.3-format) för den nya Unicode-underkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3242">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3243">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3243">Return Values</span></span>

- <span data-ttu-id="457c7-3244">**FX_SUCCESS** (0x00) Lyckad Unicode-katalog skapas.</span><span class="sxs-lookup"><span data-stu-id="457c7-3244">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="457c7-3245">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3245">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3246">**FX_ALREADY_CREATED** (0x0B) Angiven katalog finns redan.</span><span class="sxs-lookup"><span data-stu-id="457c7-3246">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="457c7-3247">**FX_NO_MORE_SPACE** (0x0A) Inga fler kluster tillgängliga på mediet för den nya katalogposten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3247">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="457c7-3248">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3248">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="457c7-3249">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-3249">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-3250">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3250">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="457c7-3251">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3251">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="457c7-3252">**FX_IO_ERROR (0x90)** Drivrutins-I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="457c7-3252">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3253">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3253">Allowed From</span></span>

<span data-ttu-id="457c7-3254">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3254">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3255">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3255">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3256">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3256">See Also</span></span>

- <span data-ttu-id="457c7-3257">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3257">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-3258">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3258">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-3259">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3259">fx_directory_create</span></span>
- <span data-ttu-id="457c7-3260">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3260">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-3261">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3261">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-3262">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3262">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-3263">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3263">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-3264">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3264">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-3265">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3265">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-3266">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-3266">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-3267">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3267">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-3268">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-3268">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-3269">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3269">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-3270">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3270">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-3271">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-3271">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-3272">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3272">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-3273">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3273">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-3274">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3274">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-3275">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3275">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-3276">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3276">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="457c7-3277">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3277">fx_unicode_directory_rename</span></span>

<span data-ttu-id="457c7-3278">Byter namn på katalogen med Unicode-sträng</span><span class="sxs-lookup"><span data-stu-id="457c7-3278">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3279">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3279">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="457c7-3280">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3280">Description</span></span>

<span data-ttu-id="457c7-3281">Den här tjänsten ändrar en Unicode-namngiven underkatalog till angivet nytt Unicode-namn i den aktuella arbetskatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3281">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="457c7-3282">Unicode-namnparametrarna får inte ha sökvägsinformation.</span><span class="sxs-lookup"><span data-stu-id="457c7-3282">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3283">*Den här tjänsten stöds inte på exFAT-media.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3283">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3284">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3284">Input Parameters</span></span>

- <span data-ttu-id="457c7-3285">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3285">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3286">**old_unicode_name:** Pekare till Unicode-namnet för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3286">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="457c7-3287">**old_unicode_name_length:** Längden på det aktuella Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3287">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="457c7-3288">**new_unicode_name**: Pekare till det nya Unicode-filnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3288">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="457c7-3289">**old_unicode_name_length:** Längden på det nya Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3289">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="457c7-3290">**new_short_name:** Pekare till mål för kortnamn (8.3-format) för den omdöpta Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3290">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="457c7-3291">Byt namn på katalog med Unicode</span><span class="sxs-lookup"><span data-stu-id="457c7-3291">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3292">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3292">Return Values</span></span>

- <span data-ttu-id="457c7-3293">**FX_SUCCESS** (0x00) Lyckad media är öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3293">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="457c7-3294">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3294">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3295">**FX_ALREADY_CREATED** (0x0B) Angivet katalognamn finns redan.</span><span class="sxs-lookup"><span data-stu-id="457c7-3295">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="457c7-3296">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-3296">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3297">**FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-3297">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="457c7-3298">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3298">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="457c7-3299">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-3299">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3300">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3300">Allowed From</span></span>

<span data-ttu-id="457c7-3301">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3302">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3302">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3303">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3303">See Also</span></span>

- <span data-ttu-id="457c7-3304">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3304">fx_directory_attributes_read</span></span>
- <span data-ttu-id="457c7-3305">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3305">fx_directory_attributes_set</span></span>
- <span data-ttu-id="457c7-3306">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3306">fx_directory_create</span></span>
- <span data-ttu-id="457c7-3307">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3307">fx_directory_default_get</span></span>
- <span data-ttu-id="457c7-3308">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3308">fx_directory_default_set</span></span>
- <span data-ttu-id="457c7-3309">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3309">fx_directory_delete</span></span>
- <span data-ttu-id="457c7-3310">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3310">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="457c7-3311">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3311">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="457c7-3312">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3312">fx_directory_information_get</span></span>
- <span data-ttu-id="457c7-3313">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="457c7-3313">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="457c7-3314">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3314">fx_directory_local_path_get</span></span>
- <span data-ttu-id="457c7-3315">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="457c7-3315">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="457c7-3316">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3316">fx_directory_local_path_set</span></span>
- <span data-ttu-id="457c7-3317">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3317">fx_directory_long_name_get</span></span>
- <span data-ttu-id="457c7-3318">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="457c7-3318">fx_directory_name_test</span></span>
- <span data-ttu-id="457c7-3319">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3319">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="457c7-3320">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="457c7-3320">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="457c7-3321">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3321">fx_directory_rename</span></span>
- <span data-ttu-id="457c7-3322">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3322">fx_directory_short_name_get</span></span>
- <span data-ttu-id="457c7-3323">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3323">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="457c7-3324">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3324">fx_unicode_file_create</span></span>

<span data-ttu-id="457c7-3325">Skapar en Unicode-fil</span><span class="sxs-lookup"><span data-stu-id="457c7-3325">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3326">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3326">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="457c7-3327">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3327">Description</span></span>

<span data-ttu-id="457c7-3328">Den här tjänsten skapar en Unicode-namngiven fil i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i parametern Unicode-källnamn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3328">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="457c7-3329">Om det lyckas returneras det korta namnet (8.3-format) för den nyligen skapade Unicode-filen av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3329">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="457c7-3330">*Alla åtgärder i Unicode-filen (öppna, skriva, läsa, stänga osv.) ska göras genom att ange det returnerade korta namnet (8.3-format) till standardfiltjänsterna för FileX.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3330">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3331">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3331">Input Parameters</span></span>


- <span data-ttu-id="457c7-3332">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3332">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3333">**source_unicode_name:** Pekare till Unicode-namnet för den nya filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3333">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="457c7-3334">**source_unicode_length:** Längden på Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3334">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="457c7-3335">**short_name**: Pekare till mål för kortnamn (8.3-format) för den nya Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3335">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3336">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3336">Return Values</span></span>

- <span data-ttu-id="457c7-3337">**FX_SUCCESS** (0x00) Lyckades fil skapas.</span><span class="sxs-lookup"><span data-stu-id="457c7-3337">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="457c7-3338">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3338">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3339">**FX_ALREADY_CREATED** (0x0B) Angiven fil finns redan.</span><span class="sxs-lookup"><span data-stu-id="457c7-3339">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="457c7-3340">**FX_NO_MORE_SPACE** (0x0A) Inga fler kluster tillgängliga på mediet för den nya filposten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3340">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="457c7-3341">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3341">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="457c7-3342">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-3342">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3343">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-3343">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="457c7-3344">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3344">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="457c7-3345">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3345">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3346">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3346">Allowed From</span></span>

<span data-ttu-id="457c7-3347">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3348">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3348">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3349">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3349">See Also</span></span>

- <span data-ttu-id="457c7-3350">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3350">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3351">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3351">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3352">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3352">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3353">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3353">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3354">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3354">fx_file_close</span></span>
- <span data-ttu-id="457c7-3355">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3355">fx_file_create</span></span>
- <span data-ttu-id="457c7-3356">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3356">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3357">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3357">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3358">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3358">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3359">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3359">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3360">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3360">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3361">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3361">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3362">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3362">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3363">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3363">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3364">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3364">fx_file_open</span></span>
- <span data-ttu-id="457c7-3365">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3365">fx_file_read</span></span>
- <span data-ttu-id="457c7-3366">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3366">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3367">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3367">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3368">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3368">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3369">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3369">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3370">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3370">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3371">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3371">fx_file_write</span></span>
- <span data-ttu-id="457c7-3372">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3372">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3373">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-3374">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3374">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-3375">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3375">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="457c7-3376">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3376">fx_unicode_file_rename</span></span>

<span data-ttu-id="457c7-3377">Byter namn på en fil med Unicode-sträng</span><span class="sxs-lookup"><span data-stu-id="457c7-3377">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3378">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3378">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="457c7-3379">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3379">Description</span></span>

<span data-ttu-id="457c7-3380">Den här tjänsten ändrar ett Unicode-namn till angivet nytt Unicode-namn i den aktuella standardkatalogen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3380">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="457c7-3381">Unicode-namnparametrarna får inte ha sökvägsinformation.</span><span class="sxs-lookup"><span data-stu-id="457c7-3381">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3382">*Den här tjänsten stöds inte på exFAT-media.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3382">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3383">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3383">Input Parameters</span></span>

- <span data-ttu-id="457c7-3384">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3384">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3385">**old_unicode_name:** Pekare till Unicode-namnet för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3385">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="457c7-3386">**old_unicode_name_length:** Längden på det aktuella Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3386">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="457c7-3387">**new_unicode_name**: Pekare till det nya Unicode-filnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3387">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="457c7-3388">**new_unicode_name_length:** Längden på det nya Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3388">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="457c7-3389">**new_short_name:** Pekare till mål för kortnamn (8.3-format) för den omdöpta Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3389">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3390">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3390">Return Values</span></span>


- <span data-ttu-id="457c7-3391">**FX_SUCCESS** (0x00) Lyckad media är öppen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3391">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="457c7-3392">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3392">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3393">**FX_ALREADY_CREATED** (0x0B) Det angivna filnamnet finns redan.</span><span class="sxs-lookup"><span data-stu-id="457c7-3393">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="457c7-3394">**FX_IO_ERROR** (0x90) Drivrutins-I/O.</span><span class="sxs-lookup"><span data-stu-id="457c7-3394">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3395">**FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.</span><span class="sxs-lookup"><span data-stu-id="457c7-3395">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="457c7-3396">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3396">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="457c7-3397">**FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="457c7-3397">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3398">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3398">Allowed From</span></span>

<span data-ttu-id="457c7-3399">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3400">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3400">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3401">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3401">See Also</span></span>

- <span data-ttu-id="457c7-3402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3402">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3403">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3404">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3406">fx_file_close</span></span>
- <span data-ttu-id="457c7-3407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3407">fx_file_create</span></span>
- <span data-ttu-id="457c7-3408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3408">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3409">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3413">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3416">fx_file_open</span></span>
- <span data-ttu-id="457c7-3417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3417">fx_file_read</span></span>
- <span data-ttu-id="457c7-3418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3418">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3419">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3420">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3421">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3422">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3423">fx_file_write</span></span>
- <span data-ttu-id="457c7-3424">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3424">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3425">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3425">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-3426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3426">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-3427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3427">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="457c7-3428">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3428">fx_unicode_length_get</span></span>

<span data-ttu-id="457c7-3429">Hämtar längden på Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="457c7-3429">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3430">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3430">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="457c7-3431">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3431">Description</span></span>

<span data-ttu-id="457c7-3432">Den här tjänsten avgör längden på det angivna Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3432">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="457c7-3433">Ett Unicode-tecken representeras av två byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-3433">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="457c7-3434">Ett Unicode-namn är en serie med Unicode-tecken med två byte som avslutas med två NULL-byte (två byte med värdet 0).</span><span class="sxs-lookup"><span data-stu-id="457c7-3434">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3435">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3435">Input Parameters</span></span>

<span data-ttu-id="457c7-3436">**unicode_name**: Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3436">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3437">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3437">Return Values</span></span>

<span data-ttu-id="457c7-3438">**length**: Längden på Unicode-namnet (antalet Unicode-tecken i namnet).</span><span class="sxs-lookup"><span data-stu-id="457c7-3438">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3439">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3439">Allowed From</span></span>

<span data-ttu-id="457c7-3440">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3440">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3441">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3441">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3442">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3442">See Also</span></span>

- <span data-ttu-id="457c7-3443">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3443">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3444">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3444">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3445">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3445">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3446">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3446">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3447">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3447">fx_file_close</span></span>
- <span data-ttu-id="457c7-3448">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3448">fx_file_create</span></span>
- <span data-ttu-id="457c7-3449">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3449">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3450">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3450">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3451">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3451">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3452">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3452">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3453">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3453">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3454">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3454">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3455">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3455">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3456">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3456">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3457">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3457">fx_file_open</span></span>
- <span data-ttu-id="457c7-3458">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3458">fx_file_read</span></span>
- <span data-ttu-id="457c7-3459">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3459">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3460">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3460">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3461">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3461">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3462">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3462">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3463">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3463">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3464">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3464">fx_file_write</span></span>
- <span data-ttu-id="457c7-3465">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3465">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3466">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3466">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-3467">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3467">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-3468">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3468">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-3469">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3469">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="457c7-3470">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="457c7-3470">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="457c7-3471">Hämtar längden på Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="457c7-3471">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3472">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3472">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="457c7-3473">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3473">Description</span></span>

<span data-ttu-id="457c7-3474">Den här tjänsten hämtar längden på det angivna Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3474">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="457c7-3475">Ett Unicode-tecken representeras av två byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-3475">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="457c7-3476">Ett Unicode-namn är en serie med Unicode-tecken på tvåbyte som avslutas med två NULL-byte (två byte med ett värde på 0).</span><span class="sxs-lookup"><span data-stu-id="457c7-3476">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3477">*Den här tjänsten är **identisk med fx_unicode_length_get()** förutom att anroparen skickar storleken på unicode_name bufferten, inklusive de två NULL-tecknen.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3477">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3478">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3478">Input Parameters</span></span>

- <span data-ttu-id="457c7-3479">**unicode_name**: Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3479">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="457c7-3480">**buffer_length:** Storlek på Unicode-namnbuffert.</span><span class="sxs-lookup"><span data-stu-id="457c7-3480">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3481">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3481">Return Values</span></span>

<span data-ttu-id="457c7-3482">**length**: Längden på Unicode-namnet (antalet Unicode-tecken i namnet).</span><span class="sxs-lookup"><span data-stu-id="457c7-3482">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3483">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3483">Allowed From</span></span>

<span data-ttu-id="457c7-3484">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3484">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3485">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3485">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3486">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3486">See Also</span></span>

- <span data-ttu-id="457c7-3487">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3487">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3488">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3488">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3489">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3489">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3490">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3490">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3491">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3491">fx_file_close</span></span>
- <span data-ttu-id="457c7-3492">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3492">fx_file_create</span></span>
- <span data-ttu-id="457c7-3493">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3493">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3494">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3494">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3495">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3495">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3496">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3496">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3497">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3497">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3498">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3498">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3499">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3499">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3500">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3500">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3501">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3501">fx_file_open</span></span>
- <span data-ttu-id="457c7-3502">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3502">fx_file_read</span></span>
- <span data-ttu-id="457c7-3503">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3503">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3504">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3504">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3505">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3505">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3506">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3506">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3507">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3507">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3508">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3508">fx_file_write</span></span>
- <span data-ttu-id="457c7-3509">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3509">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3510">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3510">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-3511">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3511">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-3512">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3512">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-3513">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3513">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="457c7-3514">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3514">fx_unicode_name_get</span></span>

<span data-ttu-id="457c7-3515">Hämtar Unicode-namn från kortnamn</span><span class="sxs-lookup"><span data-stu-id="457c7-3515">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3516">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3516">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="457c7-3517">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3517">Description</span></span>

<span data-ttu-id="457c7-3518">Den här tjänsten hämtar Unicode-namnet som är associerat med det angivna kortnamnet (8.3-format) i den aktuella standardkatalogen– ingen sökvägsinformation tillåts i den korta namnparametern.</span><span class="sxs-lookup"><span data-stu-id="457c7-3518">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="457c7-3519">Om det lyckas returneras Unicode-namnet som är associerat med det korta namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3519">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3520">*Den här tjänsten kan användas för att hämta Unicode-namn för både filer och underkataloger.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3520">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3521">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3521">Input Parameters</span></span>

- <span data-ttu-id="457c7-3522">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3522">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3523">**short_name** Pekare till kortnamn (8.3-format).</span><span class="sxs-lookup"><span data-stu-id="457c7-3523">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="457c7-3524">**destination_unicode_name: Pekare** till målet för Unicode-namnet som är associerat med det angivna kortnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3524">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="457c7-3525">**destination_unicode_length: Pekare** till returnerad Unicode-namnlängd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3525">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3526">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3526">Return Values</span></span>

- <span data-ttu-id="457c7-3527">**FX_SUCCESS** (0x00) Lyckad hämtning av Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3527">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="457c7-3528">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3528">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="457c7-3529">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-3529">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-3530">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-3530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3531">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3531">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3532">**FX_NOT_FOUND** (0x04) Kortnamnet hittades inte eller så är Unicode-målstorleken för liten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3532">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="457c7-3533">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-3533">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-3534">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3534">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="457c7-3535">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3535">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3536">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3536">Allowed From</span></span>

<span data-ttu-id="457c7-3537">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3537">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3538">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3538">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3539">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3539">See Also</span></span>

- <span data-ttu-id="457c7-3540">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3540">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3541">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3541">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3542">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3542">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3543">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3543">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3544">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3544">fx_file_close</span></span>
- <span data-ttu-id="457c7-3545">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3545">fx_file_create</span></span>
- <span data-ttu-id="457c7-3546">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3546">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3547">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3547">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3548">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3548">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3549">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3549">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3550">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3550">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3551">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3551">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3552">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3552">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3553">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3553">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3554">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3554">fx_file_open</span></span>
- <span data-ttu-id="457c7-3555">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3555">fx_file_read</span></span>
- <span data-ttu-id="457c7-3556">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3556">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3557">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3557">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3558">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3558">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3559">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3559">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3560">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3560">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3561">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3561">fx_file_write</span></span>
- <span data-ttu-id="457c7-3562">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3562">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3563">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3563">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-3564">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3564">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-3565">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3565">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="457c7-3566">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="457c7-3566">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="457c7-3567">Hämtar Unicode-namn från kortnamn</span><span class="sxs-lookup"><span data-stu-id="457c7-3567">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3568">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3568">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="457c7-3569">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3569">Description</span></span>

<span data-ttu-id="457c7-3570">Den här tjänsten hämtar Unicode-namnet som är associerat med det angivna kortnamnet (8.3-format) i den aktuella standardkatalogen– ingen sökvägsinformation tillåts i den korta namnparametern.</span><span class="sxs-lookup"><span data-stu-id="457c7-3570">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="457c7-3571">Om det lyckas returneras Unicode-namnet som är associerat med det korta namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3571">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3572">\*Den här tjänsten är identisk med \***fx_unicode_name_get**, förutom att anroparen tillhandahåller storleken på _Unicode-målbufferten som ett indataargument. Detta gör att tjänsten kan garantera att den inte skriver över Unicode-målbufferten_</span><span class="sxs-lookup"><span data-stu-id="457c7-3572">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3573">*Den här tjänsten kan användas för att hämta Unicode-namn för både filer och underkataloger.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3573">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3574">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3574">Input Parameters</span></span>

- <span data-ttu-id="457c7-3575">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3575">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3576">**short_name**: Pekare till kortnamn (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="457c7-3576">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="457c7-3577">**destination_unicode_name: Pekare** till målet för Unicode-namnet som är associerat med det angivna kortnamnet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3577">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="457c7-3578">**destination_unicode_length: Pekare** till returnerad Unicode-namnlängd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3578">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="457c7-3579">**unicode_name_buffer_length:** Storlek på Unicode-namnbufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3579">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="457c7-3580">Obs! En NULL-avslutning krävs, vilket gör en extra byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-3580">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3581">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3581">Return Values</span></span>

- <span data-ttu-id="457c7-3582">**FX_SUCCESS** (0x00) Lyckad hämtning av Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3582">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="457c7-3583">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3583">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="457c7-3584">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-3584">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-3585">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-3585">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3586">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3586">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3587">**FX_NOT_FOUND** (0x04) Kortnamnet hittades inte eller så är Unicode-målstorleken för liten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3587">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="457c7-3588">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-3588">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-3589">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3589">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="457c7-3590">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3590">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3591">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3591">Allowed From</span></span>

<span data-ttu-id="457c7-3592">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3592">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3593">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3593">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3594">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3594">See Also</span></span>

- <span data-ttu-id="457c7-3595">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3595">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3596">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3596">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3597">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3597">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3598">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3598">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3599">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3599">fx_file_close</span></span>
- <span data-ttu-id="457c7-3600">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3600">fx_file_create</span></span>
- <span data-ttu-id="457c7-3601">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3601">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3602">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3602">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3603">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3603">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3604">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3604">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3605">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3605">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3606">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3606">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3607">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3607">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3608">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3608">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3609">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3609">fx_file_open</span></span>
- <span data-ttu-id="457c7-3610">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3610">fx_file_read</span></span>
- <span data-ttu-id="457c7-3611">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3611">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3612">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3612">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3613">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3613">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3614">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3614">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3615">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3615">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3616">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3616">fx_file_write</span></span>
- <span data-ttu-id="457c7-3617">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3617">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3618">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3618">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-3619">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3619">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-3620">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3620">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="457c7-3621">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3621">fx_unicode_short_name_get</span></span>

<span data-ttu-id="457c7-3622">Hämtar kort namn från Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="457c7-3622">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3623">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3623">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="457c7-3624">Den här tjänsten hämtar det korta namnet (formatet 8.3) som är associerat med Unicode-namnet i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i Unicode-namnparametern.</span><span class="sxs-lookup"><span data-stu-id="457c7-3624">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="457c7-3625">Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3625">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3626">*Den här tjänsten kan användas för att hämta korta namn för både filer och underkataloger.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3626">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3627">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3627">Input Parameters</span></span>

- <span data-ttu-id="457c7-3628">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3628">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3629">**source_unicode_name:** Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3629">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="457c7-3630">**source_unicode_length:** Längden på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3630">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="457c7-3631">**destination_short_name:** Pekare till mål för kortnamnet (formatet 8.3).</span><span class="sxs-lookup"><span data-stu-id="457c7-3631">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="457c7-3632">Detta måste vara minst 13 byte stort.</span><span class="sxs-lookup"><span data-stu-id="457c7-3632">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3633">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3633">Return Values</span></span>

- <span data-ttu-id="457c7-3634">**FX_SUCCESS** (0x00) Kortnamnhämtningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-3634">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="457c7-3635">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3635">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="457c7-3636">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-3636">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="457c7-3637">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-3637">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3638">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3638">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3639">**FX_NOT_FOUND** (0x04) Unicode-namn hittades inte.</span><span class="sxs-lookup"><span data-stu-id="457c7-3639">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="457c7-3640">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3640">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="457c7-3641">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-3641">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-3642">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3642">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="457c7-3643">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3643">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3644">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3644">Allowed From</span></span>

<span data-ttu-id="457c7-3645">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3645">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3646">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3646">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3647">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3647">See Also</span></span>

- <span data-ttu-id="457c7-3648">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3648">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3649">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3649">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3650">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3650">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3651">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3651">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3652">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3652">fx_file_close</span></span>
- <span data-ttu-id="457c7-3653">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3653">fx_file_create</span></span>
- <span data-ttu-id="457c7-3654">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3654">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3655">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3655">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3656">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3656">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3657">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3657">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3658">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3658">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3659">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3659">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3660">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3660">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3661">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3661">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3662">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3662">fx_file_open</span></span>
- <span data-ttu-id="457c7-3663">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3663">fx_file_read</span></span>
- <span data-ttu-id="457c7-3664">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3664">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3665">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3665">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3666">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3666">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3667">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3667">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3668">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3668">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3669">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3669">fx_file_write</span></span>
- <span data-ttu-id="457c7-3670">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3670">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3671">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3671">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-3672">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3672">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-3673">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3673">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="457c7-3674">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="457c7-3674">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="457c7-3675">Hämtar kort namn från Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="457c7-3675">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="457c7-3676">Prototyp</span><span class="sxs-lookup"><span data-stu-id="457c7-3676">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="457c7-3677">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="457c7-3677">Description</span></span>

<span data-ttu-id="457c7-3678">Den här tjänsten hämtar det korta namnet (formatet 8.3) som är associerat med Unicode-namnet i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i Unicode-namnparametern.</span><span class="sxs-lookup"><span data-stu-id="457c7-3678">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="457c7-3679">Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3679">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="457c7-3680">*Den här tjänsten är identisk **med fx_unicode_short_name_get()**, förutom att anroparen tillhandahåller storleken på målbufferten som ett indataargument. Detta gör att tjänsten kan garantera att det korta namnet inte överskrider målbufferten.*</span><span class="sxs-lookup"><span data-stu-id="457c7-3680">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="457c7-3681">*Den här tjänsten kan användas för att hämta korta namn för både filer och underkataloger*</span><span class="sxs-lookup"><span data-stu-id="457c7-3681">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="457c7-3682">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="457c7-3682">Input Parameters</span></span>

- <span data-ttu-id="457c7-3683">**media_ptr:** Pekare till mediakontrollblock.</span><span class="sxs-lookup"><span data-stu-id="457c7-3683">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="457c7-3684">**source_unicode_name:** Pekare till Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3684">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="457c7-3685">**source_unicode_length:** Längden på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="457c7-3685">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="457c7-3686">**destination_short_name:** Pekare till mål för kortnamnet (formatet 8.3).</span><span class="sxs-lookup"><span data-stu-id="457c7-3686">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="457c7-3687">Detta måste vara minst 13 byte stort.</span><span class="sxs-lookup"><span data-stu-id="457c7-3687">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="457c7-3688">**short_name_buffer_length:** Storleken på målbufferten.</span><span class="sxs-lookup"><span data-stu-id="457c7-3688">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="457c7-3689">Buffertstorleken måste vara minst 14 byte.</span><span class="sxs-lookup"><span data-stu-id="457c7-3689">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="457c7-3690">Returvärden</span><span class="sxs-lookup"><span data-stu-id="457c7-3690">Return Values</span></span>

- <span data-ttu-id="457c7-3691">**FX_SUCCESS** (0x00) Kortnamnhämtningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="457c7-3691">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="457c7-3692">**FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.</span><span class="sxs-lookup"><span data-stu-id="457c7-3692">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="457c7-3693">**FX_FILE_CORRUPT** (0x08) Filen är skadad</span><span class="sxs-lookup"><span data-stu-id="457c7-3693">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="457c7-3694">**FX_IO_ERROR** (0x90) I/O-drivrutin.</span><span class="sxs-lookup"><span data-stu-id="457c7-3694">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="457c7-3695">**FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3695">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="457c7-3696">**FX_NOT_FOUND** (0x04) Unicode-namn hittades inte.</span><span class="sxs-lookup"><span data-stu-id="457c7-3696">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="457c7-3697">**FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.</span><span class="sxs-lookup"><span data-stu-id="457c7-3697">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="457c7-3698">**FX_SECTOR_INVALID** (0x89) Ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="457c7-3698">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="457c7-3699">**FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.</span><span class="sxs-lookup"><span data-stu-id="457c7-3699">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="457c7-3700">**FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="457c7-3700">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="457c7-3701">Tillåts från</span><span class="sxs-lookup"><span data-stu-id="457c7-3701">Allowed From</span></span>

<span data-ttu-id="457c7-3702">Trådar</span><span class="sxs-lookup"><span data-stu-id="457c7-3702">Threads</span></span>

### <a name="example"></a><span data-ttu-id="457c7-3703">Exempel</span><span class="sxs-lookup"><span data-stu-id="457c7-3703">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="457c7-3704">Se även</span><span class="sxs-lookup"><span data-stu-id="457c7-3704">See Also</span></span>

- <span data-ttu-id="457c7-3705">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3705">fx_file_allocate</span></span>
- <span data-ttu-id="457c7-3706">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3706">fx_file_attributes_read</span></span>
- <span data-ttu-id="457c7-3707">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3707">fx_file_attributes_set</span></span>
- <span data-ttu-id="457c7-3708">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3708">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3709">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="457c7-3709">fx_file_close</span></span>
- <span data-ttu-id="457c7-3710">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3710">fx_file_create</span></span>
- <span data-ttu-id="457c7-3711">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3711">fx_file_date_time_set</span></span>
- <span data-ttu-id="457c7-3712">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="457c7-3712">fx_file_delete</span></span>
- <span data-ttu-id="457c7-3713">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3713">fx_file_extended_allocate</span></span>
- <span data-ttu-id="457c7-3714">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="457c7-3714">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="457c7-3715">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3715">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="457c7-3716">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3716">fx_file_extended_seek</span></span>
- <span data-ttu-id="457c7-3717">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3717">fx_file_extended_truncate</span></span>
- <span data-ttu-id="457c7-3718">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3718">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="457c7-3719">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="457c7-3719">fx_file_open</span></span>
- <span data-ttu-id="457c7-3720">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="457c7-3720">fx_file_read</span></span>
- <span data-ttu-id="457c7-3721">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3721">fx_file_relative_seek</span></span>
- <span data-ttu-id="457c7-3722">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3722">fx_file_rename</span></span>
- <span data-ttu-id="457c7-3723">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="457c7-3723">fx_file_seek</span></span>
- <span data-ttu-id="457c7-3724">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="457c7-3724">fx_file_truncate</span></span>
- <span data-ttu-id="457c7-3725">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="457c7-3725">fx_file_truncate_release</span></span>
- <span data-ttu-id="457c7-3726">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="457c7-3726">fx_file_write</span></span>
- <span data-ttu-id="457c7-3727">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="457c7-3727">fx_file_write_notify_set</span></span>
- <span data-ttu-id="457c7-3728">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="457c7-3728">fx_unicode_file_create</span></span>
- <span data-ttu-id="457c7-3729">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="457c7-3729">fx_unicode_file_rename</span></span>
- <span data-ttu-id="457c7-3730">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3730">fx_unicode_name_get</span></span>
- <span data-ttu-id="457c7-3731">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="457c7-3731">fx_unicode_short_name_get</span></span>
