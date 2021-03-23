---
title: Kapitel 5-I/O-drivrutiner för Azure återställnings tider FileX
description: Det här kapitlet innehåller en beskrivning av I/O-drivrutiner för Azure återställnings tider FileX och är utformat för att hjälpa utvecklare att skriva programspecifika driv rutiner.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b44822b9d8f16208cf470a84013be5a5ff833325
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826538"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a><span data-ttu-id="84543-103">Kapitel 5-I/O-drivrutiner för Azure återställnings tider FileX</span><span class="sxs-lookup"><span data-stu-id="84543-103">Chapter 5 - I/O Drivers for Azure RTOS FileX</span></span>

<span data-ttu-id="84543-104">Det här kapitlet innehåller en beskrivning av I/O-drivrutiner för Azure återställnings tider FileX och är utformat för att hjälpa utvecklare att skriva programspecifika driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="84543-104">This chapter contains a description of I/O drivers for Azure RTOS FileX and is designed to help developers write application-specific drivers.</span></span>

## <a name="io-driver-introduction"></a><span data-ttu-id="84543-105">Introduktion till I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="84543-105">I/O Driver Introduction</span></span>

<span data-ttu-id="84543-106">FileX stöder flera medie enheter.</span><span class="sxs-lookup"><span data-stu-id="84543-106">FileX supports multiple media devices.</span></span> <span data-ttu-id="84543-107">FX_MEDIAs strukturen definierar allt som krävs för att hantera en Media enhet.</span><span class="sxs-lookup"><span data-stu-id="84543-107">The FX_MEDIA structure defines everything required to manage a media device.</span></span> <span data-ttu-id="84543-108">Den här strukturen innehåller all medie information, inklusive den leverantörsspecifika I/O-drivrutinen och tillhör ande parametrar för att skicka information och status mellan driv rutins-och FileX.</span><span class="sxs-lookup"><span data-stu-id="84543-108">This structure contains all media information, including the media-specific I/O driver and associated parameters for passing information and status between the driver and FileX.</span></span> <span data-ttu-id="84543-109">I de flesta system finns det en unik I/O-drivrutin för varje FileX medie instans.</span><span class="sxs-lookup"><span data-stu-id="84543-109">In most systems, there is a unique I/O driver for each FileX media instance.</span></span>

## <a name="io-driver-entry"></a><span data-ttu-id="84543-110">Post för I/O-drivrutin</span><span class="sxs-lookup"><span data-stu-id="84543-110">I/O Driver Entry</span></span>

<span data-ttu-id="84543-111">Varje FileX I/O-drivrutin har en enda post-funktion som definieras av ***fx_media_open*** tjänst anropet.</span><span class="sxs-lookup"><span data-stu-id="84543-111">Each FileX I/O driver has a single entry function that is defined by the ***fx_media_open*** service call.</span></span> <span data-ttu-id="84543-112">Funktionen driv rutins post har följande format:</span><span class="sxs-lookup"><span data-stu-id="84543-112">The driver entry function has the following format:</span></span>

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

<span data-ttu-id="84543-113">FileX anropar funktionen I/O-drivrutin för att begära all fysisk medie åtkomst, inklusive initiering och start sektor läsning.</span><span class="sxs-lookup"><span data-stu-id="84543-113">FileX calls the I/O driver entry function to request all physical media access, including initialization and boot sector reading.</span></span> <span data-ttu-id="84543-114">Begär Anden som görs till driv rutinen görs i tur och ordning. t. ex. FileX väntar på att den aktuella begäran ska slutföras innan en annan begäran skickas.</span><span class="sxs-lookup"><span data-stu-id="84543-114">Requests made to the driver are done sequentially; i.e., FileX waits for the current request to complete before another request is sent.</span></span>

## <a name="io-driver-requests"></a><span data-ttu-id="84543-115">I/O-drivrutin begär Anden</span><span class="sxs-lookup"><span data-stu-id="84543-115">I/O Driver Requests</span></span>

<span data-ttu-id="84543-116">Eftersom varje I/O-drivrutin har en enda post-funktion, gör FileX vissa förfrågningar via medie kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="84543-116">Because each I/O driver has a single entry function, FileX makes specific requests through the media control block.</span></span> <span data-ttu-id="84543-117">Mer specifikt används  **fx_media_driver_request** medlem i **FX_MEDIA** för att ange den exakta driv rutins förfrågan.</span><span class="sxs-lookup"><span data-stu-id="84543-117">Specifically, the  **fx_media_driver_request** member of **FX_MEDIA** is used to specify the exact driver request.</span></span> <span data-ttu-id="84543-118">I/O-drivrutinen meddelar att begäran lyckades eller misslyckades via **fx_media_driver_status** medlem i **FX_MEDIA**.</span><span class="sxs-lookup"><span data-stu-id="84543-118">The I/O driver communicates the success or failure of the request through the **fx_media_driver_status** member of **FX_MEDIA**.</span></span> <span data-ttu-id="84543-119">Om begäran om driv rutin har lyckats placeras **FX_SUCCESS** i det här fältet innan driv rutinen returneras.</span><span class="sxs-lookup"><span data-stu-id="84543-119">If the driver request was successful, **FX_SUCCESS** is placed in this field before the driver returns.</span></span> <span data-ttu-id="84543-120">Annars placeras FX_IO_ERROR i det här fältet om ett fel upptäcks.</span><span class="sxs-lookup"><span data-stu-id="84543-120">Otherwise, if an error is detected, FX_IO_ERROR is placed in this field.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="84543-121">Driv rutins initiering</span><span class="sxs-lookup"><span data-stu-id="84543-121">Driver Initialization</span></span>

<span data-ttu-id="84543-122">Även om den faktiska initieringen av driv rutinen är programspecifik, består det vanligt vis av data struktur initiering och eventuellt preliminär maskin varu initiering.</span><span class="sxs-lookup"><span data-stu-id="84543-122">Although the actual driver initialization processing is application specific, it usually consists of data structure initialization and possibly some preliminary hardware initialization.</span></span> <span data-ttu-id="84543-123">Den här begäran är den första som görs av FileX och görs inifrån den fx_media_open tjänsten.</span><span class="sxs-lookup"><span data-stu-id="84543-123">This request is the first made by FileX and is done from within the fx_media_open service.</span></span>

<span data-ttu-id="84543-124">Om medie Skriv skyddet identifieras ska driv rutinen fx_media_driver_write_protect medlem i FX_MEDIA anges till FX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="84543-124">If media write protection is detected, the driver fx_media_driver_write_protect member of FX_MEDIA should be set to FX_TRUE.</span></span>

<span data-ttu-id="84543-125">Följande FX_MEDIA-medlemmar används för begäran om att initiera I/O-drivrutinen:</span><span class="sxs-lookup"><span data-stu-id="84543-125">The following FX_MEDIA members are used for the I/O driver initialization request:</span></span>

|<span data-ttu-id="84543-126">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-126">FX_MEDIA member</span></span>|<span data-ttu-id="84543-127">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-127">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-128">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-128">fx_media_driver_request</span></span>|<span data-ttu-id="84543-129">FX_DRIVER_INIT</span><span class="sxs-lookup"><span data-stu-id="84543-129">FX_DRIVER_INIT</span></span>|

<span data-ttu-id="84543-130">FileX tillhandahåller en mekanism för att informera program driv rutinen när sektorer inte längre används.</span><span class="sxs-lookup"><span data-stu-id="84543-130">FileX provides a mechanism to inform the application driver when sectors are no longer being used.</span></span> <span data-ttu-id="84543-131">Detta är särskilt användbart för minnes hanterare i FLASH som måste hantera alla inaktuella logiska sektorer som är kopplade till FLASH.</span><span class="sxs-lookup"><span data-stu-id="84543-131">This is especially useful for FLASH memory managers that must manage all in-use logical sectors mapped to the FLASH.</span></span>

<span data-ttu-id="84543-132">Om det krävs ett sådant meddelande om kostnads fria sektorer, ställer program driv rutinen bara in *fx_media_driver_free_sector_update* fältet i den associerade **FX_MEDIAs** strukturen för att **FX_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="84543-132">If such notification of free sectors is required, the application driver simply sets the *fx_media_driver_free_sector_update* field in the associated **FX_MEDIA** structure to **FX_TRUE**.</span></span> <span data-ttu-id="84543-133">Efter den här inställningen gör FileX ett **_FX_DRIVER_RELEASE_SECTORS_** I/O-drivrutin som anger när en eller flera efterföljande sektorer blir kostnads fria.</span><span class="sxs-lookup"><span data-stu-id="84543-133">After set, FileX makes a **_FX_DRIVER_RELEASE_SECTORS_** I/O driver call indicating when one or more consecutive sectors becomes free.</span></span>

### <a name="boot-sector-read"></a><span data-ttu-id="84543-134">Läsning av start sektor</span><span class="sxs-lookup"><span data-stu-id="84543-134">Boot Sector Read</span></span>

<span data-ttu-id="84543-135">I stället för att använda en vanlig Read-begäran, gör FileX en särskild begäran om att läsa mediets start sektor.</span><span class="sxs-lookup"><span data-stu-id="84543-135">Instead of using a standard read request, FileX makes a specific request to read the media's boot sector.</span></span> <span data-ttu-id="84543-136">Följande **FX_MEDIA** -medlemmar används för i/O-drivrutinens start sektor Read-begäran:</span><span class="sxs-lookup"><span data-stu-id="84543-136">The following **FX_MEDIA** members are used for the I/O driver boot sector read request:</span></span>

|<span data-ttu-id="84543-137">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-137">FX_MEDIA member</span></span>|<span data-ttu-id="84543-138">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-138">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-139">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-139">fx_media_driver_request</span></span>| <span data-ttu-id="84543-140">FX_DRIVER_BOOT_READ</span><span class="sxs-lookup"><span data-stu-id="84543-140">FX_DRIVER_BOOT_READ</span></span>|
|<span data-ttu-id="84543-141">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="84543-141">fx_media_driver_buffer</span></span>| <span data-ttu-id="84543-142">Mål adress för start sektor.</span><span class="sxs-lookup"><span data-stu-id="84543-142">Address of destination for boot sector.</span></span>|

### <a name="boot-sector-write"></a><span data-ttu-id="84543-143">Skriv start sektor</span><span class="sxs-lookup"><span data-stu-id="84543-143">Boot Sector Write</span></span>

<span data-ttu-id="84543-144">I stället för att använda en vanlig skrivbegäran, gör FileX en särskild begäran om att skriva mediets start sektor.</span><span class="sxs-lookup"><span data-stu-id="84543-144">Instead of using a standard write request, FileX makes a specific request to write the media's boot sector.</span></span> <span data-ttu-id="84543-145">Följande **FX_MEDIA** -medlemmar används för i/O-drivrutinens start sektor Skriv förfrågan:</span><span class="sxs-lookup"><span data-stu-id="84543-145">The following **FX_MEDIA** members are used for the I/O driver boot sector write request:</span></span>

|<span data-ttu-id="84543-146">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-146">FX_MEDIA member</span></span>|<span data-ttu-id="84543-147">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-147">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-148">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-148">fx_media_driver_request</span></span>| <span data-ttu-id="84543-149">FX_DRIVER_BOOT_WRITE</span><span class="sxs-lookup"><span data-stu-id="84543-149">FX_DRIVER_BOOT_WRITE</span></span>|
|<span data-ttu-id="84543-150">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="84543-150">fx_media_driver_buffer</span></span>| <span data-ttu-id="84543-151">Källans adress för start sektorn.</span><span class="sxs-lookup"><span data-stu-id="84543-151">Address of source for boot sector.</span></span>|

### <a name="sector-read"></a><span data-ttu-id="84543-152">Läs sektor</span><span class="sxs-lookup"><span data-stu-id="84543-152">Sector Read</span></span>

<span data-ttu-id="84543-153">FileX läser en eller flera sektorer i minnet genom att utfärda en Read-begäran till I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="84543-153">FileX reads one or more sectors into memory by issuing a read request to the I/O driver.</span></span> <span data-ttu-id="84543-154">Följande **FX_MEDIA** -medlemmar används för i/O-drivrutinen Read-begäran:</span><span class="sxs-lookup"><span data-stu-id="84543-154">The following **FX_MEDIA** members are used for the I/O driver read request:</span></span>

|<span data-ttu-id="84543-155">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-155">FX_MEDIA member</span></span>|<span data-ttu-id="84543-156">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-156">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-157">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-157">fx_media_driver_request</span></span>| <span data-ttu-id="84543-158">FX_DRIVER_READ</span><span class="sxs-lookup"><span data-stu-id="84543-158">FX_DRIVER_READ</span></span>|
|<span data-ttu-id="84543-159">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="84543-159">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="84543-160">Logisk sektor att läsa</span><span class="sxs-lookup"><span data-stu-id="84543-160">Logical sector to read</span></span>|
|<span data-ttu-id="84543-161">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="84543-161">fx_media_driver_sectors</span></span>|<span data-ttu-id="84543-162">Antal sektorer att läsa</span><span class="sxs-lookup"><span data-stu-id="84543-162">Number of sectors to read</span></span>|
|<span data-ttu-id="84543-163">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="84543-163">fx_media_driver_buffer</span></span>|<span data-ttu-id="84543-164">Destinations-buffert för sektor (er) Läs</span><span class="sxs-lookup"><span data-stu-id="84543-164">Destination buffer for sector(s) read</span></span>|
|<span data-ttu-id="84543-165">fx_media_driver_data_sector_read</span><span class="sxs-lookup"><span data-stu-id="84543-165">fx_media_driver_data_sector_read</span></span>|<span data-ttu-id="84543-166">Ange till FX_TRUE om en fil data sektor begärs.</span><span class="sxs-lookup"><span data-stu-id="84543-166">Set to FX_TRUE if a file data sector is requested.</span></span> <span data-ttu-id="84543-167">I annat fall FX_FALSE om en system sektor (FAT eller katalog sektor) begärs.</span><span class="sxs-lookup"><span data-stu-id="84543-167">Otherwise, FX_FALSE if a system sector (FAT or directory sector) is requested.</span></span>|
|<span data-ttu-id="84543-168">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="84543-168">fx_media_driver_sector_type</span></span>|<span data-ttu-id="84543-169">Definierar den explicita typ av sektor som begärs enligt följande:</span><span class="sxs-lookup"><span data-stu-id="84543-169">Defines the explicit type of sector requested, as follows:</span></span><br /><span data-ttu-id="84543-170">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="84543-170">FX_FAT_SECTOR (2)</span></span><br /><span data-ttu-id="84543-171">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="84543-171">FX_DIRECTORY_SECTOR (3)</span></span><br /><span data-ttu-id="84543-172">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="84543-172">FX_DATA_SECTOR (4)</span></span>|

### <a name="sector-write"></a><span data-ttu-id="84543-173">Sektor skrivning</span><span class="sxs-lookup"><span data-stu-id="84543-173">Sector Write</span></span>

<span data-ttu-id="84543-174">FileX skriver en eller flera sektorer till de fysiska medierna genom att utfärda en skrivbegäran till I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="84543-174">FileX writes one or more sectors to the physical media by issuing a write request to the I/O driver.</span></span> <span data-ttu-id="84543-175">Följande FX_MEDIA-medlemmar används för i/O-drivrutinen Skriv förfrågan:</span><span class="sxs-lookup"><span data-stu-id="84543-175">The following FX_MEDIA members are used for the I/O driver write request:</span></span>

|<span data-ttu-id="84543-176">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-176">FX_MEDIA member</span></span>| <span data-ttu-id="84543-177">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-177">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-178">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-178">fx_media_driver_request</span></span>|<span data-ttu-id="84543-179">FX_DRIVER_WRITE</span><span class="sxs-lookup"><span data-stu-id="84543-179">FX_DRIVER_WRITE</span></span>|
|<span data-ttu-id="84543-180">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="84543-180">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="84543-181">Logisk sektor att skriva</span><span class="sxs-lookup"><span data-stu-id="84543-181">Logical sector to write</span></span>|
|<span data-ttu-id="84543-182">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="84543-182">fx_media_driver_sectors</span></span>|<span data-ttu-id="84543-183">Antal sektorer att skriva</span><span class="sxs-lookup"><span data-stu-id="84543-183">Number of sectors to write</span></span>|
|<span data-ttu-id="84543-184">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="84543-184">fx_media_driver_buffer</span></span>|<span data-ttu-id="84543-185">Source buffer för sektor (er) att skriva</span><span class="sxs-lookup"><span data-stu-id="84543-185">Source buffer for sector(s) to write</span></span>|
|<span data-ttu-id="84543-186">fx_media_driver_system_write</span><span class="sxs-lookup"><span data-stu-id="84543-186">fx_media_driver_system_write</span></span>| <span data-ttu-id="84543-187">Ange till FX_TRUE om en system sektor begärs (FAT eller katalog sektor).</span><span class="sxs-lookup"><span data-stu-id="84543-187">Set to FX_TRUE if a system sector is requested (FAT or directory sector).</span></span> <span data-ttu-id="84543-188">Annars FX_FALSE om en fil data sektor begärs.</span><span class="sxs-lookup"><span data-stu-id="84543-188">Otherwise, FX_FALSE if a file data sector is requested.</span></span>|
|<span data-ttu-id="84543-189">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="84543-189">fx_media_driver_sector_type</span></span>|<span data-ttu-id="84543-190">Definierar den explicita typ av sektor som begärs enligt följande:</span><span class="sxs-lookup"><span data-stu-id="84543-190">Defines the explicit type of sector requested, as follows:</span></span>
<span data-ttu-id="84543-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4) |</span><span class="sxs-lookup"><span data-stu-id="84543-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span></span>

### <a name="driver-flush"></a><span data-ttu-id="84543-192">Driv rutins tömning</span><span class="sxs-lookup"><span data-stu-id="84543-192">Driver Flush</span></span>

<span data-ttu-id="84543-193">FileX tömmer alla sektorer som för närvarande finns i driv Rutinens sektor-cache till det fysiska mediet genom att skicka en begäran om tömning till I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="84543-193">FileX flushes all sectors currently in the driver's sector cache to the physical media by issuing a flush request to the I/O driver.</span></span> <span data-ttu-id="84543-194">Om driv rutinen inte cachelagrar sektorer behöver denna begäran naturligtvis ingen driv rutins bearbetning.</span><span class="sxs-lookup"><span data-stu-id="84543-194">Of course, if the driver is not caching sectors, this request requires no driver processing.</span></span> <span data-ttu-id="84543-195">Följande FX_MEDIA-medlemmar används för i/O-drivrutinen tömnings förfrågan:</span><span class="sxs-lookup"><span data-stu-id="84543-195">The following FX_MEDIA members are used for the I/O driver flush request:</span></span>

|<span data-ttu-id="84543-196">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-196">FX_MEDIA member</span></span>| <span data-ttu-id="84543-197">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-197">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-198">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-198">fx_media_driver_request</span></span>|<span data-ttu-id="84543-199">FX_DRIVER_FLUSH</span><span class="sxs-lookup"><span data-stu-id="84543-199">FX_DRIVER_FLUSH</span></span>|

### <a name="driver-abort"></a><span data-ttu-id="84543-200">Avbryt driv rutin</span><span class="sxs-lookup"><span data-stu-id="84543-200">Driver Abort</span></span>

<span data-ttu-id="84543-201">FileX informerar driv rutinen för att avbryta all ytterligare fysisk I/O-aktivitet med det fysiska mediet genom att utfärda en abort-begäran till I/O-drivrutinen.</span><span class="sxs-lookup"><span data-stu-id="84543-201">FileX informs the driver to abort all further physical I/O activity with the physical media by issuing an abort request to the I/O driver.</span></span> <span data-ttu-id="84543-202">Driv rutinen ska inte utföra några I/O igen förrän den har startats om.</span><span class="sxs-lookup"><span data-stu-id="84543-202">The driver should not perform any I/O again until it is re-initialized.</span></span> <span data-ttu-id="84543-203">Följande FX_MEDIA-medlemmar används för i/O-drivrutinens abort-begäran:</span><span class="sxs-lookup"><span data-stu-id="84543-203">The following FX_MEDIA members are used for the I/O driver abort request:</span></span>

|<span data-ttu-id="84543-204">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-204">FX_MEDIA member</span></span>| <span data-ttu-id="84543-205">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-205">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-206">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-206">fx_media_driver_request</span></span>| <span data-ttu-id="84543-207">FX_DRIVER_ABORT</span><span class="sxs-lookup"><span data-stu-id="84543-207">FX_DRIVER_ABORT</span></span>|

### <a name="release-sectors"></a><span data-ttu-id="84543-208">Versions sektorer</span><span class="sxs-lookup"><span data-stu-id="84543-208">Release Sectors</span></span>

<span data-ttu-id="84543-209">Om den tidigare valdes av driv rutinen under initieringen informerar FileX driv rutinen när en eller flera sektorer i följd blir kostnads fria.</span><span class="sxs-lookup"><span data-stu-id="84543-209">If previously selected by the driver during initialization, FileX informs the driver whenever one or more consecutive sectors become free.</span></span> <span data-ttu-id="84543-210">Om driv rutinen faktiskt är en FLASH Manager kan du använda den här informationen för att berätta för FLASH Manager att dessa sektorer inte längre behövs.</span><span class="sxs-lookup"><span data-stu-id="84543-210">If the driver is actually a FLASH manager, this information can be used to tell the FLASH manager that these sectors are no longer needed.</span></span> <span data-ttu-id="84543-211">Följande **FX_MEDIAs** medlemmar används för begäran om i/O-release-release-sektorn:</span><span class="sxs-lookup"><span data-stu-id="84543-211">The following **FX_MEDIA** members are used for the I/O release sectors request:</span></span>

|<span data-ttu-id="84543-212">FX_MEDIA medlem</span><span class="sxs-lookup"><span data-stu-id="84543-212">FX_MEDIA member</span></span>| <span data-ttu-id="84543-213">Innebörd</span><span class="sxs-lookup"><span data-stu-id="84543-213">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="84543-214">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="84543-214">fx_media_driver_request</span></span>|<span data-ttu-id="84543-215">FX_DRIVER_RELEASE_SECTORS</span><span class="sxs-lookup"><span data-stu-id="84543-215">FX_DRIVER_RELEASE_SECTORS</span></span>|
|<span data-ttu-id="84543-216">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="84543-216">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="84543-217">Början av den kostnads fria sektorn</span><span class="sxs-lookup"><span data-stu-id="84543-217">Start of free sector</span></span>|
|<span data-ttu-id="84543-218">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="84543-218">fx_media_driver_sectors</span></span>|<span data-ttu-id="84543-219">Antal kostnads fria sektorer</span><span class="sxs-lookup"><span data-stu-id="84543-219">Number of free sectors</span></span>|

### <a name="driver-suspension"></a><span data-ttu-id="84543-220">Driv rutins SUS Pension</span><span class="sxs-lookup"><span data-stu-id="84543-220">Driver Suspension</span></span>

<span data-ttu-id="84543-221">Eftersom I/O med fysiska media kan ta en stund, är det ofta önskvärt att pausa anrops tråden.</span><span class="sxs-lookup"><span data-stu-id="84543-221">Because I/O with physical media may take some time, suspending the calling thread is often desirable.</span></span> <span data-ttu-id="84543-222">Detta förutsätter att slut för ande av den underliggande i/O-åtgärden avbryts.</span><span class="sxs-lookup"><span data-stu-id="84543-222">Of course, this assumes completion of the underlying I/O operation is interrupt driven.</span></span> <span data-ttu-id="84543-223">I så fall, är det enkelt att göra en tråd upphängning med en ThreadX-semafor.</span><span class="sxs-lookup"><span data-stu-id="84543-223">If so, thread suspension is easily implemented with a ThreadX semaphore.</span></span> <span data-ttu-id="84543-224">När du har startat indata-eller utdata-åtgärden inaktive ras i/O-drivrutinen på den egna interna I/O-semaforen (skapas med det inledande antalet noll under driv rutins initieringen).</span><span class="sxs-lookup"><span data-stu-id="84543-224">After starting the input or output operation, the I/O driver suspends on its own internal I/O semaphore (created with an initial count of zero during driver initialization).</span></span> <span data-ttu-id="84543-225">Som en del av avbrotts processen i/O-slut för ande av driv rutinen anges samma I/O-semafor, vilket i sin tur aktiverar den pausade tråden.</span><span class="sxs-lookup"><span data-stu-id="84543-225">As part of the driver I/O completion interrupt processing, the same I/O semaphore is set, which in turn wakes up the suspended thread.</span></span>

### <a name="sector-translation"></a><span data-ttu-id="84543-226">Sektor Översättning</span><span class="sxs-lookup"><span data-stu-id="84543-226">Sector Translation</span></span>

<span data-ttu-id="84543-227">Eftersom FileX visar mediet som linjära logiska sektorer görs I/O-begäranden som görs till i/O-drivrutinen med logiska sektorer.</span><span class="sxs-lookup"><span data-stu-id="84543-227">Because FileX views the media as linear logical sectors, I/O requests made to the I/O driver are made with logical sectors.</span></span> <span data-ttu-id="84543-228">Det är driv Rutinens ansvar att översätta mellan logiska sektorer och mediets fysiska geometri, som kan innehålla huvuden, spår och fysiska sektorer.</span><span class="sxs-lookup"><span data-stu-id="84543-228">It is the driver's responsibility to translate between logical sectors and the physical geometry of the media, which may include heads, tracks, and physical sectors.</span></span> <span data-ttu-id="84543-229">För FLASH-och RAM-skivor mappar de logiska sektorerna vanligt vis katalog till fysiska sektorer.</span><span class="sxs-lookup"><span data-stu-id="84543-229">For FLASH and RAM disk media, the logical sectors typically map directory to physical sectors.</span></span> <span data-ttu-id="84543-230">I så fall är det typiska formler för att utföra mappning av logiska till fysiska sektorer i i/O-drivrutinen:</span><span class="sxs-lookup"><span data-stu-id="84543-230">In any case, here are the typical formulas to perform the logical to physical sector mapping in the I/O driver:</span></span>

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

<span data-ttu-id="84543-231">Observera att fysiska sektorer börjar med en, medan logiska sektorer börjar på noll.</span><span class="sxs-lookup"><span data-stu-id="84543-231">Note that physical sectors start at one, while logical sectors start at zero.</span></span>

### <a name="hidden-sectors"></a><span data-ttu-id="84543-232">Dolda sektorer</span><span class="sxs-lookup"><span data-stu-id="84543-232">Hidden Sectors</span></span>

<span data-ttu-id="84543-233">Dolda sektorer fanns före start posten på mediet.</span><span class="sxs-lookup"><span data-stu-id="84543-233">Hidden sectors resided prior to the boot record on the media.</span></span> <span data-ttu-id="84543-234">Eftersom de verkligen ligger utanför omfånget för FAT-filsystemet måste de redovisas i varje logisk sektor åtgärd som driv rutinen gör.</span><span class="sxs-lookup"><span data-stu-id="84543-234">Because they are really outside the scope of the FAT file system layout, they must be accounted for in each logical sector operation the driver does.</span></span>

### <a name="media-write-protect"></a><span data-ttu-id="84543-235">Skriv skydd för media</span><span class="sxs-lookup"><span data-stu-id="84543-235">Media Write Protect</span></span>

<span data-ttu-id="84543-236">FileX-drivrutinen kan aktivera skriv skydd genom att ange fältet fx_media_driver_write_protect i medie kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="84543-236">The FileX driver can turn on write protect by setting the fx_media_driver_write_protect field in the media control block.</span></span> <span data-ttu-id="84543-237">Detta leder till att ett fel returneras om eventuella FileX-anrop görs i ett försök att skriva till mediet.</span><span class="sxs-lookup"><span data-stu-id="84543-237">This will cause an error to be returned if any FileX calls are made in an attempt to write to the media.</span></span>

## <a name="sample-ram-driver"></a><span data-ttu-id="84543-238">Exempel på RAM-drivrutin</span><span class="sxs-lookup"><span data-stu-id="84543-238">Sample RAM Driver</span></span>

<span data-ttu-id="84543-239">FileX demonstrations systemet levereras med en liten RAM-drivrutin, som definieras i filen fx_ram_driver. c.</span><span class="sxs-lookup"><span data-stu-id="84543-239">The FileX demonstration system is delivered with a small RAM disk driver, which is defined in the file fx_ram_driver.c.</span></span> <span data-ttu-id="84543-240">Driv rutinen förutsätter ett minnes utrymme på 32K och skapar en start post för 256 128 byte-sektorer.</span><span class="sxs-lookup"><span data-stu-id="84543-240">The driver assumes a 32K memory space and creates a boot record for 256 128-byte sectors.</span></span> <span data-ttu-id="84543-241">Den här filen ger ett användbart exempel på hur du implementerar programspecifika FileX I/O-drivrutiner.</span><span class="sxs-lookup"><span data-stu-id="84543-241">This file provides a good example of how to implement application specific FileX I/O drivers.</span></span>

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
