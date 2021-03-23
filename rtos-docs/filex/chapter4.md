---
title: Kapitel 4 – Beskrivning av Azure återställnings tider FileX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider FileX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826544"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="5b3fc-103">Kapitel 4 – Beskrivning av Azure återställnings tider FileX-tjänster</span><span class="sxs-lookup"><span data-stu-id="5b3fc-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="5b3fc-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider FileX-tjänster i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="5b3fc-105">Tjänst namn är utformade så att alla liknande tjänster grupperas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="5b3fc-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="5b3fc-107">Läser katalogattribut</span><span class="sxs-lookup"><span data-stu-id="5b3fc-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-108">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="5b3fc-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-109">Description</span></span>

<span data-ttu-id="5b3fc-110">Den här tjänsten läser katalogens attribut från det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-111">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-111">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-112">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-113">**directory_name**: pekar mot namnet på den begärda katalogen (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="5b3fc-114">**attribut** _Ptr: pekar mot målet för katalogens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="5b3fc-115">Katalogattribut returneras i ett bit kart format med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="5b3fc-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="5b3fc-117">FX_HIDDEN (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="5b3fc-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="5b3fc-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="5b3fc-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="5b3fc-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-122">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-122">Return Values</span></span>

- <span data-ttu-id="5b3fc-123">**FX_SUCCESS** (0x00) attributen för lyckad katalog läsning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="5b3fc-124">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-125">Det gick inte att hitta **FX-_NOT** (0x04) som angavs i mediet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="5b3fc-126">**FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="5b3fc-127">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-128">**FX_FILE_CORRUPT** 0X08-filen är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-129">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-130">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-131">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-132">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="5b3fc-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="5b3fc-133">**FX_PTR_ERROR** (0X18) ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="5b3fc-134">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-135">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-135">Allowed From</span></span>

<span data-ttu-id="5b3fc-136">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-138">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-138">See Also</span></span>

- <span data-ttu-id="5b3fc-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-140">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-141">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-142">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-143">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-146">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-152">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-155">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="5b3fc-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="5b3fc-160">Anger katalogattribut</span><span class="sxs-lookup"><span data-stu-id="5b3fc-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-161">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="5b3fc-162">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-162">Description</span></span>

<span data-ttu-id="5b3fc-163">Den här tjänsten anger katalogens attribut till dem som anges av anroparen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-164">*Det här programmet får bara ändra en delmängd av katalogens attribut med den här tjänsten. Alla försök att ange ytterligare attribut leder till ett fel.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-165">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-165">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-166">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-167">**directory_name**: pekar mot namnet på den begärda katalogen (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="5b3fc-168">**attribut**: de nya attributen för den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="5b3fc-169">Giltiga katalogattribut definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="5b3fc-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="5b3fc-171">FX_HIDDEN (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="5b3fc-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="5b3fc-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-174">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-174">Return Values</span></span>

- <span data-ttu-id="5b3fc-175">**FX_SUCCESS** (0x00) konfigurerat katalog-Attribute</span><span class="sxs-lookup"><span data-stu-id="5b3fc-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="5b3fc-176">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-177">Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04) i mediet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="5b3fc-178">**FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="5b3fc-179">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-180">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat</span><span class="sxs-lookup"><span data-stu-id="5b3fc-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="5b3fc-181">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-182">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-183">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-184">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-185">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="5b3fc-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="5b3fc-186">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="5b3fc-187">**FX_PTR_ERROR** (0X18) ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="5b3fc-188">**FX_INVALID_ATTR** (0X19) ogiltiga attribut har marker ATS.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="5b3fc-189">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-190">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-190">Allowed From</span></span>

<span data-ttu-id="5b3fc-191">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-192">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-193">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-193">See Also</span></span>

- <span data-ttu-id="5b3fc-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-195">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-196">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-197">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-198">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-201">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-207">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-210">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="5b3fc-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-214">fx_directory_create</span></span>

<span data-ttu-id="5b3fc-215">Skapar under Katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-216">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-217">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-217">Description</span></span>

<span data-ttu-id="5b3fc-218">Den här tjänsten skapar en under katalog i den aktuella standard katalogen eller i sökvägen som anges i katalog namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="5b3fc-219">Till skillnad från rot katalogen har under kataloger ingen gräns för hur många filer de kan innehålla.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="5b3fc-220">Rot katalogen kan bara innehålla antalet poster som fastställs av start posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-221">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-221">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-222">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-223">**directory_name**: pekar på namnet på katalogen som ska skapas (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-224">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-224">Return Values</span></span>

- <span data-ttu-id="5b3fc-225">**FX_SUCCESS** (0x00) katalogen har skapats.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="5b3fc-226">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-227">Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04) i mediet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="5b3fc-228">**FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="5b3fc-229">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-230">**FX_FILE _CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-231">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-232">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-233">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-234">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="5b3fc-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="5b3fc-235">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="5b3fc-236">**FX_PTR_ERROR** (0X18) ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="5b3fc-237">**FX_INVALID_ATTR** (0X19) ogiltiga attribut har marker ATS.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="5b3fc-238">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-239">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-239">Allowed From</span></span>

<span data-ttu-id="5b3fc-240">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-241">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-242">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-242">See Also</span></span>

- <span data-ttu-id="5b3fc-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-245">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-246">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-247">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-250">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-256">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-259">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="5b3fc-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-263">fx_directory_default_get</span></span>

<span data-ttu-id="5b3fc-264">Hämtar senaste standard katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-265">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-266">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-266">Description</span></span>

<span data-ttu-id="5b3fc-267">Den här tjänsten returnerar pekaren till den sökväg som senast angavs av ***fx_directory_default_set***.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="5b3fc-268">Om standard katalogen inte har angetts eller om den aktuella standard katalogen är rot katalogen returneras ett värde för FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-269">*Standard storleken för den interna Sök vägs strängen är 256 tecken. Du kan ändra det genom att ändra **FX_MAXIMUM_PATH** i **fx_api. h** och återskapa hela FileX-biblioteket. Tecken Strängs Sök vägen upprätthålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-270">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-270">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-271">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-272">**return_path_name**: pekar mot målet för den senaste standard katalog strängen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="5b3fc-273">Värdet FX_NULL returneras om den aktuella inställningen för standard katalogen är roten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="5b3fc-274">När mediet har öppnats är roten standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-275">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-275">Return Values</span></span>

- <span data-ttu-id="5b3fc-276">**FX_SUCCESS** (0x00) standard katalog hämtning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="5b3fc-277">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-278">**FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="5b3fc-279">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-280">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-280">Allowed From</span></span>

<span data-ttu-id="5b3fc-281">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-282">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-283">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-283">See Also</span></span>

- <span data-ttu-id="5b3fc-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-286">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-287">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-288">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-291">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-297">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-300">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="5b3fc-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-304">fx_directory_default_set</span></span>

<span data-ttu-id="5b3fc-305">Ställer in standard katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-306">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-307">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-307">Description</span></span>

<span data-ttu-id="5b3fc-308">Den här tjänsten anger standard katalogen för mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="5b3fc-309">Om värdet FX_NULL anges, anges standard katalogen till mediets rot Katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="5b3fc-310">Alla efterföljande fil åtgärder som inte uttryckligen anger en sökväg kommer att använda den här katalogen som standard.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-311">*Standard storleken för den interna Sök vägs strängen är 256 tecken. Du kan ändra det genom att ändra **FX_MAXIMUM_PATH** i **fx_api. h** och återskapa hela FileX-biblioteket. Tecken Strängs Sök vägen upprätthålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-312">*För namn som anges av programmet stöder FileX både omvänt snedstreck ( \\ ) och snedstreck (/) för att skilja kataloger, under kataloger och fil namn. FileX använder dock bara det omvända snedstrecket i sökvägar som returneras till programmet.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-313">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-313">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-314">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-315">**new_path_name**: pekar mot nytt standard katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="5b3fc-316">Om värdet FX_NULL anges, är standard katalogen för mediet inställt på mediets rot Katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-317">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-317">Return Values</span></span>

- <span data-ttu-id="5b3fc-318">**FX_SUCCESS** (0x00) standard katalog uppsättning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="5b3fc-319">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-320">Det gick inte att hitta **FX_INVALID_PATH** (0X0D) ny katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="5b3fc-321">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-322">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-323">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-323">Allowed From</span></span>

<span data-ttu-id="5b3fc-324">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-325">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-326">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-326">See Also</span></span>

- <span data-ttu-id="5b3fc-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-329">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-330">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-331">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-334">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-340">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-343">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="5b3fc-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-347">fx_directory_delete</span></span>

<span data-ttu-id="5b3fc-348">Tar bort under Katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-349">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-350">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-350">Description</span></span>

<span data-ttu-id="5b3fc-351">Den här tjänsten tar bort den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-351">This service deletes the specified directory.</span></span> <span data-ttu-id="5b3fc-352">Observera att katalogen måste vara tom för att den ska kunna tas bort.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-353">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-353">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-354">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-355">**directory_name**: pekar till namnet på katalogen som ska tas bort (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-356">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-356">Return Values</span></span>

- <span data-ttu-id="5b3fc-357">**FX_SUCCESS** (0X00) lyckad katalog borttagning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="5b3fc-358">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-359">Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="5b3fc-360">Den angivna katalogen för **FX_DIR_NOT_EMPTY** (0x10) är inte tom</span><span class="sxs-lookup"><span data-stu-id="5b3fc-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="5b3fc-361">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-362">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat</span><span class="sxs-lookup"><span data-stu-id="5b3fc-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="5b3fc-363">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-364">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-365">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-366">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-367">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="5b3fc-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="5b3fc-368">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="5b3fc-369">**FX_NOT_DIRECTORY** (0X0E) inte en katalog post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="5b3fc-370">**FX_PTR_ERROR** (0X18) ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="5b3fc-371">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-372">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-372">Allowed From</span></span>

<span data-ttu-id="5b3fc-373">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-374">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-375">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-375">See Also</span></span>

- <span data-ttu-id="5b3fc-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-378">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-379">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-380">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-383">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-389">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-392">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="5b3fc-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="5b3fc-397">Hämtar första katalog posten</span><span class="sxs-lookup"><span data-stu-id="5b3fc-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-398">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-399">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-399">Description</span></span>

<span data-ttu-id="5b3fc-400">Den här tjänsten hämtar det första post namnet i standard katalogen och kopierar den till det angivna målet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-401">*Det angivna målet måste vara tillräckligt stort för att rymma det maximala storleks FileX namnet, som definieras av **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="5b3fc-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-402">*Om du använder en icke-lokal sökväg är det viktigt att förhindra (med en ThreadX semafor, mutex eller prioritets nivå ändring) andra program trådar från att ändra katalogen medan en katalogs traversr äger rum. Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-403">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-403">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-404">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-405">**return_entry_name**: pekar mot mål för det första post namnet i standard katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-406">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-406">Return Values</span></span>

- <span data-ttu-id="5b3fc-407">**FX_SUCCESS** (0x00) den första katalog posten hittades</span><span class="sxs-lookup"><span data-stu-id="5b3fc-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="5b3fc-408">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-409">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="5b3fc-410">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-411">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-412">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-413">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-414">**FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="5b3fc-415">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd</span><span class="sxs-lookup"><span data-stu-id="5b3fc-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-416">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-416">Allowed From</span></span>

<span data-ttu-id="5b3fc-417">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-418">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-419">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-419">See Also</span></span>

- <span data-ttu-id="5b3fc-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-422">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-423">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-424">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-425">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-427">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-433">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-436">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="5b3fc-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="5b3fc-441">Hämtar den första katalog posten med fullständig information</span><span class="sxs-lookup"><span data-stu-id="5b3fc-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-442">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="5b3fc-443">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-443">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-444">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-445">**directory_name**: pekar mot målet som namn på en katalog post.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="5b3fc-446">Måste vara minst lika stor som FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="5b3fc-447">**attribut**: om det inte är null pekar pekaren på målet för postens attribut att placeras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="5b3fc-448">Attributen returneras i formatet bit-Map med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="5b3fc-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="5b3fc-450">**FX_HIDDEN** (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="5b3fc-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="5b3fc-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="5b3fc-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="5b3fc-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="5b3fc-455">**storlek**: om den inte är null pekar markören mot målet för postens storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="5b3fc-456">**år**: om det inte är null pekar pekaren på målet för postens ändrings år.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="5b3fc-457">**månad**: om det inte är null pekar pekaren på målet för postens månads ändring.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="5b3fc-458">**dag**: om den inte är null pekar du på målet för postens dag.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="5b3fc-459">**timme**: om det inte är null pekar pekaren på målet för postens ändrings tid.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="5b3fc-460">**Minute**: om den inte är null pekar du på målet för postens minuters ändring.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="5b3fc-461">**sekund**: om det inte är null pekar pekaren på målet för postens andra ändring.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-462">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-462">Return Values</span></span>

- <span data-ttu-id="5b3fc-463">**FX_SUCCESS** (0x00) den första katalog posten hittades</span><span class="sxs-lookup"><span data-stu-id="5b3fc-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="5b3fc-464">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-465">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="5b3fc-466">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-467">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat</span><span class="sxs-lookup"><span data-stu-id="5b3fc-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="5b3fc-468">**FX_FILE _CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-469">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-470">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-471">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-472">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="5b3fc-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="5b3fc-473">**FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="5b3fc-474">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-475">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-475">Allowed From</span></span>

<span data-ttu-id="5b3fc-476">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-477">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-477">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-478">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-478">See Also</span></span>

- <span data-ttu-id="5b3fc-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-481">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-482">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-483">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-484">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-486">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-492">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-495">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="5b3fc-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-499">fx_directory_information_get:</span></span>

<span data-ttu-id="5b3fc-500">Hämtar information om katalog post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-501">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="5b3fc-502">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-502">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-503">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-504">**directory_name**: pekar på katalog postens namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="5b3fc-505">**attribut**: pekar mot målet för attributen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="5b3fc-506">**storlek**: pekar mot målets storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="5b3fc-507">**år**: pekare till målet för året.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="5b3fc-508">**månad**: pekare till målet för månaden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="5b3fc-509">**dag**: pekar mot målet för dagen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="5b3fc-510">**timme**: pekare till målet för timmen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="5b3fc-511">**minut**: pekar på målet för minuten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="5b3fc-512">**sekund**: pekar mot målet för den andra.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-513">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-513">Return Values</span></span>

- <span data-ttu-id="5b3fc-514">**FX_SUCCESS** (0x00) den första katalog posten hittades</span><span class="sxs-lookup"><span data-stu-id="5b3fc-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="5b3fc-515">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-516">Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04) i mediet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="5b3fc-517">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-518">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="5b3fc-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="5b3fc-519">**FX_FILE _CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-520">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-521">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-522">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-523">**FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="5b3fc-524">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-525">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-525">Allowed From</span></span>

<span data-ttu-id="5b3fc-526">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-527">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-527">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-528">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-528">See Also</span></span>

- <span data-ttu-id="5b3fc-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-531">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-532">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-533">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-534">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-542">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-545">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="5b3fc-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="5b3fc-550">Rensar standard lokal sökväg</span><span class="sxs-lookup"><span data-stu-id="5b3fc-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-551">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="5b3fc-552">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-552">Description</span></span>

<span data-ttu-id="5b3fc-553">Den här tjänsten rensar den tidigare lokala Sök vägs inställningen för den anropande tråden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-554">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-554">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-555">**media_ptr**: pekar på ett tidigare öppnat medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-556">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-556">Return Values</span></span>

- <span data-ttu-id="5b3fc-557">**FX_SUCCESS** (0x00) den lokala sökvägen är klar.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="5b3fc-558">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är för närvarande inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="5b3fc-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH definieras</span><span class="sxs-lookup"><span data-stu-id="5b3fc-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="5b3fc-560">**FX_PTR_ERROR** (0X18) ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-561">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-561">Allowed From</span></span>

<span data-ttu-id="5b3fc-562">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-563">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-564">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-564">See Also</span></span>

- <span data-ttu-id="5b3fc-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-567">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-568">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-569">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-570">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-573">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-578">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-581">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="5b3fc-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="5b3fc-586">Hämtar den aktuella lokala Sök vägs strängen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-587">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-588">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-588">Description</span></span>

<span data-ttu-id="5b3fc-589">Den här tjänsten returnerar den lokala Sök vägs pekaren för det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="5b3fc-590">Om det inte finns någon lokal Sök vägs uppsättning returneras ett NULL-värde till anroparen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-591">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-591">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-592">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-593">**return_path_name**: pekar mot mål Strängs pekaren för den lokala Sök vägs strängen som ska lagras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-594">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-594">Return Values</span></span>

- <span data-ttu-id="5b3fc-595">**FX_SUCCESS** (0x00) lokal sökväg Hämta.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="5b3fc-596">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är för närvarande inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="5b3fc-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="5b3fc-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="5b3fc-598">**FX_PTR_ERROR** (0X18) ogiltig medie pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="5b3fc-599">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-599">Allowed From</span></span>

<span data-ttu-id="5b3fc-600">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-601">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-602">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-602">See Also</span></span>

- <span data-ttu-id="5b3fc-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-605">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-606">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-607">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-608">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-611">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-616">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-619">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="5b3fc-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="5b3fc-624">Återställer tidigare lokal sökväg</span><span class="sxs-lookup"><span data-stu-id="5b3fc-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-625">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="5b3fc-626">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-626">Description</span></span>

<span data-ttu-id="5b3fc-627">Den här tjänsten återställer en tidigare angiven lokal sökväg.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-627">This service restores a previously set local path.</span></span> <span data-ttu-id="5b3fc-628">Sök positionen för katalogen som gjorts på den här lokala sökvägen återställs också, vilket gör den här rutinen användbar i rekursiva katalogs ökningar av programmet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-629">*Varje lokal sökväg innehåller en lokal Sök vägs sträng med **FX_MAXIMUM_PATH** i storlek, som är som standard 256 tecken. Den här interna Sök vägs strängen används inte av FileX och tillhandahålls endast för programmets användning. Om **FX_LOCAL_PATH** ska deklareras som en lokal variabel bör användarna vara intakta i stacken som växer genom storleken på den här strukturen. Användarna är välkommen att minska storleken på **FX_MAXIMUM_PATH** och återskapa biblioteks källan för FileX.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-630">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-630">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-631">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-632">**local_path_ptr**: pekar mot den tidigare angivna lokala sökvägen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="5b3fc-633">Det är mycket viktigt att se till att den här pekaren faktiskt pekar på en lokal sökväg som används tidigare och fortfarande är intakt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-634">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-634">Return Values</span></span>

- <span data-ttu-id="5b3fc-635">**FX_SUCCESS** (0x00) återställning av lokal sökväg har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="5b3fc-636">**FX_MEDIA_NOT_OPEN** (0X11) angivet medium är inte öppet för tillfället.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="5b3fc-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH definieras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="5b3fc-638">**FX_PTR_ERROR** (0X18) ogiltig media-eller lokal Sök vägs pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-639">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-639">Allowed From</span></span>

<span data-ttu-id="5b3fc-640">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-641">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-642">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-642">See Also</span></span>

- <span data-ttu-id="5b3fc-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-645">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-646">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-647">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-648">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-651">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-656">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-659">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="5b3fc-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="5b3fc-664">Konfigurerar en tråd bestämd lokal sökväg</span><span class="sxs-lookup"><span data-stu-id="5b3fc-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-665">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-666">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-666">Description</span></span>

<span data-ttu-id="5b3fc-667">Den här tjänsten konfigurerar en tråd specifik sökväg som anges av \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="5b3fc-668">När den här rutinen har slutförts har den lokala Sök vägs informationen som lagras i _ *_local_path_ptr_*\* företräde framför den globala medie Sök vägen för alla fil-och katalog åtgärder som utförs av den här tråden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="5b3fc-669">Detta kommer inte att påverka någon annan tråd i systemet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="5b3fc-670">*Standard storleken för den lokala Sök vägs strängen är 256 tecken. Du kan ändra det genom att ändra **FX_MAXIMUM_PATH** i **fx_api. h** och återskapa hela FileX-biblioteket. Tecken Strängs Sök vägen upprätthålls för programmet och används inte internt av FileX.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-671">*För namn som anges av programmet stöder FileX både omvänt snedstreck ( \\ ) och snedstreck (/) för att skilja kataloger, under kataloger och fil namn. FileX använder dock bara det omvända snedstrecket i sökvägar som returneras till programmet.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-672">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-672">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-673">**media_ptr**: pekar mot det tidigare öppnade mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="5b3fc-674">**local_path_ptr**: målet för att hålla den trådbaserade lokala Sök vägs informationen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="5b3fc-675">Adressen till den här strukturen kan anges i funktionen för återställning av lokal sökväg i framtiden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="5b3fc-676">**new_path_name**: anger den lokala sökvägen till installations programmet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-677">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-677">Return Values</span></span>

- <span data-ttu-id="5b3fc-678">**FX_SUCCESS** (0x00) standard katalog uppsättningen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="5b3fc-679">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-680">**FX_NOT_IMPLEMENTED** (0x22) \* \* FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="5b3fc-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="5b3fc-681">Det gick inte att hitta **FX_INVALID_PATH** (0X0D) ny katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="5b3fc-682">**FX_NOT_IMPLEMENTED** (0x22)-\* \* FX_NO_LOCAL_PATH definieras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="5b3fc-683">**FX_PTR_ERROR** (0X18) ogiltig media-eller lokal Sök vägs pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-684">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-684">Allowed From</span></span>

<span data-ttu-id="5b3fc-685">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-686">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-686">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-687">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-687">See Also</span></span>

- <span data-ttu-id="5b3fc-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-690">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-691">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-692">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-693">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-696">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-701">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-704">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="5b3fc-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="5b3fc-709">Hämtar långt namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-710">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-711">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-711">Description</span></span>

<span data-ttu-id="5b3fc-712">Den här tjänsten hämtar det långa namnet (om det finns någon) som är associerad med det angivna korta (8,3-format) namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="5b3fc-713">Det korta namnet kan vara antingen ett fil namn eller ett katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-714">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-714">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-715">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-716">**short_name**: pekare till källans korta namn (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="5b3fc-717">**long_name**: pekar mot mål för långt namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="5b3fc-718">Om det inte finns något långt namn returneras det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="5b3fc-719">Observera att målet för det långa namnet måste vara tillräckligt stort för att rymma FX_MAX_LONG_NAME_LEN tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-720">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-720">Return Values</span></span>

- <span data-ttu-id="5b3fc-721">**FX_SUCCESS** (0X00) slutfört långt namn get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="5b3fc-722">Det gick inte att hitta **FX_NOT_FOUND** (0X04) kort namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="5b3fc-723">**FX_IO_ERROR** (0X90) driv rutin I/O-fel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="5b3fc-724">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium</span><span class="sxs-lookup"><span data-stu-id="5b3fc-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="5b3fc-725">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-726">**FX_SECTOR_INVALID** (0X89) ogiltig sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="5b3fc-727">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="5b3fc-728">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-729">**FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare</span><span class="sxs-lookup"><span data-stu-id="5b3fc-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="5b3fc-730">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd</span><span class="sxs-lookup"><span data-stu-id="5b3fc-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-731">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-731">Allowed From</span></span>

<span data-ttu-id="5b3fc-732">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-733">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-734">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-734">See Also</span></span>

- <span data-ttu-id="5b3fc-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-737">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-738">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-739">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-740">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-743">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-748">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-751">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="5b3fc-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="5b3fc-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="5b3fc-756">Hämtar långt namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-757">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="5b3fc-758">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-758">Description</span></span>

<span data-ttu-id="5b3fc-759">Den här tjänsten hämtar det långa namnet (om det finns någon) som är associerad med det angivna korta (8,3-format) namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="5b3fc-760">Det korta namnet kan vara antingen ett fil namn eller ett katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-761">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-761">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-762">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-763">**short_name**: pekare till källans korta namn (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="5b3fc-764">**long_name**: pekar mot mål för långt namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="5b3fc-765">Om det inte finns något långt namn returneras det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="5b3fc-766">Obs: målet för det långa namnet måste vara tillräckligt stort för att rymma **FX_MAX_LONG_NAME_LEN** tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="5b3fc-767">**long_file_name_buffer_length**: längden på den långa namn bufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-768">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-768">Return Values</span></span>

- <span data-ttu-id="5b3fc-769">**FX_SUCCESS** (0X00) lyckat långt namn Hämta.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="5b3fc-770">Det gick inte att hitta **FX_NOT_FOUND** (0X04) kort namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="5b3fc-771">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-772">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-773">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-774">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-775">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-776">**FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="5b3fc-777">**FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="5b3fc-778">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-779">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-779">Allowed From</span></span>

<span data-ttu-id="5b3fc-780">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-781">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-782">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-782">See Also</span></span>

- <span data-ttu-id="5b3fc-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-785">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-786">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-787">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-788">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-791">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-799">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="5b3fc-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-803">fx_directory_name_test</span></span>

<span data-ttu-id="5b3fc-804">Test för katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-805">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-806">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-806">Description</span></span>

<span data-ttu-id="5b3fc-807">Den här tjänsten testar om det angivna namnet är en katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="5b3fc-808">I så fall returneras en FX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-809">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-809">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-810">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-811">**directory_name**: pekar på katalog postens namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-812">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-812">Return Values</span></span>

- <span data-ttu-id="5b3fc-813">Det angivna namnet för **FX_SUCCESS** (0x00) är en katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="5b3fc-814">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="5b3fc-815">Det gick inte att hitta **FX_NOT_FOUND** (0X04) katalog posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="5b3fc-816">**FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="5b3fc-817">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-818">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-819">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-820">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-821">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-822">**FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="5b3fc-823">**FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="5b3fc-824">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-825">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-825">Allowed From</span></span>

<span data-ttu-id="5b3fc-826">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-827">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-828">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-828">See Also</span></span>

- <span data-ttu-id="5b3fc-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-831">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-832">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-833">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-834">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-837">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-845">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="5b3fc-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="5b3fc-849">Hämtar nästa katalog post</span><span class="sxs-lookup"><span data-stu-id="5b3fc-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-850">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-851">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-851">Description</span></span>

<span data-ttu-id="5b3fc-852">Den här tjänsten returnerar nästa postnamn i den aktuella standard katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-853">*Om du använder en icke-lokal sökväg är det också viktigt att förhindra (med en ThreadX semafor eller tråd prioritets nivå) andra program trådar från att ändra den här katalogen medan en katalog traversr äger rum. Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-854">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-854">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-855">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-856">**return_entry_name**: pekare till målet för nästa postnamn i standard katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="5b3fc-857">Den buffert som pekaren pekar på måste vara tillräckligt stor för att rymma den maximala storleken på FileX namn, som definieras av **_FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-858">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-858">Return Values</span></span>

- <span data-ttu-id="5b3fc-859">**FX_SUCCESS** (0x00) Nästa post hitta</span><span class="sxs-lookup"><span data-stu-id="5b3fc-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="5b3fc-860">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-861">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="5b3fc-862">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-863">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-864">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-865">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-866">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-867">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-868">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-869">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-869">Allowed From</span></span>

<span data-ttu-id="5b3fc-870">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-871">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-872">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-872">See Also</span></span>

- <span data-ttu-id="5b3fc-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-875">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-876">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-877">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-878">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-881">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-887">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-889">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="5b3fc-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="5b3fc-894">Hämtar nästa katalog post med fullständig information</span><span class="sxs-lookup"><span data-stu-id="5b3fc-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-895">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-895">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="5b3fc-896">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-896">Description</span></span>

<span data-ttu-id="5b3fc-897">Den här tjänsten hämtar nästa postnamn i standard katalogen och kopierar den till det angivna målet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="5b3fc-898">Den returnerar också fullständig information om posten som anges av de ytterligare indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-899">\* Det angivna målet måste vara tillräckligt stort för att rymma det maximala storleks FileX namnet, som definieras av \* \* \* FX_MAX_LONG_NAME_LEN \* \* \* \*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-900">*Om du använder en icke-lokal sökväg är det viktigt att förhindra (med en ThreadX semafor, mutex eller prioritets nivå ändring) andra program trådar från att ändra katalogen medan en katalogs traversr äger rum. Annars kan ogiltiga resultat erhållas.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-901">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-901">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-902">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-903">**directory_name**: pekar mot målet som namn på en katalog post.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="5b3fc-904">Måste vara minst lika stor som **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="5b3fc-905">**attribut**: om det inte är null pekar pekaren på målet för postens attribut att placeras. Attributen returneras i formatet bit-Map med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="5b3fc-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="5b3fc-907">**FX_HIDDEN** (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="5b3fc-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="5b3fc-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="5b3fc-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="5b3fc-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="5b3fc-912">**storlek**: om den inte är null pekar markören mot målet för postens storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="5b3fc-913">**månad**: om det inte är null pekar pekaren på målet för postens månads ändring.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="5b3fc-914">**år**: om det inte är null pekar pekaren på målet för postens ändrings år.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="5b3fc-915">**dag**: om den inte är null pekar du på målet för postens dag.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="5b3fc-916">**timme**: om det inte är null pekar pekaren på målet för postens ändrings tid.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="5b3fc-917">**Minute**: om den inte är null pekar du på målet för postens minuters ändring.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="5b3fc-918">**sekund**: om det inte är null pekar pekaren på målet för postens andra ändring.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-919">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-919">Return Values</span></span>

- <span data-ttu-id="5b3fc-920">**FX_SUCCESS** (0X00) lyckad katalog nästa post hitta.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="5b3fc-921">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-922">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="5b3fc-923">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-924">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-925">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-926">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-927">**FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="5b3fc-928">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-929">**FX_PTR_ERROR** (0X18) ogiltig Media pekare eller också är alla indataparametrar null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="5b3fc-930">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-931">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-931">Allowed From</span></span>

<span data-ttu-id="5b3fc-932">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-933">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-933">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-934">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-934">See Also</span></span>

- <span data-ttu-id="5b3fc-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-937">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-938">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-939">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-940">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-943">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-949">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-951">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="5b3fc-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-955">fx_directory_rename</span></span>

<span data-ttu-id="5b3fc-956">Byter namn på katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-957">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-958">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-958">Description</span></span>

<span data-ttu-id="5b3fc-959">Den här tjänsten ändrar katalog namnet till det angivna nya katalog namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="5b3fc-960">Namnbytet görs också i förhållande till den angivna sökvägen eller standard Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="5b3fc-961">Om en sökväg anges i det nya katalog namnet flyttas den nya katalogen faktiskt till den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="5b3fc-962">Om ingen sökväg anges placeras den omdöpta katalogen i den aktuella standard Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-963">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-963">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-964">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-965">**old_directory_name**: pekar på aktuellt katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="5b3fc-966">**new_directory_name**: pekar mot nytt katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-967">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-967">Return Values</span></span>

- <span data-ttu-id="5b3fc-968">**FX_SUCCESS** (0x00) katalog namns byte lyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="5b3fc-969">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-970">Det gick inte att hitta **FX_NOT_FOUND** (0X04) katalog posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="5b3fc-971">**FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="5b3fc-972">**FX_INVALID_NAME** (0X0C) nytt katalog namn är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="5b3fc-973">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-974">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-975">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-976">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-977">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-978">**FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="5b3fc-979">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-980">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="5b3fc-981">**FX_INVALID_PATH** (0X0D) ogiltig sökväg angavs med katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="5b3fc-982">**FX_ALREADY_CREATED** (0x0B) den angivna katalogen har redan skapats.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="5b3fc-983">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-984">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-985">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-985">Allowed From</span></span>

<span data-ttu-id="5b3fc-986">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-987">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-988">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-988">See Also</span></span>

- <span data-ttu-id="5b3fc-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-991">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-992">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-993">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-994">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-997">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="5b3fc-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="5b3fc-1010">Hämtar kort namn från ett långt namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1011">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-1012">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1012">Description</span></span>

<span data-ttu-id="5b3fc-1013">Den här tjänsten hämtar det korta (8,3-format) namn som är associerat med det angivna långa namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="5b3fc-1014">Det långa namnet kan vara antingen ett fil namn eller ett katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1015">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1015">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1016">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-1017">**long_name**: pekar mot källans långa namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="5b3fc-1018">**short_name**: pekare till målets kort namn (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="5b3fc-1019">Observera att målet för det korta namnet måste vara tillräckligt stort för att rymma 14 tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1020">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1020">Return Values</span></span>

- <span data-ttu-id="5b3fc-1021">**FX_SUCCESS** (0x00) kort namn hämtades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="5b3fc-1022">Det gick inte att hitta **FX_NOT_FOUND** (0X04) långt namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="5b3fc-1023">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1024">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1025">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1026">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1027">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1028">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1029">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-1030">**FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="5b3fc-1031">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1032">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1032">Allowed From</span></span>

<span data-ttu-id="5b3fc-1033">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1034">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1035">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1035">See Also</span></span>

- <span data-ttu-id="5b3fc-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1038">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1041">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1053">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="5b3fc-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="5b3fc-1057">Hämtar kort namn från ett långt namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1058">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="5b3fc-1059">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1059">Description</span></span>

<span data-ttu-id="5b3fc-1060">Den här tjänsten hämtar det korta (8,3-format) namn som är associerat med det angivna långa namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="5b3fc-1061">Det långa namnet kan vara antingen ett fil namn eller ett katalog namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1062">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1062">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1063">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-1064">**long_name**: pekar mot källans långa namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="5b3fc-1065">**short_name**: pekare till målets kort namn (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="5b3fc-1066">Obs: målet för det korta namnet måste vara tillräckligt stort för att rymma 14 tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="5b3fc-1067">**short_file_name_length**: längden på den korta bufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1068">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1068">Return Values</span></span>

- <span data-ttu-id="5b3fc-1069">**FX_SUCCESS** (0x00) kort namn hämtades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="5b3fc-1070">Det gick inte att hitta **FX_NOT_FOUND** (0X04) långt namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="5b3fc-1071">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1072">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1073">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1074">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1075">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1076">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1077">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-1078">**FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="5b3fc-1079">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1080">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1080">Allowed From</span></span>

<span data-ttu-id="5b3fc-1081">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1082">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1083">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1083">See Also</span></span>

- <span data-ttu-id="5b3fc-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1086">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1089">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1101">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="5b3fc-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="5b3fc-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="5b3fc-1105">Aktiverar tjänsten fel tolerans</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1106">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="5b3fc-1107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1107">Description</span></span>

<span data-ttu-id="5b3fc-1108">Den här tjänsten aktiverar den feltoleranta modulen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="5b3fc-1109">Vid start identifierar den feltoleranta modulen om fil systemet är under FileX feltolerant skydd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="5b3fc-1110">Om den inte är det hittar tjänsten tillgängliga sektorer i fil systemet för att lagra loggar i fil system transaktioner.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="5b3fc-1111">Om fil systemet är under FileX feltolerant skydd tillämpas loggarna på fil systemet för att upprätthålla dess integritet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1112">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1112">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1113">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-1114">**memory_ptr**: pekar på ett minnes block som används av feltolerant modul som virtuellt minne.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="5b3fc-1115">**memory_size**: minnets storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="5b3fc-1116">För att feltolerant ska fungera korrekt, måste storleken på virtuellt minne vara minst 3072 byte, och måste vara flera av sektor storleken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1117">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1117">Return Values</span></span>

- <span data-ttu-id="5b3fc-1118">**FX_SUCCESS** (0X00) har aktiverat fel tolerans.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="5b3fc-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) minnes storleken är för liten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="5b3fc-1120">Start sektor fel **FX_BOOT_ERROR** (0x01).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="5b3fc-1121">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1122">**FX_NO_MORE_ENTRIES** (0x0F) det finns inget ledigt kluster tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="5b3fc-1123">**FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="5b3fc-1124">**FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="5b3fc-1125">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1126">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-1127">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1128">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1128">Allowed From</span></span>

<span data-ttu-id="5b3fc-1129">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1130">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1131">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1131">See Also</span></span>

- <span data-ttu-id="5b3fc-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1132">fx_system_initialize</span></span>
- <span data-ttu-id="5b3fc-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1133">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1135">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1136">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1140">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1141">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1142">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1144">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1145">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="5b3fc-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1149">fx_file_allocate</span></span>

<span data-ttu-id="5b3fc-1150">Allokerar utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1151">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1152">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1152">Description</span></span>

<span data-ttu-id="5b3fc-1153">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="5b3fc-1154">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="5b3fc-1155">Resultatet avrundas sedan uppåt till nästa hela kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="5b3fc-1156">För att allokera utrymme utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1157">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1157">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1158">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-1159">**storlek**: antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1160">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1160">Return Values</span></span>

- <span data-ttu-id="5b3fc-1161">**FX_SUCCESS** (0X00) slutförde filallokering.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="5b3fc-1162">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-1163">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1164">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1165">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-1166">**FX_NO_MORE_ENTRIES** (0x0F) det finns inget ledigt kluster tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="5b3fc-1167">**FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="5b3fc-1168">**FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="5b3fc-1169">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1170">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1171">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-1172">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1173">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1173">Allowed From</span></span>

<span data-ttu-id="5b3fc-1174">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1175">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1176">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1176">See Also</span></span>

- <span data-ttu-id="5b3fc-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1180">fx_file_close-fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1182">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1189">fx_file_open-fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1191">fx_file_rename-fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1192">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1194">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="5b3fc-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="5b3fc-1201">Läser filattribut</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1202">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1203">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1203">Description</span></span>

<span data-ttu-id="5b3fc-1204">Den här tjänsten läser filens attribut från det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1205">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1205">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1206">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-1207">**file_name**: pekar mot namnet på den begärda filen (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="5b3fc-1208">**attributes_ptr**: pekar mot målet för filens attribut som ska placeras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="5b3fc-1209">Filattributen returneras i ett bit kart format med följande möjliga inställningar:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="5b3fc-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="5b3fc-1211">FX_HIDDEN (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="5b3fc-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="5b3fc-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="5b3fc-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="5b3fc-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1216">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1216">Return Values</span></span>

- <span data-ttu-id="5b3fc-1217">Det lästa attributet för **FX_SUCCESS** (0x00) har lästs.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="5b3fc-1218">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-1219">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen i mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="5b3fc-1220">**FX_NOT_A_FILE** (0x05) den angivna filen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="5b3fc-1221">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1222">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1223">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1224">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1225">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1226">**FX_PTR_ERROR** (0X18) ogiltiga media-eller attribut pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="5b3fc-1227">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1228">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1228">Allowed From</span></span>

<span data-ttu-id="5b3fc-1229">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1230">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1231">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1231">See Also</span></span>

- <span data-ttu-id="5b3fc-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1232">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1235">fx_file_close-fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1237">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1244">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1245">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1247">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1248">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1249">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1251">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="5b3fc-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="5b3fc-1258">Ställer in filattribut</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1259">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1260">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1260">Description</span></span>

<span data-ttu-id="5b3fc-1261">Den här tjänsten anger filens attribut till dem som anges av anroparen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-1262">*Programmet får bara ändra en delmängd av filens attribut med den här tjänsten. Alla försök att ange ytterligare attribut leder till ett fel.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1263">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1263">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1264">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-1265">**file_name**: pekar på namnet på den begärda filen \* \* (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="5b3fc-1266">**attribut**: de nya attributen för filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="5b3fc-1267">Giltiga filattribut definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="5b3fc-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="5b3fc-1269">FX_HIDDEN (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="5b3fc-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="5b3fc-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1272">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1272">Return Values</span></span>

- <span data-ttu-id="5b3fc-1273">Den angivna attributet för **FX_SUCCESS** (0x00) har angetts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="5b3fc-1274">**FX_ACCESS_ERROR** -filen (0x06) är öppen och kan inte ha attributen inställd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="5b3fc-1275">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1276">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1277">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-1278">**FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i tabellen fat-eller exFAT-kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="5b3fc-1279">**FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="5b3fc-1280">**FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen i mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="5b3fc-1281">**FX_NOT_A_FILE** (0x05) den angivna filen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="5b3fc-1282">**FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="5b3fc-1283">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1284">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1285">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-1286">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-1287">**FX_INVALID_ATTR** (0X19) ogiltiga attribut har marker ATS.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="5b3fc-1288">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1289">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1289">Allowed From</span></span>

<span data-ttu-id="5b3fc-1290">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1291">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1292">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1292">See Also</span></span>

- <span data-ttu-id="5b3fc-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1293">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1296">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1297">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1299">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1306">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1307">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1309">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1310">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1311">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1313">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="5b3fc-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="5b3fc-1320">Bästa förmåga att allokera utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1321">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1322">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1322">Description</span></span>

<span data-ttu-id="5b3fc-1323">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="5b3fc-1324">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="5b3fc-1325">Resultatet avrundas sedan uppåt till nästa hela kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="5b3fc-1326">Om det inte finns tillräckligt många kluster som finns i följd i mediet länkar den här tjänsten det största tillgängliga blocket av flera kluster i följd till filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="5b3fc-1327">Mängden utrymme som faktiskt allokeras till filen returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="5b3fc-1328">För att allokera utrymme utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1329">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1329">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1330">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-1331">**storlek**: antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1332">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1332">Return Values</span></span>

- <span data-ttu-id="5b3fc-1333">**FX_SUCCESS** (0x00) bästa filallokering för bästa ansträngning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="5b3fc-1334">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-1335">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-1336">**FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="5b3fc-1337">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1338">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1339">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1340">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1341">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1342">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1343">**FX_PTR_ERROR** (0X18) ogiltig fil pekare eller mål.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="5b3fc-1344">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1345">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1345">Allowed From</span></span>

<span data-ttu-id="5b3fc-1346">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1347">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1348">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1348">See Also</span></span>

- <span data-ttu-id="5b3fc-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1349">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1352">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1353">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1355">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1362">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1363">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1365">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1366">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1367">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1369">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="5b3fc-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1375">fx_file_close</span></span>

<span data-ttu-id="5b3fc-1376">Stänger filen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1377">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1378">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1378">Description</span></span>

<span data-ttu-id="5b3fc-1379">Den här tjänsten stänger den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1379">This service closes the specified file.</span></span> <span data-ttu-id="5b3fc-1380">Om filen var öppen för skrivning och om den har ändrats, slutför den här tjänsten fil ändrings processen genom att uppdatera katalog posten med den nya storleken och den aktuella system tiden och det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1381">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1381">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1382">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1383">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1383">Return Values</span></span>

- <span data-ttu-id="5b3fc-1384">**FX_SUCCESS** (0x00) fil stängningen är klar.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="5b3fc-1385">**FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="5b3fc-1386">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1387">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1388">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1389">**FX_PTR_ERROR** (0X18) ogiltiga media-eller attribut pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="5b3fc-1390">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1391">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1391">Allowed From</span></span>

<span data-ttu-id="5b3fc-1392">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1393">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1394">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1394">See Also</span></span>

- <span data-ttu-id="5b3fc-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1395">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1399">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1401">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1408">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1409">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1411">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1412">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1413">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1415">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="5b3fc-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1421">fx_file_create</span></span>

<span data-ttu-id="5b3fc-1422">Skapar fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1423">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1424">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1424">Description</span></span>

<span data-ttu-id="5b3fc-1425">Den här tjänsten skapar den angivna filen i standard katalogen eller i den katalog Sök väg som anges med fil namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-1426">*Den här tjänsten skapar en fil med längden noll, dvs. inga kluster allokeras. Allokeringen sker automatiskt vid efterföljande fil skrivningar eller kan göras i förväg med tjänsten fx_file_allocate eller fx_file_extended_allocate utrymme bortom 4 GB).*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1427">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1427">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1428">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-1429">**file_name**: pekar mot namnet på filen som ska skapas (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1430">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1430">Return Values</span></span>

- <span data-ttu-id="5b3fc-1431">**FX_SUCCESS** (0x00) filen har skapats.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="5b3fc-1432">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-1433">**FX_ALREADY_CREATED** (0x0B) den angivna filen har redan skapats.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="5b3fc-1434">**FX_NO_MORE_SPACE** (0x0A) det finns antingen inga fler poster i rot katalogen eller så finns det inga fler kluster tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="5b3fc-1435">**FX_INVALID_PATH** (0X0D) ogiltig sökväg angavs med fil namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="5b3fc-1436">**FX_INVALID_NAME** (0X0C) fil namnet är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="5b3fc-1437">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1438">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1439">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1440">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1441">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1442">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="5b3fc-1443">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1444">**FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1445">**FX_PTR_ERROR** (0X18) ogiltigt medie-eller fil namns pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="5b3fc-1446">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1447">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1447">Allowed From</span></span>

<span data-ttu-id="5b3fc-1448">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1449">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1450">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1450">See Also</span></span>
- <span data-ttu-id="5b3fc-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1451">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1455">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1457">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1464">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1465">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1467">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1468">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1469">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1471">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="5b3fc-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="5b3fc-1478">Anger datum och tid för filen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1478">Sets file date and time</span></span>

<span data-ttu-id="5b3fc-1479">Ange datum och tid för filen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1480">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1480">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="5b3fc-1481">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1481">Description</span></span>

<span data-ttu-id="5b3fc-1482">Den här tjänsten anger datum och tid för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1483">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1483">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1484">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-1485">**file_name**: pekaren till namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="5b3fc-1486">**år**: värdet på året (1980-2107 inklusiv).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="5b3fc-1487">**månad**: värde för månad (1-12 inklusiv).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="5b3fc-1488">**dag**: värde på dag (1-31 inklusiv).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="5b3fc-1489">**timme**: värde för timme (0-23 inklusiv).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="5b3fc-1490">**Minute**: värdet för minut (0-59 inklusiv).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="5b3fc-1491">**sekund**: värdet för sekund (0-59 inklusiv).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1492">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1492">Return Values</span></span>

- <span data-ttu-id="5b3fc-1493">**FX_SUCCESS** (0X00) lyckad datum/tid-uppsättning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="5b3fc-1494">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-1495">Det gick inte att hitta **FX_NOT_FOUND** -filen (0x04).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="5b3fc-1496">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1497">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1498">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1499">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1500">**FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="5b3fc-1501">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1502">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1503">**FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="5b3fc-1504">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="5b3fc-1505">**FX_INVALID_YEAR** 0X12-året är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="5b3fc-1506">**FX_INVALID_MONTH** (0X13) månaden är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="5b3fc-1507">**FX_INVALID_DAY** (0X14) dagen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="5b3fc-1508">**FX_INVALID_HOUR** (0X15) timmen är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="5b3fc-1509">**FX_INVALID_MINUTE** (0X16) minut är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="5b3fc-1510">Den andra **FX_INVALID_SECOND** (0x17) är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1511">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1511">Allowed From</span></span>

<span data-ttu-id="5b3fc-1512">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1513">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1514">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1514">See Also</span></span>

- <span data-ttu-id="5b3fc-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1515">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1519">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1520">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1521">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1528">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1529">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1531">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1532">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1533">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1535">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="5b3fc-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="5b3fc-1542">Tar bort fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1542">Deletes file</span></span>

<span data-ttu-id="5b3fc-1543">Borttagning av fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1544">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1545">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1545">Description</span></span>

<span data-ttu-id="5b3fc-1546">Den här tjänsten tar bort den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1547">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1547">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1548">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-1549">**file_name**: pekar mot namnet på filen som ska tas bort (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1550">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1550">Return Values</span></span>

- <span data-ttu-id="5b3fc-1551">**FX_SUCCESS** (0x00) fil borttagning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="5b3fc-1552">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-1553">Det gick inte att hitta den angivna filen **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="5b3fc-1554">**FX_NOT_A_FILE** (0x05) det angivna fil namnet var en katalog eller volym.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="5b3fc-1555">Den angivna filen för **FX_ACCESS_ERROR** (0x06) är öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="5b3fc-1556">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1557">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1558">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1559">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1560">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1561">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1562">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1563">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-1564">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-1565">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1566">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1566">Allowed From</span></span>

<span data-ttu-id="5b3fc-1567">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1568">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1569">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1569">See Also</span></span>

- <span data-ttu-id="5b3fc-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1570">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1574">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1575">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1583">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1584">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1586">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1587">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1588">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1590">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="5b3fc-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="5b3fc-1597">Allokerar utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1598">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1599">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1599">Description</span></span>

<span data-ttu-id="5b3fc-1600">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="5b3fc-1601">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="5b3fc-1602">Resultatet avrundas sedan uppåt till nästa hela kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="5b3fc-1603">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="5b3fc-1604">*Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen förallokerar utrymme bortom intervallet 4 GB.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1605">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1605">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1606">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-1607">**storlek**: antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1608">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1608">Return Values</span></span>

- <span data-ttu-id="5b3fc-1609">**FX_SUCCESS** (0X00) slutförde filallokering.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="5b3fc-1610">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-1611">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-1612">**FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="5b3fc-1613">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1614">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1615">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1616">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1617">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1618">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1619">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-1620">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1621">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1621">Allowed From</span></span>

<span data-ttu-id="5b3fc-1622">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1623">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1624">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1624">See Also</span></span>

- <span data-ttu-id="5b3fc-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1625">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1629">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1630">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1632">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1638">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1639">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1641">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1642">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1643">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1645">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="5b3fc-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="5b3fc-1652">Bästa förmåga att allokera utrymme för en fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1653">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1654">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1654">Description</span></span>

<span data-ttu-id="5b3fc-1655">Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="5b3fc-1656">FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="5b3fc-1657">Resultatet avrundas sedan uppåt till nästa hela kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="5b3fc-1658">Om det inte finns tillräckligt många kluster som finns i följd i mediet länkar den här tjänsten det största tillgängliga blocket av flera kluster i följd till filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="5b3fc-1659">Mängden utrymme som faktiskt allokeras till filen returneras till anroparen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="5b3fc-1660">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="5b3fc-1661">*Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen förallokerar utrymme bortom intervallet 4 GB.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1662">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1662">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1663">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-1664">**storlek**: antal byte som ska allokeras för filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1665">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1665">Return Values</span></span>

- <span data-ttu-id="5b3fc-1666">**FX_SUCCESS** (0X00) slutförde filallokering.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="5b3fc-1667">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-1668">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-1669">**FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="5b3fc-1670">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1671">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1672">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1673">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1674">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1675">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1676">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-1677">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1678">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1678">Allowed From</span></span>

<span data-ttu-id="5b3fc-1679">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1680">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1680">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-1681">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1681">See Also</span></span>

- <span data-ttu-id="5b3fc-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1682">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1686">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1687">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1689">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1695">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1696">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1698">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1699">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1700">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1702">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="5b3fc-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="5b3fc-1709">Positioner till en relativ byte förskjutning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1710">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1711">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1711">Description</span></span>

<span data-ttu-id="5b3fc-1712">Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven relativ byte förskjutning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="5b3fc-1713">Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="5b3fc-1714">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="5b3fc-1715">Parametern *byte_offset* tar ett 64-bitars värde, vilket gör att anroparen kan placera Läs-och skriv Visa-pekaren utanför 4 GB-intervall.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-1716">*Om Sök åtgärden försöker söka efter slutet av filen placeras filens Läs-och skriv pekare i slutet av filen. Om Sök åtgärden försöker placera förbi början av filen placeras filens Läs-och skriv visare i början av filen.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1717">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1717">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1718">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-1719">**byte_offset**: önskad relativ byte förskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="5b3fc-1720">**seek_from**: riktningen och platsen där den relativa sökningen ska utföras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="5b3fc-1721">Giltiga alternativ för sökning definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="5b3fc-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="5b3fc-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="5b3fc-1724">FX_SEEK_FORWARD (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="5b3fc-1725">FX_SEEK_BACK (0x03) om FX_SEEK_BEGIN anges utförs Sök åtgärden från början av filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="5b3fc-1726">Om FX_SEEK_END har angetts utförs Sök åtgärden bakåt från slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="5b3fc-1727">Om FX_SEEK_FORWARD har angetts utförs söknings åtgärden framåt från den aktuella fil positionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="5b3fc-1728">Om FX_SEEK_BACK har angetts utförs Sök åtgärden baklänges från den aktuella fil positionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1729">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1729">Return Values</span></span>

- <span data-ttu-id="5b3fc-1730">**FX_SUCCESS** (0x00) fil relativ sökning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="5b3fc-1731">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-1732">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1733">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1734">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1735">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1736">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-1737">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1738">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1738">Allowed From</span></span>

<span data-ttu-id="5b3fc-1739">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1740">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1741">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1741">See Also</span></span>

- <span data-ttu-id="5b3fc-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1742">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1746">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1747">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1749">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1755">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1756">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1758">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1759">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1760">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1762">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="5b3fc-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="5b3fc-1769">Positioner till byte-förskjutning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1770">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1771">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1771">Description</span></span>

<span data-ttu-id="5b3fc-1772">Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven byte förskjutning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="5b3fc-1773">Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="5b3fc-1774">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="5b3fc-1775">Parametern *byte_offset* tar ett 64-bitars värde, vilket gör att anroparen kan placera Läs-och skriv Visa-pekaren utanför 4 GB-intervall.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1776">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1776">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1777">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-1778">**byte_offset**: önskad byte förskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="5b3fc-1779">Värdet noll placerar Läs-och skriv pekaren i början av filen, medan ett värde som är större än filens storlek kommer att placera Läs-och skriv pekaren i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1780">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1780">Return Values</span></span>

- <span data-ttu-id="5b3fc-1781">**FX_SUCCESS** (0x00) Sök efter filer.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="5b3fc-1782">**FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="5b3fc-1783">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1784">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1785">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1786">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1787">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-1788">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1789">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1789">Allowed From</span></span>

<span data-ttu-id="5b3fc-1790">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1791">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1792">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1792">See Also</span></span>

- <span data-ttu-id="5b3fc-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1793">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1797">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1798">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1800">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1806">fx_file_open-fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1808">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1809">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1810">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1812">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="5b3fc-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="5b3fc-1819">Trunkerar fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1820">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1821">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1821">Description</span></span>

<span data-ttu-id="5b3fc-1822">Den här tjänsten trunkerar filens storlek till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="5b3fc-1823">Om den angivna storleken är större än den faktiska fil storleken gör inte den här tjänsten något.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="5b3fc-1824">Inget av de medie kluster som är associerade med filen har släppts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-1825">*Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="5b3fc-1826">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="5b3fc-1827">*Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen kan använda fler än 4 GB.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1828">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1828">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1829">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-1830">**storlek**: ny fil storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1830">**size**: New file size.</span></span> <span data-ttu-id="5b3fc-1831">Gamla byte den nya fil storleken ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1832">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1832">Return Values</span></span>

- <span data-ttu-id="5b3fc-1833">**FX_SUCCESS** (0x00) filen trunkerades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="5b3fc-1834">**FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="5b3fc-1835">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-1836">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1837">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1838">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1839">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1840">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1841">**FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1842">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-1843">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1844">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1844">Allowed From</span></span>

<span data-ttu-id="5b3fc-1845">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1846">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1847">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1847">See Also</span></span>

- <span data-ttu-id="5b3fc-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1848">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1852">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1853">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1855">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1861">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1862">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1864">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1865">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1866">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1868">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="5b3fc-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="5b3fc-1875">Trunkerar filen och släpper kluster (er)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1876">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="5b3fc-1877">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1877">Description</span></span>

<span data-ttu-id="5b3fc-1878">Den här tjänsten trunkerar filens storlek till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="5b3fc-1879">Om den angivna storleken är större än den faktiska fil storleken gör inte tjänsten något.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="5b3fc-1880">Till skillnad från den ***fx_file_extended_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-1881">*Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="5b3fc-1882">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="5b3fc-1883">*Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen kan använda fler än 4 GB.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1884">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1884">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1885">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-1886">**storlek**: ny fil storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1886">**size**: New file size.</span></span> <span data-ttu-id="5b3fc-1887">Gamla byte den nya fil storleken ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1888">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1888">Return Values</span></span>

- <span data-ttu-id="5b3fc-1889">**FX_SUCCESS** (0x00) filen trunkerades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="5b3fc-1890">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-1891">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-1892">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1893">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-1894">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1895">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-1896">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1897">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1898">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1899">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-1900">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1901">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1901">Allowed From</span></span>

<span data-ttu-id="5b3fc-1902">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1903">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1904">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1904">See Also</span></span>

- <span data-ttu-id="5b3fc-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1905">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1909">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1910">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1912">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1918">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1919">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1921">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1922">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1923">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1925">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="5b3fc-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1931">fx_file_open</span></span>

<span data-ttu-id="5b3fc-1932">Öppnar fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1933">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1934">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1934">Description</span></span>

<span data-ttu-id="5b3fc-1935">Den här tjänsten öppnar den angivna filen för antingen läsning eller skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="5b3fc-1936">En fil kan öppnas för läsning flera gånger, medan en fil bara kan öppnas för skrivning en gång tills skrivaren stänger filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-1937">*Var försiktig om en fil öppnas samtidigt för läsning och skrivning. Fil skrivning som utförs när en fil öppnas samtidigt för läsning kanske inte visas av läsaren, om inte läsaren stänger och öppnar filen för läsning. På samma sätt bör filen Writer vara försiktig när du använder filtrunkering av tjänster. Om en fil trunkeras av skrivaren kan läsare av samma fil returnera ogiltiga data.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-1938">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1938">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-1939">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-1940">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-1941">**file_name**: pekar mot namnet på filen som ska öppnas (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="5b3fc-1942">**open_type**: typ av fil öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="5b3fc-1943">Giltiga alternativ för öppen typ är:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="5b3fc-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="5b3fc-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="5b3fc-1946">FX_OPEN_FOR_READ_FAST (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="5b3fc-1947">Att öppna filer med FX_OPEN_FOR_READ och FX_OPEN_FOR_READ_FAST liknar följande:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="5b3fc-1948">FX_OPEN_FOR_READ innehåller en verifiering av att den länkade listan över kluster som utgör filen är intakt och FX_OPEN_FOR_READ_FAST inte utför den här verifieringen, vilket gör det snabbare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-1949">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1949">Return Values</span></span>

- <span data-ttu-id="5b3fc-1950">**FX_SUCCESS** (0x00) filen är öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="5b3fc-1951">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-1952">Det gick inte att hitta den angivna filen **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="5b3fc-1953">**FX_NOT_A_FILE** (0x05) det angivna fil namnet var en katalog eller volym.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="5b3fc-1954">**FX_FILE_CORRUPT** (0x08) den angivna filen är skadad och det gick inte att öppna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="5b3fc-1955">**FX_ACCESS_ERROR** (0x06) den angivna filen är redan öppen eller öppen typ är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="5b3fc-1956">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-1957">**FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="5b3fc-1958">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-1959">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-1960">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-1961">**FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="5b3fc-1962">**FX_PTR_ERROR** (0X18) ogiltig media-eller fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="5b3fc-1963">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-1964">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1964">Allowed From</span></span>

<span data-ttu-id="5b3fc-1965">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-1966">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-1967">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1967">See Also</span></span>

- <span data-ttu-id="5b3fc-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1968">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1972">fx_file_close-fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="5b3fc-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1974">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1981">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1983">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1984">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1985">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1987">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="5b3fc-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1993">fx_file_read</span></span>

<span data-ttu-id="5b3fc-1994">Läser byte från fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-1995">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="5b3fc-1996">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1996">Description</span></span>

<span data-ttu-id="5b3fc-1997">Tjänsten läser byte från filen och lagrar dem i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="5b3fc-1998">När läsningen är klar är filens interna Läs pekare justerad så att den pekar på nästa byte i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="5b3fc-1999">Om det finns färre byte kvar i begäran lagras bara återstående byte i bufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="5b3fc-2000">I alla fall returneras det totala antalet byte som placeras i bufferten till anroparen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2001">*Programmet måste se till att den angivna bufferten kan lagra det angivna antalet begärda byte.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2002">*Snabbare prestanda uppnås om målcachen är på ett långt ord och den begärda storleken är jämnt delbar med sizeof (**ulong**).*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2003">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2003">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2004">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-2005">**buffer_ptr**: pekar mot målcachen för läsning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="5b3fc-2006">**request_size**: högsta antal byte som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="5b3fc-2007">**actual_size**: pekar mot variabeln som innehåller det faktiska antalet byte som läses in i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2008">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2008">Return Values</span></span>

- <span data-ttu-id="5b3fc-2009">**FX_SUCCESS** (0x00) filen har lästs.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="5b3fc-2010">**FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="5b3fc-2011">**FX_FILE_CORRUPT** (0x08) den angivna filen är skadad och läsningen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="5b3fc-2012">**FX_END_OF_FILE** (0X09) slutet av filen har nåtts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="5b3fc-2013">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2014">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-2015">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2016">**FX_PTR_ERROR** (0X18) ogiltig fil-eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="5b3fc-2017">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2018">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2018">Allowed From</span></span>

<span data-ttu-id="5b3fc-2019">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2020">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2020">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="5b3fc-2021">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2021">See Also</span></span>

- <span data-ttu-id="5b3fc-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="5b3fc-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="5b3fc-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="5b3fc-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="5b3fc-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2026">fx_file_close,</span></span>
- <span data-ttu-id="5b3fc-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2027">fx_file_create,</span></span>
- <span data-ttu-id="5b3fc-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="5b3fc-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2029">fx_file_delete,</span></span>
- <span data-ttu-id="5b3fc-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="5b3fc-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="5b3fc-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="5b3fc-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="5b3fc-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="5b3fc-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="5b3fc-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2036">fx_file_open,</span></span>
- <span data-ttu-id="5b3fc-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="5b3fc-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2038">fx_file_rename,</span></span>
- <span data-ttu-id="5b3fc-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2039">fx_file_seek,</span></span>
- <span data-ttu-id="5b3fc-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="5b3fc-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="5b3fc-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2042">fx_file_write,</span></span>
- <span data-ttu-id="5b3fc-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="5b3fc-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="5b3fc-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="5b3fc-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="5b3fc-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="5b3fc-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="5b3fc-2049">Positioner till en relativ byte förskjutning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2050">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2051">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2051">Description</span></span>

<span data-ttu-id="5b3fc-2052">Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven relativ byte förskjutning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="5b3fc-2053">Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-2054">*Om Sök åtgärden försöker söka efter slutet av filen placeras filens Läs-och skriv pekare i slutet av filen. Om Sök åtgärden försöker placera förbi början av filen placeras filens Läs-och skriv visare i början av filen.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="5b3fc-2055">För att kunna söka med ett förskjutnings värde utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2056">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2056">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2057">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-2058">**byte_offset**: önskad relativ byte förskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="5b3fc-2059">**seek_from**: riktningen och platsen där den relativa sökningen ska utföras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="5b3fc-2060">Giltiga alternativ för sökning definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="5b3fc-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="5b3fc-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="5b3fc-2063">FX_SEEK_FORWARD (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="5b3fc-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="5b3fc-2065">Om FX_SEEK_BEGIN anges utförs Sök åtgärden från början av filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="5b3fc-2066">Om FX_SEEK_END har angetts utförs Sök åtgärden bakåt från slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="5b3fc-2067">Om FX_SEEK_FORWARD har angetts utförs söknings åtgärden framåt från den aktuella fil positionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="5b3fc-2068">Om FX_SEEK_BACK har angetts utförs Sök åtgärden baklänges från den aktuella fil positionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2069">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2069">Return Values</span></span>

- <span data-ttu-id="5b3fc-2070">**FX_SUCCESS** (0x00) fil relativ sökning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="5b3fc-2071">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-2072">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2073">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2074">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2075">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-2076">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-2077">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2078">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2078">Allowed From</span></span>

<span data-ttu-id="5b3fc-2079">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2080">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2081">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2081">See Also</span></span>

- <span data-ttu-id="5b3fc-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2082">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2086">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2087">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2089">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2096">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2097">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2098">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2099">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2100">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2102">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="5b3fc-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2108">fx_file_rename</span></span>

<span data-ttu-id="5b3fc-2109">Byter namn på filen</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2110">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2111">Description</span></span>

<span data-ttu-id="5b3fc-2112">Den här tjänsten ändrar namnet på filen som anges av *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="5b3fc-2113">Namnbytet görs också i förhållande till den angivna sökvägen eller standard Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="5b3fc-2114">Om en sökväg anges i det nya fil namnet flyttas filen med namnet som bytt namn till den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="5b3fc-2115">Om ingen sökväg anges placeras den omdöpta filen i den aktuella standard Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2116">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2116">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2117">**media_ptr**: pekar mot ett medie kontroll block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="5b3fc-2118">**old_file_name**: pekar mot namnet på filen som ska byta namn (katalog Sök väg är valfritt).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="5b3fc-2119">**new_file_name**: pekar mot det nya fil namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="5b3fc-2120">Katalog Sök vägen är inte tillåten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2121">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2121">Return Values</span></span>

- <span data-ttu-id="5b3fc-2122">**FX_SUCCESS** (0x00) filen har bytt namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="5b3fc-2123">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2124">Det gick inte att hitta den angivna filen **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="5b3fc-2125">**FX_NOT_A_FILE** (0x05) den angivna filen är en katalog.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="5b3fc-2126">Den angivna filen för **FX_ACCESS_ERROR** (0x06) är redan öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="5b3fc-2127">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2128">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-2129">**FX_INVALID_NAME** (0X0C) angivet nytt fil namn är inte ett giltigt fil namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="5b3fc-2130">Sökvägen till **FX_INVALID_PATH** (0x0D) är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="5b3fc-2131">**FX_ALREADY_CREATED** (0X0B) det nya fil namnet används.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="5b3fc-2132">**FX_MEDIA_INVALID** -mediet (protokollnumret 0x02) är ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="5b3fc-2133">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2134">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2135">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-2136">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-2137">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="5b3fc-2138">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-2139">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2140">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2140">Allowed From</span></span>

<span data-ttu-id="5b3fc-2141">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2142">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2143">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2143">See Also</span></span>

- <span data-ttu-id="5b3fc-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2144">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2148">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2149">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2151">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2158">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2159">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2161">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2162">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2164">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="5b3fc-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2170">fx_file_seek</span></span>

<span data-ttu-id="5b3fc-2171">Positioner till byte-förskjutning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2172">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2173">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2173">Description</span></span>

<span data-ttu-id="5b3fc-2174">Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven byte förskjutning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="5b3fc-2175">Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="5b3fc-2176">För att kunna söka med ett förskjutnings värde utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2177">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2177">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2178">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-2179">**byte_offset**: önskad byte förskjutning i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="5b3fc-2180">Värdet noll placerar Läs-och skriv pekaren i början av filen, medan ett värde som är större än filens storlek kommer att placera Läs-och skriv pekaren i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2181">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2181">Return Values</span></span>

- <span data-ttu-id="5b3fc-2182">**FX_SUCCESS** (0x00) Sök efter filer.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="5b3fc-2183">**FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="5b3fc-2184">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2185">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2186">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2187">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-2188">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-2189">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2190">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2190">Allowed From</span></span>

<span data-ttu-id="5b3fc-2191">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2192">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2193">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2193">See Also</span></span>

- <span data-ttu-id="5b3fc-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2194">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2198">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2199">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2201">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2208">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2209">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2210">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2211">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2212">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2214">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="5b3fc-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2220">fx_file_truncate</span></span>

<span data-ttu-id="5b3fc-2221">Trunkerar fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2222">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="5b3fc-2223">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2223">Description</span></span>

<span data-ttu-id="5b3fc-2224">Den här tjänsten trunkerar filens storlek till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="5b3fc-2225">Om den angivna storleken är större än den faktiska fil storleken gör inte den här tjänsten något.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="5b3fc-2226">Inget av de medie kluster som är associerade med filen har släppts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2227">*Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="5b3fc-2228">För att kunna arbeta mer än 4 GB använder programmet tjänsten *fx_file_extended_truncate*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2229">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2229">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2230">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-2231">**storlek**: ny fil storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2231">**size**: New file size.</span></span> <span data-ttu-id="5b3fc-2232">Gamla byte den nya fil storleken ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2233">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2233">Return Values</span></span>

- <span data-ttu-id="5b3fc-2234">**FX_SUCCESS** (0x00) filen trunkerades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="5b3fc-2235">**FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="5b3fc-2236">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-2237">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2238">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-2239">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2240">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2241">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-2242">**FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="5b3fc-2243">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-2244">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2245">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2245">Allowed From</span></span>

<span data-ttu-id="5b3fc-2246">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2247">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2248">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2248">See Also</span></span>

- <span data-ttu-id="5b3fc-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2249">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2253">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2254">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2256">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2263">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2264">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2266">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2267">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2269">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="5b3fc-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="5b3fc-2276">Trunkerar filen och släpper kluster (er)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2277">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2278">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2278">Description</span></span>

<span data-ttu-id="5b3fc-2279">Den här tjänsten trunkerar filens storlek till den angivna storleken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="5b3fc-2280">Om den angivna storleken är större än den faktiska fil storleken gör inte tjänsten något.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="5b3fc-2281">Till skillnad från den ***fx_file_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2282">*Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="5b3fc-2283">För att kunna arbeta mer än 4 GB använder programmet tjänsten *fx_file_extended_truncate_release*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2284">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2284">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2285">**file_ptr**: pekar mot en tidigare öppnad fil.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="5b3fc-2286">**storlek**: ny fil storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2286">**size**: New file size.</span></span> <span data-ttu-id="5b3fc-2287">Gamla byte den nya fil storleken ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2288">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2288">Return Values</span></span>

- <span data-ttu-id="5b3fc-2289">**FX_SUCCESS** (0x00) filen trunkerades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="5b3fc-2290">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-2291">Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="5b3fc-2292">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2293">**FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="5b3fc-2294">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2295">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2296">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-2297">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-2298">**FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="5b3fc-2299">**FX_PTR_ERROR** (0X18) ogiltig fil pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="5b3fc-2300">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2301">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2301">Allowed From</span></span>

<span data-ttu-id="5b3fc-2302">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2303">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="5b3fc-2304">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2304">See Also</span></span>

- <span data-ttu-id="5b3fc-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2305">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2309">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2310">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2312">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2319">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2320">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2322">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2323">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2324">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2325">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="5b3fc-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2331">fx_file_write</span></span>

<span data-ttu-id="5b3fc-2332">Skriver byte till fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2333">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2334">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2334">Description</span></span>

<span data-ttu-id="5b3fc-2335">Den här tjänsten skriver byte från den angivna bufferten med början i filens aktuella position.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="5b3fc-2336">När skrivningen är klar är filens interna Läs pekare justerad så att den pekar på nästa byte i filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2337">*Snabbare prestanda uppnås om källhierarkin är på ett långt ord och den begärda storleken är jämnt delbar med sizeof (**ulong**).*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2338">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2338">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2339">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-2340">**buffer_ptr**: pekar på käll bufferten för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="5b3fc-2341">**storlek**: antal byte som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2342">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2342">Return Values</span></span>

- <span data-ttu-id="5b3fc-2343">**FX_SUCCESS** (0x00) fil skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="5b3fc-2344">**FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="5b3fc-2345">**FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="5b3fc-2346">**FX_NO_MORE_SPACE** (0X0a) det finns inget utrymme tillgängligt på mediet för att kunna utföra den här skrivningen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="5b3fc-2347">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2348">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-2349">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2350">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2351">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="5b3fc-2352">**FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="5b3fc-2353">**FX_PTR_ERROR** (0X18) ogiltig fil-eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="5b3fc-2354">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2355">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2355">Allowed From</span></span>

<span data-ttu-id="5b3fc-2356">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2357">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2358">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2358">See Also</span></span>

- <span data-ttu-id="5b3fc-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="5b3fc-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="5b3fc-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="5b3fc-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="5b3fc-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2363">fx_file_close,</span></span>
- <span data-ttu-id="5b3fc-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2364">fx_file_create,</span></span>
- <span data-ttu-id="5b3fc-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="5b3fc-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2366">fx_file_delete,</span></span>
- <span data-ttu-id="5b3fc-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="5b3fc-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="5b3fc-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="5b3fc-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="5b3fc-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="5b3fc-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="5b3fc-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2373">fx_file_open,</span></span>
- <span data-ttu-id="5b3fc-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2374">fx_file_read,</span></span>
- <span data-ttu-id="5b3fc-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="5b3fc-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2376">fx_file_rename,</span></span>
- <span data-ttu-id="5b3fc-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2377">fx_file_seek,</span></span>
- <span data-ttu-id="5b3fc-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="5b3fc-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="5b3fc-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="5b3fc-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="5b3fc-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="5b3fc-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="5b3fc-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="5b3fc-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="5b3fc-2386">Ställer in funktionen för fil skrivnings meddelande</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2387">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="5b3fc-2388">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2388">Description</span></span>

<span data-ttu-id="5b3fc-2389">Den här tjänsten installerar callback-funktionen som anropas efter en lyckad fil skrivnings åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2390">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2390">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2391">**file_ptr**: pekar mot fil kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="5b3fc-2392">**file_write_notify**: funktionen Skriv motringning för fil som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="5b3fc-2393">Om du anger funktionen motringning till NULL inaktive ras motringningsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2394">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2394">Return Values</span></span>

- <span data-ttu-id="5b3fc-2395">**FX_SUCCESS** (0X00) har installerat motringningsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="5b3fc-2396">**FX_PTR_ERROR** (0x18) FILE_PTR är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="5b3fc-2397">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2398">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2398">Allowed From</span></span>

<span data-ttu-id="5b3fc-2399">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2400">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2401">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2401">See Also</span></span>

- <span data-ttu-id="5b3fc-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2402">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2406">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2407">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2409">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2416">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2417">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2419">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2420">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2421">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2423">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="5b3fc-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2428">fx_media_abort</span></span>

<span data-ttu-id="5b3fc-2429">Avbryter medie aktiviteter</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2430">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2431">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2431">Description</span></span>

<span data-ttu-id="5b3fc-2432">Den här tjänsten avbryter alla aktuella aktiviteter som är associerade med mediet, inklusive stängning av alla öppna filer, sändning av en abort-begäran till den associerade driv rutinen och placering av mediet i avbrutet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="5b3fc-2433">Den här tjänsten kallas vanligt vis när I/O-fel upptäcks.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2434">*Mediet måste öppnas igen för att det ska kunna användas igen när en avbrotts åtgärd utförs.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2435">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2435">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2436">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2437">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2437">Return Values</span></span>

- <span data-ttu-id="5b3fc-2438">**FX_SUCCESS** (0x00) mediet har avbrutits.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="5b3fc-2439">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2440">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-2441">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2442">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2442">Allowed From</span></span>

<span data-ttu-id="5b3fc-2443">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2444">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2445">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2445">See Also</span></span>

- <span data-ttu-id="5b3fc-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2448">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2449">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2453">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2454">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2455">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2457">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2458">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2461">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="5b3fc-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="5b3fc-2464">Ogiltig cachelagring av logisk sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2465">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="5b3fc-2466">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2466">Description</span></span>

<span data-ttu-id="5b3fc-2467">Den här tjänsten tömmer alla skadade sektorer i cachen och upphäver sedan hela den logiska sektorens cacheminne.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2468">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2468">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2469">**media_ptr**: pekare till Media Control Block</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2470">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2470">Return Values</span></span>

- <span data-ttu-id="5b3fc-2471">**FX_SUCCESS** (0x00) cachelagring av medie innehåll är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="5b3fc-2472">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2473">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2474">**FX_PTR_ERROR** (0X18) ogiltig media-eller Scratch-pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="5b3fc-2475">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2476">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2476">Allowed From</span></span>

<span data-ttu-id="5b3fc-2477">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2478">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2479">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2479">See Also</span></span>

- <span data-ttu-id="5b3fc-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2481">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2482">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2483">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2487">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2488">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2489">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2491">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2492">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2495">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="5b3fc-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2497">fx_media_check</span></span>

<span data-ttu-id="5b3fc-2498">Söker efter fel i mediet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2499">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2500">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2500">Description</span></span>

<span data-ttu-id="5b3fc-2501">Den här tjänsten kontrollerar det angivna mediet för grundläggande strukturella fel, inklusive fil/katalog över länkning, ogiltiga FAT-kedjor och förlorade kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="5b3fc-2502">Tjänsten ger också möjlighet att korrigera identifierade fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="5b3fc-2503">Den fx_media_check tjänsten kräver minne i minnet för den djupgående första analysen av kataloger och filer på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="5b3fc-2504">Mer specifikt måste det virtuella minnet som tillhandahålls för medie kontroll tjänsten vara tillräckligt stort för att rymma flera katalog poster, en data struktur för att "stacka" den aktuella katalog inmatnings positionen innan du går in i under kataloger och slutligen den logiska FAT-bitars kartan.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="5b3fc-2505">Det virtuella minnet måste vara minst 512-1024 byte plus minne för den logiska FAT-bitars kartan, vilket kräver så många bitar som det finns kluster i mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="5b3fc-2506">Till exempel skulle en enhet med 8000 kluster kräva 1000 byte för att representera och därför kräva en total arbets yta i ordningen på 2048 byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2507">*Den här tjänsten ska endast anropas omedelbart efter fx_media_open och utan någon annan fil system aktivitet.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2508">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2508">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2509">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-2510">**scratch_memory_ptr**: pekar mot start av virtuellt minne.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="5b3fc-2511">**scratch_memory_size**: minnets storlek i byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="5b3fc-2512">**error_correction_option**: fel korrigerings alternativ bitar när biten har angetts utförs fel korrigering.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="5b3fc-2513">Bitarna med fel korrigerings alternativ definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="5b3fc-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="5b3fc-2515">FX_DIRECTORY_ERROR (protokollnumret 0x02)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="5b3fc-2516">FX_LOST_CLUSTER_ERROR (0x04) enkelt eller tillsammans de nödvändiga fel korrigerings alternativen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="5b3fc-2517">Om ingen fel korrigering krävs måste värdet 0 anges.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="5b3fc-2518">**errors_detected_ptr**: målet för fel identifierings bitar enligt definitionen nedan:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="5b3fc-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="5b3fc-2520">FX_DIRECTORY_ERROR (protokollnumret 0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="5b3fc-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2522">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2522">Return Values</span></span>

- <span data-ttu-id="5b3fc-2523">Media kontrollen **FX_SUCCESS** (0X00) lyckades, Visa fel identifierade destinationer för mer information.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="5b3fc-2524">**FX_ACCESS_ERROR** (0X06) Det går inte att utföra kontrollen med öppna filer.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="5b3fc-2525">**FX_FILE_CORRUPT** -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2526">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2527">**FX_NO_MORE_SPACE** (0x0A) Det går inte att frigöra utrymme på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="5b3fc-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) som tillhandahöll det virtuella minnet är inte tillräckligt stort.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="5b3fc-2529">**FX_ERROR_NOT_FIXED** (0X93) fel i FAT32-rot katalogen som inte kunde åtgärdas.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="5b3fc-2530">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2531">**FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="5b3fc-2532">**FX_PTR_ERROR** (0X18) ogiltig media-eller Scratch-pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="5b3fc-2533">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2534">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2534">Allowed From</span></span>

<span data-ttu-id="5b3fc-2535">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2536">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2536">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-2537">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2537">See Also</span></span>

- <span data-ttu-id="5b3fc-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2539">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2541">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2545">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2546">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2547">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2549">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2550">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2553">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="5b3fc-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2555">fx_media_close</span></span>

<span data-ttu-id="5b3fc-2556">Stänger mediet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2557">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2558">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2558">Description</span></span>

<span data-ttu-id="5b3fc-2559">Den här tjänsten stänger det angivna mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2559">This service closes the specified media.</span></span> <span data-ttu-id="5b3fc-2560">När mediet stängs stängs alla öppna filer och eventuella kvarvarande buffertar töms till det fysiska mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2561">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2561">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2562">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2563">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2563">Return Values</span></span>

- <span data-ttu-id="5b3fc-2564">**FX_SUCCESS** (0x00) medie stängningen lyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="5b3fc-2565">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2566">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2567">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-2568">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2569">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2569">Allowed From</span></span>

<span data-ttu-id="5b3fc-2570">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2571">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2572">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2572">See Also</span></span>

- <span data-ttu-id="5b3fc-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2574">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2576">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2580">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2581">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2582">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2584">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2585">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2588">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="5b3fc-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="5b3fc-2591">Ställer in meddelande funktionen för medie stängning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2592">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="5b3fc-2593">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2593">Description</span></span>

<span data-ttu-id="5b3fc-2594">Den här tjänsten anger en funktion för att skicka ett meddelande om motringning som anropas när ett medium har stängts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2595">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2595">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2596">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-2597">**media_close_notify**: medie stängning meddela återanrops funktion som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="5b3fc-2598">Om du skickar NULL som callback-funktionen inaktive ras mediet Stäng motringning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2599">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2599">Return Values</span></span>

- <span data-ttu-id="5b3fc-2600">**FX_SUCCESS** (0X00) har installerat motringningsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="5b3fc-2601">**FX_PTR_ERROR** (0x18) MEDIA_PTR är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="5b3fc-2602">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2603">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2603">Allowed From</span></span>

<span data-ttu-id="5b3fc-2604">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2605">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="5b3fc-2606">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2606">See Also</span></span>

- <span data-ttu-id="5b3fc-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2608">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2610">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2611">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2614">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2615">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2616">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2618">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2619">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2622">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="5b3fc-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="5b3fc-2625">Formaterar Media</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2626">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2626">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="5b3fc-2627">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2627">Description</span></span>

<span data-ttu-id="5b3fc-2628">Den här tjänsten formaterar det angivna mediet på ett exFAT-kompatibelt sätt baserat på de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="5b3fc-2629">Den här tjänsten måste anropas innan mediet kan öppnas.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2630">*Formatering av redan formaterade medier raderar effektivt alla filer och kataloger på mediet.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2631">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2631">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2632">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2632">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="5b3fc-2633">Detta används endast för att ge lite grundläggande information som krävs för att driv rutinen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2633">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="5b3fc-2634">**driv rutin**: pekar på i/O-drivrutinen för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2634">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="5b3fc-2635">Detta är vanligt vis samma driv rutin som anges för efterföljande fx_media_open-anrop.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2635">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="5b3fc-2636">**driver_info_ptr**: pekar mot valfri information som i/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2636">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="5b3fc-2637">**memory_ptr**: pekar på det aktiva minnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2637">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="5b3fc-2638">memory_size anger storleken på arbets medie minnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2638">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="5b3fc-2639">Storleken måste vara minst lika stor som mediets sektor storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2639">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="5b3fc-2640">**volume_name**: pekar på volym namn strängen, vilket är högst 11 tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2640">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="5b3fc-2641">**number_of_fats**: antalet fetter på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2641">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="5b3fc-2642">Aktuell implementering stöder en FAT på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2642">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="5b3fc-2643">**hidden_sectors**: antalet sektorer som är dolda innan mediets start sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2643">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="5b3fc-2644">Detta är vanligt när det finns flera partitioner.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2644">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="5b3fc-2645">**total_sectors**: det totala antalet sektorer i mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2645">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="5b3fc-2646">**bytes_per_sector**: antal byte per sektor, vanligt vis 512.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2646">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="5b3fc-2647">FileX kräver att detta är en multipel av 32.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2647">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="5b3fc-2648">**sectors_per_cluster**: antalet sektorer i varje kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2648">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="5b3fc-2649">Klustret är den minsta allokeringsenheten i ett FAT-filsystem.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2649">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="5b3fc-2650">**volumne_serial_number**: serie numret som ska användas för den här volymen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2650">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="5b3fc-2651">**boundary_unit**: justerings storlek för fysiskt data område i antal sektorer.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2651">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2652">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2652">Return Values</span></span>

- <span data-ttu-id="5b3fc-2653">**FX_SUCCESS** (0x00) medie formatet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2653">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="5b3fc-2654">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2654">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2655">**FX_PTR_ERROR** (0X18) ogiltig media, driv rutin eller minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2655">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="5b3fc-2656">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2656">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2657">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2657">Allowed From</span></span>

<span data-ttu-id="5b3fc-2658">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2658">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2659">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2659">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-2660">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2660">See Also</span></span>

- <span data-ttu-id="5b3fc-2661">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2661">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2662">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2662">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2663">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2663">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2664">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2664">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2665">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2665">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2666">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2666">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2667">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2667">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2668">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2668">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2669">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2669">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2670">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2670">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2671">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2671">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2672">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2672">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2673">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2673">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2674">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2674">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2675">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2675">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2676">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2676">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2677">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2677">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="5b3fc-2678">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2678">fx_media_extended_space_available</span></span>

<span data-ttu-id="5b3fc-2679">Returnerar tillgängligt medie utrymme</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2679">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2680">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2680">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2681">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2681">Description</span></span>

<span data-ttu-id="5b3fc-2682">Den här tjänsten returnerar antalet byte som är tillgängliga i mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2682">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="5b3fc-2683">Den här tjänsten är utformad för exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2683">This service is designed for exFAT.</span></span> <span data-ttu-id="5b3fc-2684">Pekaren till *available_bytes* parameter tar ett 64-bitars heltals värde, vilket gör att anroparen kan arbeta med Media utanför 4 GB-intervallet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2684">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2685">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2685">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2686">**media_ptr**: pekar på ett tidigare öppnat medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2686">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="5b3fc-2687">**available_bytes_ptr**: tillgängliga byte kvar på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2687">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2688">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2688">Return Values</span></span>

- <span data-ttu-id="5b3fc-2689">**FX_SUCCESS** (0X00) har hämtat tillgängligt utrymme på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2689">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="5b3fc-2690">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2690">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2691">**FX_PTR_ERROR** (0X18) ogiltig Media pekare eller tillgängliga byte pekare är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2691">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="5b3fc-2692">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2692">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2693">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2693">Allowed From</span></span>

<span data-ttu-id="5b3fc-2694">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2694">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2695">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2695">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2696">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2696">See Also</span></span>

- <span data-ttu-id="5b3fc-2697">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2697">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2698">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2698">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2699">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2699">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2700">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2700">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2701">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2701">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2702">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2702">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2703">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2703">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2704">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2704">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2705">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2705">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2706">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2706">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2707">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2707">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2708">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2708">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2709">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2709">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2710">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2710">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2711">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2711">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2712">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2712">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2713">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2713">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="5b3fc-2714">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2714">fx_media_flush</span></span>

<span data-ttu-id="5b3fc-2715">Tömmer data till fysiska media</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2715">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2716">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2716">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2717">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2717">Description</span></span>

<span data-ttu-id="5b3fc-2718">Den här tjänsten tömmer alla cachelagrade sektorer och katalog poster för alla ändrade filer till det fysiska mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2718">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2719">*Den här rutinen kan anropas regelbundet av programmet för att minska risken för skadade filer och/eller data förlust i händelse av plötslig förlust av ström på målet.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2719">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2720">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2720">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2721">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2721">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2722">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2722">Return Values</span></span>

- <span data-ttu-id="5b3fc-2723">**FX_SUCCESS** (0x00) medie tömning lyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2723">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="5b3fc-2724">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2724">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2725">**FX_FILE_CORRUPT**    -filen (0x08) är skadad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2725">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="5b3fc-2726">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2726">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2727">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2727">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2728">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2728">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-2729">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2729">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-2730">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2730">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2731">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2731">Allowed From</span></span>

<span data-ttu-id="5b3fc-2732">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2733">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2733">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2734">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2734">See Also</span></span>

- <span data-ttu-id="5b3fc-2735">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2735">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2736">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2736">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2737">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2737">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2738">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2738">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2739">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2739">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2740">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2740">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2741">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2741">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2742">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2742">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2743">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2743">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2744">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2744">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2745">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2745">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2746">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2746">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2747">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2747">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2748">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2748">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2749">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2749">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2750">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2750">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2751">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2751">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="5b3fc-2752">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2752">fx_media_format</span></span>

<span data-ttu-id="5b3fc-2753">Formaterar Media</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2753">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2754">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2754">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="5b3fc-2755">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2755">Description</span></span>

<span data-ttu-id="5b3fc-2756">Den här tjänsten formaterar det angivna mediet i ett FAT 12/16/32-kompatibelt sätt baserat på de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2756">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="5b3fc-2757">Den här tjänsten måste anropas innan mediet kan öppnas.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2757">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2758">*Formatering av redan formaterade medier raderar effektivt alla filer och kataloger på mediet.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2758">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2759">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2759">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2760">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2760">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="5b3fc-2761">Detta används endast för att ge lite grundläggande information som krävs för att driv rutinen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2761">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="5b3fc-2762">**driv rutin**: pekar på i/O-drivrutinen för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2762">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="5b3fc-2763">Detta är vanligt vis samma driv rutin som anges för efterföljande fx_media_open-anrop.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2763">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="5b3fc-2764">**driver_info_ptr**: pekar mot valfri information som i/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2764">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="5b3fc-2765">**memory_ptr**: pekar på det aktiva minnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2765">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="5b3fc-2766">**memory_size**: anger storleken på arbets medie minnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2766">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="5b3fc-2767">Storleken måste vara minst lika stor som mediets sektor storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2767">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="5b3fc-2768">**volume_name**: pekar på volym namn strängen, vilket är högst 11 tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2768">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="5b3fc-2769">**number_of_fats**: antalet fetter på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2769">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="5b3fc-2770">Det minimala värdet är 1 för primärt fett.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2770">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="5b3fc-2771">Värden som är större än 1 leder till att ytterligare FAT-kopior bevaras vid körning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2771">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="5b3fc-2772">**directory_entries**: antalet katalog poster i rot katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2772">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="5b3fc-2773">**hidden_sectors**: antalet sektorer som är dolda innan mediets start sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2773">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="5b3fc-2774">Detta är vanligt när det finns flera partitioner.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2774">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="5b3fc-2775">**total_sectors**: det totala antalet sektorer i mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2775">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="5b3fc-2776">**bytes_per_sector**: antal byte per sektor, vanligt vis 512.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2776">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="5b3fc-2777">FileX kräver att detta är en multipel av 32.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2777">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="5b3fc-2778">**sectors_per_cluster**: antalet sektorer i varje kluster.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2778">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="5b3fc-2779">Klustret är den minsta allokeringsenheten i ett FAT-filsystem.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2779">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="5b3fc-2780">**huvuden**: antal fysiska huvuden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2780">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="5b3fc-2781">**sectors_per_track**: antalet sektorer per spår.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2781">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2782">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2782">Return Values</span></span>

- <span data-ttu-id="5b3fc-2783">**FX_SUCCESS** (0x00) medie formatet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2783">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="5b3fc-2784">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2784">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2785">**FX_PTR_ERROR** (0X18) ogiltig media, driv rutin eller minnes pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2785">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="5b3fc-2786">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2786">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2787">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2787">Allowed From</span></span>

<span data-ttu-id="5b3fc-2788">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2789">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2789">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-2790">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2790">See Also</span></span>

- <span data-ttu-id="5b3fc-2791">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2791">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2792">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2792">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2793">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2793">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2794">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2794">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2795">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2795">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2796">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2796">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2797">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2797">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2798">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2798">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2799">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2799">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2800">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2800">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2801">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2801">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2802">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2802">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2803">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2803">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2804">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2804">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2805">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2805">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2806">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2806">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2807">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2807">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="5b3fc-2808">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2808">fx_media_open</span></span>

<span data-ttu-id="5b3fc-2809">Öppnar mediet för fil åtkomst</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2809">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2810">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2810">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2811">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2811">Description</span></span>

<span data-ttu-id="5b3fc-2812">Den här tjänsten öppnar ett medium för fil åtkomst med hjälp av den angivna I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2812">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-2813">*Det minne som har angetts för den här tjänsten används för att implementera en intern logisk sektor, vilket innebär att det mer minne som tillhandahölls desto mer fysiskt I/O minskas. FileX kräver en cache på minst en logisk sektor (byte per sektor av mediet).*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2813">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2814">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2814">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2815">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2815">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-2816">**media_name**: pekar på mediets namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2816">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="5b3fc-2817">**media_driver**: pekare till i/O-drivrutin för det här mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2817">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="5b3fc-2818">I/O-drivrutinen måste uppfylla kraven för FileX-drivrutin som definieras i kapitel 5.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2818">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="5b3fc-2819">**driver_info_ptr**: pekar mot valfri information som den angivna i/O-drivrutinen kan använda.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2819">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="5b3fc-2820">**memory_ptr**: pekar på det aktiva minnet för mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2820">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="5b3fc-2821">**memory_size**: anger storleken på arbets medie minnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2821">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="5b3fc-2822">Storleken måste vara lika stor som mediets sektor storlek (vanligt vis 512 byte).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2822">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2823">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2823">Return Values</span></span>

- <span data-ttu-id="5b3fc-2824">**FX_SUCCESS** (0x00) media är öppna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2824">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="5b3fc-2825">**FX_BOOT_ERROR** (0x01) Det gick inte att läsa mediets start sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2825">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="5b3fc-2826">**FX_MEDIA_INVALID** (protokollnumret 0x02) det angivna mediets start sektor är skadat eller ogiltigt.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2826">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="5b3fc-2827">Dessutom används den här retur koden för att ange att antingen cache-storleken för den logiska sektorn eller FAT-poststorleken inte är en potens av 2.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2827">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="5b3fc-2828">**FX_FAT_READ_ERROR** (0x03) Det gick inte att läsa mediet fat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2828">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="5b3fc-2829">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2829">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2830">**FX_PTR_ERROR** (0X18) en eller flera pekare är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2830">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="5b3fc-2831">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2831">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2832">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2832">Allowed From</span></span>

<span data-ttu-id="5b3fc-2833">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2834">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2834">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2835">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2835">See Also</span></span>

- <span data-ttu-id="5b3fc-2836">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2836">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2837">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2837">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2838">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2838">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2839">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2839">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2840">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2840">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2841">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2841">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2842">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2842">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2843">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2843">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2844">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2844">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2845">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2845">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2846">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2846">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2847">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2847">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2848">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2848">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2849">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2849">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2850">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2850">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2851">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2851">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2852">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2852">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="5b3fc-2853">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2853">fx_media_open_notify_set</span></span>

<span data-ttu-id="5b3fc-2854">Anger funktionen för att öppna meddelanden i media</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2854">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2855">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2855">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="5b3fc-2856">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2856">Description</span></span>

<span data-ttu-id="5b3fc-2857">Den här tjänsten anger en funktion för att skicka ett meddelande om motringning som anropas när ett medium har öppnats.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2857">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2858">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2858">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2859">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2859">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-2860">**media_open_notify**: mediet är öppet, så att callback-funktionen installeras.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2860">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="5b3fc-2861">Om du skickar NULL som callback-funktionen inaktive ras mediet öppna motanrop.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2861">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2862">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2862">Return Values</span></span>


- <span data-ttu-id="5b3fc-2863">**FX_SUCCESS** (0x00) installerade återanrops funktionen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2863">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="5b3fc-2864">**FX_PTR_ERROR** (0x18) MEDIA_PTR är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2864">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="5b3fc-2865">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2865">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2866">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2866">Allowed From</span></span>

<span data-ttu-id="5b3fc-2867">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2868">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2868">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2869">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2869">See Also</span></span>

- <span data-ttu-id="5b3fc-2870">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2870">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2871">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2871">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2872">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2872">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2873">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2873">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2874">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2874">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2875">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2875">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2876">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2876">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2877">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2877">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2878">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2878">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2879">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2879">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2880">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2880">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2881">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2881">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2882">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2882">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2883">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2883">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2884">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2884">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2885">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2885">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2886">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2886">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="5b3fc-2887">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2887">fx_media_read</span></span>

<span data-ttu-id="5b3fc-2888">Läser logisk sektor från media</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2888">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2889">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2889">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2890">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2890">Description</span></span>

<span data-ttu-id="5b3fc-2891">Den här tjänsten läser en logisk sektor från mediet och placerar den i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2891">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2892">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2892">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2893">**media_ptr**: pekar på ett tidigare öppnat medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2893">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="5b3fc-2894">**logical_sector**: logisk sektor som ska läsas.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2894">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="5b3fc-2895">**buffer_ptr**: pekar mot målet för den logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2895">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2896">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2896">Return Values</span></span>

- <span data-ttu-id="5b3fc-2897">**FX_SUCCESS** (0x00) medie läsning har lästs.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2897">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="5b3fc-2898">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2898">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2899">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2899">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2900">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2900">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-2901">**FX_PTR_ERROR** (0X18) ogiltig media-eller buffert pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2901">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="5b3fc-2902">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2902">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2903">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2903">Allowed From</span></span>

<span data-ttu-id="5b3fc-2904">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2904">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2905">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2905">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2906">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2906">See Also</span></span>

- <span data-ttu-id="5b3fc-2907">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2907">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2908">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2908">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2909">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2909">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2910">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2910">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2911">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2911">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2912">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2912">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2913">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2913">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2914">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2914">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2915">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2915">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2916">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2916">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2917">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2917">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2918">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2918">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2919">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2919">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2920">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2920">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2921">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2921">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2922">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2922">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2923">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2923">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="5b3fc-2924">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2924">fx_media_space_available</span></span>

<span data-ttu-id="5b3fc-2925">Returnerar tillgängligt medie utrymme</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2925">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2926">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2926">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="5b3fc-2927">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2927">Description</span></span>

<span data-ttu-id="5b3fc-2928">Den här tjänsten returnerar antalet byte som är tillgängliga i mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2928">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="5b3fc-2929">Om du vill arbeta med mediet som är större än 4 GB använder programmet tjänsten *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2929">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2930">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2930">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2931">**media_ptr**: pekar på ett tidigare öppnat medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2931">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="5b3fc-2932">**available_bytes_ptr**: tillgängliga byte kvar på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2932">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2933">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2933">Return Values</span></span>

- <span data-ttu-id="5b3fc-2934">**FX_SUCCESS** (0x00) returnerade tillgängligt utrymme på mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2934">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="5b3fc-2935">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2935">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2936">**FX_PTR_ERROR** (0X18) ogiltig Media pekare eller tillgängliga byte pekare är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2936">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="5b3fc-2937">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2937">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2938">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2938">Allowed From</span></span>

<span data-ttu-id="5b3fc-2939">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2939">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2940">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2940">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2941">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2941">See Also</span></span>

- <span data-ttu-id="5b3fc-2942">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2942">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2943">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2943">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2944">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2944">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2945">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2945">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2946">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2946">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2947">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2947">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2948">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2948">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2949">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2949">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2950">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2950">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2951">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2951">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2952">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2952">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2953">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2953">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2954">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2954">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2955">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2955">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-2956">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2956">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2957">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2957">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2958">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2958">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="5b3fc-2959">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2959">fx_media_volume_get</span></span>

<span data-ttu-id="5b3fc-2960">Hämtar medie volymens namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2960">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-2961">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2961">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="5b3fc-2962">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2962">Description</span></span>

<span data-ttu-id="5b3fc-2963">Den här tjänsten hämtar volym namnet för det tidigare öppnade mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2963">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-2964">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2964">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-2965">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2965">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-2966">**volume_name**: pekar mot mål för volym namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2966">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="5b3fc-2967">Observera att målet måste vara minst tillräckligt stort för att rymma 12 tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2967">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="5b3fc-2968">**volume_source**: anger var du vill hämta namnet, antingen från start sektorn eller rot katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2968">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="5b3fc-2969">Giltiga värden för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2969">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="5b3fc-2970">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2970">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="5b3fc-2971">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2971">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-2972">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2972">Return Values</span></span>

- <span data-ttu-id="5b3fc-2973">**FX_SUCCESS** (0x00) medie volym hämtades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2973">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="5b3fc-2974">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2974">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-2975">Det gick inte att hitta **FX_NOT_FOUND** -volymen (0x04).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2975">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="5b3fc-2976">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2976">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-2977">**FX_PTR_ERROR** (0X18) ogiltig media-eller volym destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2977">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="5b3fc-2978">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2978">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-2979">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2979">Allowed From</span></span>

<span data-ttu-id="5b3fc-2980">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2980">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-2981">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2981">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="5b3fc-2982">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2982">See Also</span></span>

- <span data-ttu-id="5b3fc-2983">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2983">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-2984">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2984">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-2985">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2985">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-2986">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2986">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-2987">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2987">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-2988">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2988">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-2989">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2989">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-2990">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2990">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-2991">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2991">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-2992">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2992">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-2993">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2993">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-2994">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2994">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-2995">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2995">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-2996">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2996">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-2997">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2997">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-2998">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2998">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-2999">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-2999">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="5b3fc-3000">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3000">fx_media_volume_get_extended</span></span>

<span data-ttu-id="5b3fc-3001">Hämtar medie volymens namn för tidigare öppnade medier</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3001">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3002">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3002">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3003">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3003">Description</span></span>

<span data-ttu-id="5b3fc-3004">Den här tjänsten hämtar volym namnet för det tidigare öppnade mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3004">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3005">Den här tjänsten är identisk med ***fx_media_volume_get () _,** förutom att anroparen skickar i storlek på den _ *volume_name** bufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3005">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3006">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3006">Input Parameters</span></span>


- <span data-ttu-id="5b3fc-3007">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3007">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3008">**volume_name**: pekar mot mål för volym namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3008">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="5b3fc-3009">Observera att målet måste vara minst tillräckligt stort för att rymma 12 tecken.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3009">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="5b3fc-3010">**volume_name_buffer_length**: volume_name buffertens storlek.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3010">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="5b3fc-3011">**volume_source**: anger var du vill hämta namnet, antingen från start sektorn eller rot katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3011">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="5b3fc-3012">Giltiga värden för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3012">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="5b3fc-3013">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3013">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="5b3fc-3014">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3014">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3015">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3015">Return Values</span></span>

- <span data-ttu-id="5b3fc-3016">**FX_SUCCESS** (0x00) medie volym hämtades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3016">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="5b3fc-3017">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3017">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3018">Det gick inte att hitta **FX_NOT_FOUND** -volymen (0x04).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3018">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="5b3fc-3019">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3019">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3020">**FX_PTR_ERROR** (0X18) ogiltig media-eller volym destinations pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3020">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="5b3fc-3021">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3021">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3022">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3022">Allowed From</span></span>

<span data-ttu-id="5b3fc-3023">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3023">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3024">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3024">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-3025">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3025">See Also</span></span>

- <span data-ttu-id="5b3fc-3026">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3026">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-3027">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3027">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-3028">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3028">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-3029">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3029">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-3030">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3030">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-3031">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3031">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-3032">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3032">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-3033">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3033">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-3034">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3034">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-3035">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3035">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-3036">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3036">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-3037">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3037">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-3038">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3038">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-3039">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3039">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-3040">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3040">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-3041">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3041">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-3042">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3042">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="5b3fc-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3043">fx_media_volume_set</span></span>

<span data-ttu-id="5b3fc-3044">Anger medie volymens namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3044">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3045">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3045">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3046">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3046">Description</span></span>

<span data-ttu-id="5b3fc-3047">Den här tjänsten anger volym namnet för det tidigare öppnade mediet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3047">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3048">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3048">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3049">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3049">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3050">**volume_name**: pekar mot volymens namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3050">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3051">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3051">Return Values</span></span>

- <span data-ttu-id="5b3fc-3052">Den **FX_SUCCESS** (0x00) medie volym uppsättningen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3052">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="5b3fc-3053">**FX_INVALID_NAME** (0x0C) Volume_name är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3053">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="5b3fc-3054">**FX_MEDIA_INVALID** (protokollnumret 0x02) Det gick inte att ange volym namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3054">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="5b3fc-3055">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3055">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3056">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3056">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3057">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3057">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-3058">**FX_PTR_ERROR** (0X18) ogiltigt medium eller volym namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3058">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="5b3fc-3059">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3059">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3060">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3060">Allowed From</span></span>

<span data-ttu-id="5b3fc-3061">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3061">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3062">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3062">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-3063">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3063">See Also</span></span>

- <span data-ttu-id="5b3fc-3064">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3064">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-3065">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3065">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-3066">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3066">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-3067">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3067">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-3068">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3068">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-3069">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3069">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-3070">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3070">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-3071">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3071">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-3072">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3072">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-3073">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3073">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-3074">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3074">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-3075">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3075">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-3076">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3076">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-3077">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3077">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-3078">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3078">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-3079">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3079">fx_media_write</span></span>
- <span data-ttu-id="5b3fc-3080">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3080">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="5b3fc-3081">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3081">fx_media_write</span></span>

<span data-ttu-id="5b3fc-3082">Skriver logisk sektor</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3082">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3083">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3083">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3084">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3084">Description</span></span>

<span data-ttu-id="5b3fc-3085">Den här tjänsten skriver den angivna bufferten till den angivna logiska sektorn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3085">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3086">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3086">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3087">**media_ptr**: pekar på ett tidigare öppnat medium.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3087">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="5b3fc-3088">**logical_sector**: logisk sektor som ska skrivas.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3088">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="5b3fc-3089">**buffer_ptr**: pekar mot källan för den logiska sektor skrivningen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3089">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3090">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3090">Return Values</span></span>

- <span data-ttu-id="5b3fc-3091">**FX_SUCCESS** (0x00) skrivning av media lyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3091">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="5b3fc-3092">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3092">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3093">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3093">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-3094">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3094">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3095">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3095">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-3096">**FX_PTR_ERROR** (0X18) ogiltig medie pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3096">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="5b3fc-3097">**FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3097">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3098">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3098">Allowed From</span></span>

<span data-ttu-id="5b3fc-3099">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3099">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3100">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3100">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3101">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3101">See Also</span></span>

- <span data-ttu-id="5b3fc-3102">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3102">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="5b3fc-3103">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3103">fx_media_abort</span></span>
- <span data-ttu-id="5b3fc-3104">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3104">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="5b3fc-3105">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3105">fx_media_check</span></span>
- <span data-ttu-id="5b3fc-3106">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3106">fx_media_close</span></span>
- <span data-ttu-id="5b3fc-3107">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3107">fx_media_close_notify_set</span></span>
- <span data-ttu-id="5b3fc-3108">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3108">fx_media_exFAT_format</span></span>
- <span data-ttu-id="5b3fc-3109">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3109">fx_media_extended_space_available</span></span>
- <span data-ttu-id="5b3fc-3110">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3110">fx_media_flush</span></span>
- <span data-ttu-id="5b3fc-3111">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3111">fx_media_format</span></span>
- <span data-ttu-id="5b3fc-3112">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3112">fx_media_open</span></span>
- <span data-ttu-id="5b3fc-3113">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3113">fx_media_open_notify_set</span></span>
- <span data-ttu-id="5b3fc-3114">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3114">fx_media_read</span></span>
- <span data-ttu-id="5b3fc-3115">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3115">fx_media_space_available</span></span>
- <span data-ttu-id="5b3fc-3116">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3116">fx_media_volume_get</span></span>
- <span data-ttu-id="5b3fc-3117">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3117">fx_media_volume_set</span></span>
- <span data-ttu-id="5b3fc-3118">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3118">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="5b3fc-3119">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3119">fx_system_date_get</span></span>

<span data-ttu-id="5b3fc-3120">Hämtar fil system datum</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3120">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3121">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3121">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3122">Description</span></span>

<span data-ttu-id="5b3fc-3123">Den här tjänsten returnerar det aktuella system datumet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3123">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3124">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3124">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3125">**år**: pekare till målet för år.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3125">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="5b3fc-3126">**månad**: pekar mot mål i månaden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3126">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="5b3fc-3127">**dag**: pekare till mål för dag.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3127">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3128">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3128">Return Values</span></span>

- <span data-ttu-id="5b3fc-3129">**FX_SUCCESS** (0X00) lyckad datum hämtning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3129">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="5b3fc-3130">**FX_PTR_ERROR** (0X18) en eller flera INDATAPARAMETRAR är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3130">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3131">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3131">Allowed From</span></span>

<span data-ttu-id="5b3fc-3132">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3133">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3133">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3134">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3134">See Also</span></span>

- <span data-ttu-id="5b3fc-3135">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3135">fx_system_date_set</span></span>
- <span data-ttu-id="5b3fc-3136">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3136">fx_system_initialize</span></span>
- <span data-ttu-id="5b3fc-3137">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3137">fx_system_time_get</span></span>
- <span data-ttu-id="5b3fc-3138">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3138">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="5b3fc-3139">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3139">fx_system_date_set</span></span>

<span data-ttu-id="5b3fc-3140">Anger system datum</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3140">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3141">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3141">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3142">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3142">Description</span></span>

<span data-ttu-id="5b3fc-3143">Den här tjänsten anger det system datum som anges.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3143">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-3144">*Den här tjänsten ska ringas strax efter **fx_system_initialize** att ange det ursprungliga system datumet. Som standard är system datumet den senaste allmänna FileX-versionen.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3144">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3145">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3145">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3146">**år**: nytt år.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3146">**year**: New year.</span></span> <span data-ttu-id="5b3fc-3147">Det giltiga intervallet är från 1980 till och med året 2107.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3147">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="5b3fc-3148">**månad**: ny månad.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3148">**month**: New month.</span></span> <span data-ttu-id="5b3fc-3149">Det giltiga intervallet är mellan 1 och 12.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3149">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="5b3fc-3150">**dag**: ny dag.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3150">**day**: New day.</span></span> <span data-ttu-id="5b3fc-3151">Det giltiga intervallet är mellan 1 och 31, beroende på månad och år för skottår.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3151">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3152">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3152">Return Values</span></span>

- <span data-ttu-id="5b3fc-3153">Datum inställningen för **FX_SUCCESS** (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3153">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="5b3fc-3154">**FX_INVALID_YEAR** (0X12) ogiltigt år har angetts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3154">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="5b3fc-3155">**FX_INVALID_MONTH** (0X13) ogiltig månad har angetts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3155">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="5b3fc-3156">**FX_INVALID_DAY** (0X14) ogiltig dag har angetts.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3156">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3157">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3157">Allowed From</span></span>

<span data-ttu-id="5b3fc-3158">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3158">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3159">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3159">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-3160">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3160">See Also</span></span>

- <span data-ttu-id="5b3fc-3161">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3161">fx_system_date_get</span></span>
- <span data-ttu-id="5b3fc-3162">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3162">fx_system_initialize</span></span>
- <span data-ttu-id="5b3fc-3163">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3163">fx_system_time_get</span></span>
- <span data-ttu-id="5b3fc-3164">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3164">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="5b3fc-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3165">fx_system_initialize</span></span>

<span data-ttu-id="5b3fc-3166">Initierar hela systemet</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3166">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3167">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3167">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3168">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3168">Description</span></span>

<span data-ttu-id="5b3fc-3169">Den här tjänsten initierar alla huvud data strukturer för FileX.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3169">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="5b3fc-3170">Den ska anropas antingen i ***tx_application_define*** eller eventuellt från en initierings tråd och måste anropas innan någon annan FileX-tjänst används.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3170">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-3171">\* När det här anropet har initierats bör programmet anropa ***fx_system_date_set** _ och _ *fx_system_time_set** för att börja med ett korrekt system datum och tid.\*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3171">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3172">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3172">Input Parameters</span></span>

<span data-ttu-id="5b3fc-3173">Inget</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3173">None</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3174">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3174">Return Values</span></span>

<span data-ttu-id="5b3fc-3175">Inga.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3175">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3176">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3176">Allowed From</span></span>

<span data-ttu-id="5b3fc-3177">Initiering, trådar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3178">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3178">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3179">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3179">See Also</span></span>

- <span data-ttu-id="5b3fc-3180">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3180">fx_system_date_get</span></span>
- <span data-ttu-id="5b3fc-3181">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3181">fx_system_date_set</span></span>
- <span data-ttu-id="5b3fc-3182">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3182">fx_system_time_get</span></span>
- <span data-ttu-id="5b3fc-3183">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3183">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="5b3fc-3184">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3184">fx_system_time_get</span></span>

<span data-ttu-id="5b3fc-3185">Hämtar aktuell system tid</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3185">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3186">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3186">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3187">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3187">Description</span></span>

<span data-ttu-id="5b3fc-3188">Den här tjänsten hämtar den aktuella system tiden.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3188">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3189">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3189">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3190">**timme**: pekare till målet i timmen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3190">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="5b3fc-3191">**minut**: pekare till målet för minut.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3191">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="5b3fc-3192">**sekund**: pekar mot målet för en sekund.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3192">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3193">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3193">Return Values</span></span>

- <span data-ttu-id="5b3fc-3194">**FX_SUCCESS** (0X00) lyckad system tids hämtning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3194">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="5b3fc-3195">**FX_PTR_ERROR** (0X18) en eller flera indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3195">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3196">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3196">Allowed From</span></span>

<span data-ttu-id="5b3fc-3197">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3197">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3198">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3198">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3199">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3199">See Also</span></span>

- <span data-ttu-id="5b3fc-3200">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3200">fx_system_date_get</span></span>
- <span data-ttu-id="5b3fc-3201">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3201">fx_system_date_set</span></span>
- <span data-ttu-id="5b3fc-3202">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3202">fx_system_initialize</span></span>
- <span data-ttu-id="5b3fc-3203">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3203">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="5b3fc-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3204">fx_system_time_set</span></span>

<span data-ttu-id="5b3fc-3205">Anger aktuell system tid</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3205">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3206">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3206">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3207">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3207">Description</span></span>

<span data-ttu-id="5b3fc-3208">Den här tjänsten anger den aktuella system tiden som anges av indataparametrarna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3208">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-3209">*Den här tjänsten ska ringas strax efter **fx_system_initialize** för att ställa in den första system tiden. System tiden är som standard 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3209">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3210">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3210">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3211">**timme**: ny timme (0-23).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3211">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="5b3fc-3212">**Minute**: ny minut (0-59).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3212">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="5b3fc-3213">**sekund**: ny sekund (0-59).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3213">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3214">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3214">Return Values</span></span>

- <span data-ttu-id="5b3fc-3215">**FX_SUCCESS** (0X00) lyckad system tids hämtning.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3215">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="5b3fc-3216">**FX_INVALID_HOUR**    (0X15) ny timme är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3216">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="5b3fc-3217">**FX_INVALID_MINUTE** (0X16) ny minut är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3217">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="5b3fc-3218">**FX_INVALID_SECOND** (0X17) ny sekund är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3218">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3219">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3219">Allowed From</span></span>

<span data-ttu-id="5b3fc-3220">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3221">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3221">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="5b3fc-3222">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3222">See Also</span></span>

- <span data-ttu-id="5b3fc-3223">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3223">fx_system_date_get</span></span>
- <span data-ttu-id="5b3fc-3224">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3224">fx_system_date_set</span></span>
- <span data-ttu-id="5b3fc-3225">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3225">fx_system_initialize</span></span>
- <span data-ttu-id="5b3fc-3226">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3226">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="5b3fc-3227">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3227">fx_unicode_directory_create</span></span>

<span data-ttu-id="5b3fc-3228">Skapar en Unicode-katalog</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3228">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3229">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3229">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3230">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3230">Description</span></span>

<span data-ttu-id="5b3fc-3231">Den här tjänsten skapar en Unicode-namngiven under katalog i den aktuella standard katalogen – ingen Sök vägs information tillåts i Unicode-källans namn parameter.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3231">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="5b3fc-3232">Om det lyckas returneras det korta namnet (8,3-formatet) för den nyligen skapade Unicode-underkatalogen av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3232">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-3233">*Alla åtgärder i Unicode-underkatalogen (vilket gör den till standard Sök vägen, ta bort osv.) bör göras genom att ange det returnerade korta namnet (8,3-formatet) till standard katalog tjänsterna för FileX.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3233">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3234">*Den här tjänsten stöds inte på exFAT media.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3234">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3235">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3235">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3236">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3236">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3237">**source_unicode_name**: pekar mot Unicode-namnet för den nya under katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3237">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="5b3fc-3238">**source_unicode_length**: längden på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3238">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3239">**short_name**: pekare till målet för kort namn (8,3-format) för den nya Unicode-underkatalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3239">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3240">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3240">Return Values</span></span>

- <span data-ttu-id="5b3fc-3241">**FX_SUCCESS** (0X00) Unicode-katalogen har skapats.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3241">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="5b3fc-3242">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3242">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3243">**FX_ALREADY_CREATED** (0x0B) som den angivna katalogen finns redan.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3243">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="5b3fc-3244">**FX_NO_MORE_SPACE** (0X0a) inga fler kluster är tillgängliga i mediet för den nya katalog posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3244">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="5b3fc-3245">Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3245">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="5b3fc-3246">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3246">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-3247">**FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3247">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="5b3fc-3248">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3248">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="5b3fc-3249">**FX_IO_ERROR (0x90)** Driv rutins-I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3249">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3250">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3250">Allowed From</span></span>

<span data-ttu-id="5b3fc-3251">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3252">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3252">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3253">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3253">See Also</span></span>

- <span data-ttu-id="5b3fc-3254">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3254">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3255">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3255">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3256">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3256">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-3257">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3257">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-3258">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3258">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-3259">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3259">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-3260">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3260">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-3261">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3261">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-3262">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3262">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-3263">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3263">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-3264">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3264">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-3265">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3265">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-3266">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3266">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-3267">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3267">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-3268">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3268">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-3269">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3269">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-3270">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3270">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-3271">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3271">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-3272">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3272">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-3273">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3273">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="5b3fc-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3274">fx_unicode_directory_rename</span></span>

<span data-ttu-id="5b3fc-3275">Byter namn på katalogen med Unicode-sträng</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3275">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3276">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3276">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3277">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3277">Description</span></span>

<span data-ttu-id="5b3fc-3278">Den här tjänsten ändrar en Unicode-namngiven under katalog till ett angivet nytt Unicode-namn i den aktuella arbets katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3278">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="5b3fc-3279">Unicode-namnets parametrar får inte innehålla Sök vägs information.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3279">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3280">*Den här tjänsten stöds inte på exFAT media.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3280">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3281">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3281">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3282">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3282">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3283">**old_unicode_name**: pekar mot Unicode-namnet för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3283">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="5b3fc-3284">**old_unicode_name_length**: längden på det aktuella Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3284">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3285">**new_unicode_name**: pekar mot det nya Unicode-filnamn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3285">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="5b3fc-3286">**old_unicode_name_length**: längden på det nya Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3286">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3287">**new_short_name**: pekare till målet för kort namn (8,3-format) för den omdöpta Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3287">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="5b3fc-3288">Byt namn på katalogen med Unicode</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3288">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3289">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3289">Return Values</span></span>

- <span data-ttu-id="5b3fc-3290">**FX_SUCCESS** (0x00) media är öppna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3290">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="5b3fc-3291">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3291">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3292">**FX_ALREADY_CREATED** (0x0B) det angivna katalog namnet finns redan.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3292">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="5b3fc-3293">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3293">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3294">**FX_PTR_ERROR** (0X18) en eller flera pekare är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3294">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="5b3fc-3295">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3295">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="5b3fc-3296">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3296">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3297">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3297">Allowed From</span></span>

<span data-ttu-id="5b3fc-3298">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3298">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3299">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3299">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3300">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3300">See Also</span></span>

- <span data-ttu-id="5b3fc-3301">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3301">fx_directory_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3302">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3302">fx_directory_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3303">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3303">fx_directory_create</span></span>
- <span data-ttu-id="5b3fc-3304">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3304">fx_directory_default_get</span></span>
- <span data-ttu-id="5b3fc-3305">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3305">fx_directory_default_set</span></span>
- <span data-ttu-id="5b3fc-3306">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3306">fx_directory_delete</span></span>
- <span data-ttu-id="5b3fc-3307">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3307">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="5b3fc-3308">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3308">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-3309">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3309">fx_directory_information_get</span></span>
- <span data-ttu-id="5b3fc-3310">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3310">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="5b3fc-3311">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3311">fx_directory_local_path_get</span></span>
- <span data-ttu-id="5b3fc-3312">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3312">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="5b3fc-3313">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3313">fx_directory_local_path_set</span></span>
- <span data-ttu-id="5b3fc-3314">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3314">fx_directory_long_name_get</span></span>
- <span data-ttu-id="5b3fc-3315">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3315">fx_directory_name_test</span></span>
- <span data-ttu-id="5b3fc-3316">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3316">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="5b3fc-3317">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3317">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="5b3fc-3318">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3318">fx_directory_rename</span></span>
- <span data-ttu-id="5b3fc-3319">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3319">fx_directory_short_name_get</span></span>
- <span data-ttu-id="5b3fc-3320">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3320">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="5b3fc-3321">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3321">fx_unicode_file_create</span></span>

<span data-ttu-id="5b3fc-3322">Skapar en Unicode-fil</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3322">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3323">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3323">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3324">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3324">Description</span></span>

<span data-ttu-id="5b3fc-3325">Den här tjänsten skapar en Unicode-namngiven fil i den aktuella standard katalogen – ingen Sök vägs information tillåts i Unicode-källans namn parameter.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3325">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="5b3fc-3326">Om det lyckas returneras det korta namnet (8,3-formatet) för den nyligen skapade Unicode-filen av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3326">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="5b3fc-3327">*Alla åtgärder på Unicode-filen (öppna, skriva, läsa, stänga osv.) bör utföras genom att tillhandahålla det returnerade korta namnet (8,3-formatet) till standard-FileX fil tjänster.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3327">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3328">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3328">Input Parameters</span></span>


- <span data-ttu-id="5b3fc-3329">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3329">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3330">**source_unicode_name**: pekar mot Unicode-namnet för den nya filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3330">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="5b3fc-3331">**source_unicode_length**: längden på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3331">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3332">**short_name**: pekare till målet för kort namn (8,3-format) för den nya Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3332">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3333">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3333">Return Values</span></span>

- <span data-ttu-id="5b3fc-3334">**FX_SUCCESS** (0x00) filen har skapats.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3334">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="5b3fc-3335">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3335">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3336">Den angivna filen för **FX_ALREADY_CREATED** (0x0B) finns redan.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3336">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="5b3fc-3337">**FX_NO_MORE_SPACE** (0X0a) inga fler kluster är tillgängliga i mediet för den nya fil posten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3337">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="5b3fc-3338">Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3338">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="5b3fc-3339">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3339">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3340">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3340">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="5b3fc-3341">**FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3341">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="5b3fc-3342">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3342">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3343">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3343">Allowed From</span></span>

<span data-ttu-id="5b3fc-3344">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3344">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3345">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3345">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3346">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3346">See Also</span></span>

- <span data-ttu-id="5b3fc-3347">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3347">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3348">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3348">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3349">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3349">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3350">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3350">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3351">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3351">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3352">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3352">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3353">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3353">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3354">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3354">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3355">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3355">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3356">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3356">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3357">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3357">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3358">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3358">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3359">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3359">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3360">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3360">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3361">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3361">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3362">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3362">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3363">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3363">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3364">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3364">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3365">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3365">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3366">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3366">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3367">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3367">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3368">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3368">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3369">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3369">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3370">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3370">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-3371">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3371">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-3372">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3372">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="5b3fc-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3373">fx_unicode_file_rename</span></span>

<span data-ttu-id="5b3fc-3374">Byter namn på en fil med Unicode-sträng</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3374">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3375">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3375">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3376">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3376">Description</span></span>

<span data-ttu-id="5b3fc-3377">Den här tjänsten ändrar ett Unicode-namngivet fil namn till ett angivet nytt Unicode-namn i den aktuella standard katalogen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3377">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="5b3fc-3378">Unicode-namnets parametrar får inte innehålla Sök vägs information.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3378">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3379">*Den här tjänsten stöds inte på exFAT media.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3379">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3380">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3380">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3381">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3381">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3382">**old_unicode_name**: pekar mot Unicode-namnet för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3382">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="5b3fc-3383">**old_unicode_name_length**: längden på det aktuella Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3383">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3384">**new_unicode_name**: pekar mot det nya Unicode-filnamn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3384">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="5b3fc-3385">**new_unicode_name_length**: längden på det nya Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3385">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3386">**new_short_name**: pekare till målet för kort namn (8,3-format) för den omdöpta Unicode-filen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3386">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3387">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3387">Return Values</span></span>


- <span data-ttu-id="5b3fc-3388">**FX_SUCCESS** (0x00) media är öppna.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3388">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="5b3fc-3389">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3389">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3390">**FX_ALREADY_CREATED** (0x0B) det angivna fil namnet finns redan.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3390">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="5b3fc-3391">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3391">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3392">**FX_PTR_ERROR** (0X18) en eller flera pekare är null.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3392">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="5b3fc-3393">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3393">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="5b3fc-3394">**FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3394">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3395">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3395">Allowed From</span></span>

<span data-ttu-id="5b3fc-3396">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3396">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3397">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3397">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3398">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3398">See Also</span></span>

- <span data-ttu-id="5b3fc-3399">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3399">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3400">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3400">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3401">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3401">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3402">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3402">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3403">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3403">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3404">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3404">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3405">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3405">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3406">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3406">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3407">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3407">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3408">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3408">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3409">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3409">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3410">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3410">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3411">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3411">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3412">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3412">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3413">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3413">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3414">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3414">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3415">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3415">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3416">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3416">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3417">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3417">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3418">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3418">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3419">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3419">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3420">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3420">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3421">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3421">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3422">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3422">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-3423">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3423">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-3424">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3424">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="5b3fc-3425">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3425">fx_unicode_length_get</span></span>

<span data-ttu-id="5b3fc-3426">Hämtar längden på Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3426">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3427">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3427">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3428">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3428">Description</span></span>

<span data-ttu-id="5b3fc-3429">Den här tjänsten fastställer längden på det angivna Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3429">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="5b3fc-3430">Ett Unicode-tecken representeras av två byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3430">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="5b3fc-3431">Ett Unicode-namn är en serie med två byte Unicode-tecken som avslut ATS av två NULL-byte (två byte 0-värde).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3431">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3432">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3432">Input Parameters</span></span>

<span data-ttu-id="5b3fc-3433">**unicode_name**: pekar mot Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3433">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3434">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3434">Return Values</span></span>

<span data-ttu-id="5b3fc-3435">**längd**: längden på Unicode-namn (antal Unicode-tecken i namnet).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3435">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3436">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3436">Allowed From</span></span>

<span data-ttu-id="5b3fc-3437">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3438">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3438">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3439">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3439">See Also</span></span>

- <span data-ttu-id="5b3fc-3440">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3440">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3441">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3441">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3442">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3442">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3443">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3443">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3444">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3444">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3445">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3445">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3446">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3446">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3447">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3447">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3448">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3448">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3449">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3449">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3450">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3450">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3451">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3451">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3452">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3452">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3453">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3453">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3454">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3454">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3455">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3455">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3456">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3456">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3457">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3457">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3458">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3458">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3459">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3459">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3460">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3460">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3461">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3461">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3462">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3462">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3463">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3463">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-3464">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3464">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-3465">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3465">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-3466">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3466">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="5b3fc-3467">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3467">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="5b3fc-3468">Hämtar längden på Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3468">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3469">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3469">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3470">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3470">Description</span></span>

<span data-ttu-id="5b3fc-3471">Den här tjänsten hämtar längden på det angivna Unicode-namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3471">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="5b3fc-3472">Ett Unicode-tecken representeras av två byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3472">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="5b3fc-3473">Ett Unicode-namn är en serie twobyte Unicode-tecken som avslut ATS av två NULL-byte (två byte 0-värde).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3473">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3474">*Den här tjänsten är identisk med **fx_unicode_length_get ()** , förutom att anroparen skickar i storleken på den **unicode_name** bufferten, inklusive de två null-tecknen.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3474">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3475">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3475">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3476">**unicode_name**: pekar mot Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3476">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3477">**buffer_length**: storlek på Unicode-namnsuffix.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3477">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3478">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3478">Return Values</span></span>

<span data-ttu-id="5b3fc-3479">**längd**: längden på Unicode-namn (antal Unicode-tecken i namnet).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3479">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3480">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3480">Allowed From</span></span>

<span data-ttu-id="5b3fc-3481">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3481">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3482">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3482">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3483">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3483">See Also</span></span>

- <span data-ttu-id="5b3fc-3484">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3484">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3485">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3485">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3486">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3486">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3487">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3487">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3488">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3488">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3489">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3489">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3490">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3490">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3491">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3491">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3492">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3492">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3493">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3493">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3494">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3494">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3495">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3495">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3496">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3496">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3497">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3497">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3498">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3498">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3499">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3499">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3500">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3500">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3501">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3501">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3502">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3502">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3503">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3503">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3504">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3504">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3505">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3505">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3506">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3506">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3507">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3507">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-3508">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3508">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-3509">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3509">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-3510">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3510">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="5b3fc-3511">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3511">fx_unicode_name_get</span></span>

<span data-ttu-id="5b3fc-3512">Hämtar Unicode-namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3512">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3513">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3513">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3514">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3514">Description</span></span>

<span data-ttu-id="5b3fc-3515">Den här tjänsten hämtar det Unicode-namn som är associerat med det angivna korta namnet (8,3-formatet) i den aktuella standard katalogen – ingen Sök vägs information tillåts i den korta namn parametern.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3515">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="5b3fc-3516">Om det lyckas returneras det Unicode-namn som är associerat med det korta namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3516">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3517">*Den här tjänsten kan användas för att hämta Unicode-namn för både filer och under kataloger.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3517">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3518">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3518">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3519">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3519">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3520">**short_name** Pekare till kort namn (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3520">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="5b3fc-3521">**destination_unicode_name**: pekar mot målet för det Unicode-namn som är associerat med det angivna korta namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3521">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="5b3fc-3522">**destination_unicode_length**: pekare till returnerad Unicode-namn längd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3522">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3523">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3523">Return Values</span></span>

- <span data-ttu-id="5b3fc-3524">**FX_SUCCESS** (0X00) lyckades hämtning av Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3524">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="5b3fc-3525">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3525">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="5b3fc-3526">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3526">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-3527">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3527">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3528">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3528">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3529">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet eller så är storleken på Unicode-målet för liten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3529">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="5b3fc-3530">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3530">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-3531">**FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3531">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="5b3fc-3532">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3532">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3533">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3533">Allowed From</span></span>

<span data-ttu-id="5b3fc-3534">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3535">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3535">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3536">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3536">See Also</span></span>

- <span data-ttu-id="5b3fc-3537">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3537">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3538">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3538">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3539">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3539">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3540">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3540">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3541">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3541">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3542">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3542">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3543">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3543">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3544">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3544">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3545">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3545">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3546">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3546">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3547">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3547">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3548">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3548">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3549">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3549">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3550">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3550">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3551">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3551">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3552">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3552">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3553">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3553">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3554">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3554">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3555">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3555">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3556">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3556">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3557">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3557">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3558">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3558">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3559">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3559">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3560">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3560">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-3561">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3561">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-3562">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3562">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="5b3fc-3563">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3563">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="5b3fc-3564">Hämtar Unicode-namn från kort namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3564">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3565">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3565">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="5b3fc-3566">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3566">Description</span></span>

<span data-ttu-id="5b3fc-3567">Den här tjänsten hämtar det Unicode-namn som är associerat med det angivna korta namnet (8,3-formatet) i den aktuella standard katalogen – ingen Sök vägs information tillåts i den korta namn parametern.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3567">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="5b3fc-3568">Om det lyckas returneras det Unicode-namn som är associerat med det korta namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3568">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3569">\* Den här tjänsten är identisk med \***fx_unicode_name_get**_, förutom att anroparen tillhandahåller storleken på målets Unicode-buffert som indatamängds argument. Detta gör att tjänsten kan garantera att den inte kommer att skriva över målets Unicode-buffert_</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3569">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3570">*Den här tjänsten kan användas för att hämta Unicode-namn för både filer och under kataloger.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3570">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3571">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3571">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3572">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3572">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3573">**short_name**: pekar mot kort namn (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3573">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="5b3fc-3574">**destination_unicode_name**: pekar mot målet för det Unicode-namn som är associerat med det angivna korta namnet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3574">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="5b3fc-3575">**destination_unicode_length**: pekare till returnerad Unicode-namn längd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3575">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="5b3fc-3576">**unicode_name_buffer_length**: storleken på Unicode-databufferten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3576">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="5b3fc-3577">Obs! en NULL-begränsare krävs, vilket innebär en extra byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3577">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3578">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3578">Return Values</span></span>

- <span data-ttu-id="5b3fc-3579">**FX_SUCCESS** (0X00) lyckades hämtning av Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3579">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="5b3fc-3580">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3580">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="5b3fc-3581">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3581">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-3582">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3582">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3583">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3583">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3584">**FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet eller så är storleken på Unicode-målet för liten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3584">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="5b3fc-3585">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3585">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-3586">**FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3586">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="5b3fc-3587">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3587">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3588">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3588">Allowed From</span></span>

<span data-ttu-id="5b3fc-3589">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3590">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3590">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3591">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3591">See Also</span></span>

- <span data-ttu-id="5b3fc-3592">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3592">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3593">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3593">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3594">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3594">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3595">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3595">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3596">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3596">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3597">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3597">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3598">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3598">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3599">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3599">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3600">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3600">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3601">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3601">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3602">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3602">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3603">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3603">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3604">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3604">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3605">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3605">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3606">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3606">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3607">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3607">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3608">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3608">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3609">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3609">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3610">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3610">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3611">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3611">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3612">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3612">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3613">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3613">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3614">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3614">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3615">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3615">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-3616">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3616">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-3617">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3617">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="5b3fc-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3618">fx_unicode_short_name_get</span></span>

<span data-ttu-id="5b3fc-3619">Hämtar kort namn från Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3619">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3620">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3620">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="5b3fc-3621">Den här tjänsten hämtar det korta namnet (8,3-formatet) som är associerat med Unicode-namnet i den aktuella standard katalogen, ingen Sök vägs information tillåts i Unicode-namn parametern.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3621">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="5b3fc-3622">Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3622">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3623">*Den här tjänsten kan användas för att hämta korta namn för både filer och under kataloger.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3623">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3624">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3624">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3625">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3625">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3626">**source_unicode_name**: pekar mot Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3626">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3627">**source_unicode_length**: längden på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3627">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3628">**destination_short_name**: pekare till målet för kort namnet (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3628">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="5b3fc-3629">Det måste vara minst 13 byte stort.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3629">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3630">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3630">Return Values</span></span>

- <span data-ttu-id="5b3fc-3631">**FX_SUCCESS** (0x00) kort namn hämtning (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3631">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="5b3fc-3632">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3632">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="5b3fc-3633">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3633">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="5b3fc-3634">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3634">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3635">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3635">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3636">Det gick inte att hitta **FX_NOT_FOUND** (0X04) Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3636">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="5b3fc-3637">Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3637">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="5b3fc-3638">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3638">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-3639">**FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3639">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="5b3fc-3640">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3640">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3641">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3641">Allowed From</span></span>

<span data-ttu-id="5b3fc-3642">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3642">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3643">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3643">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3644">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3644">See Also</span></span>

- <span data-ttu-id="5b3fc-3645">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3645">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3646">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3646">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3647">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3648">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3648">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3649">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3649">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3650">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3650">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3651">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3651">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3652">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3652">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3653">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3653">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3654">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3654">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3655">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3655">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3656">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3656">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3657">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3657">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3658">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3658">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3659">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3659">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3660">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3660">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3661">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3661">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3662">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3662">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3663">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3663">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3664">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3664">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3665">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3665">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3666">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3666">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3667">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3667">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3668">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3668">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-3669">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3669">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-3670">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3670">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="5b3fc-3671">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3671">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="5b3fc-3672">Hämtar kort namn från Unicode-namn</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3672">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="5b3fc-3673">Prototyp</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3673">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="5b3fc-3674">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3674">Description</span></span>

<span data-ttu-id="5b3fc-3675">Den här tjänsten hämtar det korta namnet (8,3-formatet) som är associerat med Unicode-namnet i den aktuella standard katalogen, ingen Sök vägs information tillåts i Unicode-namn parametern.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3675">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="5b3fc-3676">Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3676">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3fc-3677">*Den här tjänsten är identisk med **fx_unicode_short_name_get ()**, förutom att anroparen tillhandahåller storleken på målcachen som ett indataargument. Detta gör att tjänsten garanterar det korta namnet inte överskrider målcachen.*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3677">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="5b3fc-3678">*Den här tjänsten kan användas för att hämta korta namn för både filer och under kataloger*</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3678">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5b3fc-3679">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3679">Input Parameters</span></span>

- <span data-ttu-id="5b3fc-3680">**media_ptr**: pekare till Media Control Block.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3680">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="5b3fc-3681">**source_unicode_name**: pekar mot Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3681">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3682">**source_unicode_length**: längden på Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3682">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="5b3fc-3683">**destination_short_name**: pekare till målet för kort namnet (8,3-format).</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3683">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="5b3fc-3684">Det måste vara minst 13 byte stort.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3684">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="5b3fc-3685">**short_name_buffer_length**: storleken på måldomänkontrollanten.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3685">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="5b3fc-3686">Buffertstorleken måste vara minst 14 byte.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3686">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="5b3fc-3687">Retur värden</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3687">Return Values</span></span>

- <span data-ttu-id="5b3fc-3688">**FX_SUCCESS** (0x00) kort namn hämtning (0X00) lyckades.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3688">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="5b3fc-3689">**FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3689">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="5b3fc-3690">**FX_FILE_CORRUPT** -filen (0x08) är skadad</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3690">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="5b3fc-3691">**FX_IO_ERROR** (0X90) driv rutin I/O-fel.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3691">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="5b3fc-3692">**FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="5b3fc-3693">Det gick inte att hitta **FX_NOT_FOUND** (0X04) Unicode-namn.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3693">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="5b3fc-3694">Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3694">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="5b3fc-3695">**FX_SECTOR_INVALID** (0X89) ogiltig sektor.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3695">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="5b3fc-3696">**FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3696">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="5b3fc-3697">**FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3697">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5b3fc-3698">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3698">Allowed From</span></span>

<span data-ttu-id="5b3fc-3699">Konversation</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3699">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5b3fc-3700">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3700">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5b3fc-3701">Se även</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3701">See Also</span></span>

- <span data-ttu-id="5b3fc-3702">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3702">fx_file_allocate</span></span>
- <span data-ttu-id="5b3fc-3703">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3703">fx_file_attributes_read</span></span>
- <span data-ttu-id="5b3fc-3704">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3704">fx_file_attributes_set</span></span>
- <span data-ttu-id="5b3fc-3705">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3705">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3706">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3706">fx_file_close</span></span>
- <span data-ttu-id="5b3fc-3707">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3707">fx_file_create</span></span>
- <span data-ttu-id="5b3fc-3708">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3708">fx_file_date_time_set</span></span>
- <span data-ttu-id="5b3fc-3709">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3709">fx_file_delete</span></span>
- <span data-ttu-id="5b3fc-3710">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3710">fx_file_extended_allocate</span></span>
- <span data-ttu-id="5b3fc-3711">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3711">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="5b3fc-3712">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3712">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3713">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3713">fx_file_extended_seek</span></span>
- <span data-ttu-id="5b3fc-3714">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3714">fx_file_extended_truncate</span></span>
- <span data-ttu-id="5b3fc-3715">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3715">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3716">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3716">fx_file_open</span></span>
- <span data-ttu-id="5b3fc-3717">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3717">fx_file_read</span></span>
- <span data-ttu-id="5b3fc-3718">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3718">fx_file_relative_seek</span></span>
- <span data-ttu-id="5b3fc-3719">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3719">fx_file_rename</span></span>
- <span data-ttu-id="5b3fc-3720">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3720">fx_file_seek</span></span>
- <span data-ttu-id="5b3fc-3721">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3721">fx_file_truncate</span></span>
- <span data-ttu-id="5b3fc-3722">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3722">fx_file_truncate_release</span></span>
- <span data-ttu-id="5b3fc-3723">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3723">fx_file_write</span></span>
- <span data-ttu-id="5b3fc-3724">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3724">fx_file_write_notify_set</span></span>
- <span data-ttu-id="5b3fc-3725">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3725">fx_unicode_file_create</span></span>
- <span data-ttu-id="5b3fc-3726">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3726">fx_unicode_file_rename</span></span>
- <span data-ttu-id="5b3fc-3727">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3727">fx_unicode_name_get</span></span>
- <span data-ttu-id="5b3fc-3728">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="5b3fc-3728">fx_unicode_short_name_get</span></span>
